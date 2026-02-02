HTTP, ou Hypertext Transfer Protocol, é um protocolo para transmissão de documentos hipermídia, como HTML. Serve principalmente para a comunicação entre navegadores web e servidores web, mas também tem outros propósitos.

As mensagens enviadas pelo cliente, geralmente o navegador Web, recebem o nome solicitações (requests) ou requisições. As mensagens enviadas pelo servidor como réplica, por sua vez, recebem o nome de respostas (responses).

Obs: não necessariamente o cliente é o navegador. Às vezes, pode ser um bot que varre a Web. Em geral, pode ser qualquer coisa.

Entre as solicitações e a resposta, há várias entidades, designadas coletivamente como proxies, que executam operações diferentes. Um servidor proxy é um computador ou programa intermediário para navegar em conexões de internet diferentes.

![A HTTP request from a client forwarded by several proxies to a server and a response taking the same route back to the client.](https://mdn.github.io/shared-assets/images/diagrams/http/overview/client-server-chain.svg)

Esses proxies podem ser roteadores, modems, etc. Normalmente, essas camadas são abstraídas, enquanto o HTTP age na camada de aplicação.  Por isso, essas outras camadas são irrelevantes para o HTTP.

### Cliente: o agente-usuário

O agente-usuário é qualquer ferramente que age em nome do usuário, predominantemente o navegador Web. Ele sempre inicia as requisições, salvo algumas exceções muito específicas.

Para mostrar uma página Web, por exemplo, o navegador envia uma requisição para buscar o documento HTML. Assim, ele analisa o arquivo, buscando também scripts de execução, informações de layout e subrecursos.

### Servidor

Do outro lado, o servidor serve o documento requisitado pelo usuário. Virtualmente, ele é apenas uma máquina, mas pode ser inúmeros servidores ou programas complexos que acessam outros servidores, gerando toda ou parte do documento.

# O que o HTTP controla?

O HTTP, por ser naturalmente extensivo, tem permitido mais controle e funcionalidade para a internet. Alguns exemplos são:

* Cache: a forma como documentos são cacheados pode ser controlada pelo HTTP, tanto no lado do servidor quanto no do cliente;

* Segurança: para prevenir invasores, os navegadores reforçam a separação dos sites Web. No entanto, os cabeçalhos HTTP conseguem relaxar essa separação no lado dos servidores, permitindo que o documento seja composto por várias fontes de informação;

* Autenticação: o HTTP pode fornecer autenticação básica por meio de simples comandos no cabeçalho, facilitando o acesso apenas a usuários específicos;

# Fluxo HTTP

Quando o cliente quer se comunicar com um servidor, realizam-se os seguintes passos:

1.  Abre-se uma conexão TCP, usada para enviar a requisição e receber a resposta. Várias conexões podem ser abertas. O protocolo TCP é escolhido por ter maior segurança.

2.  Envia-se uma mensagem HTTP, que era legível anteriormente.

![[Pasted image 20260202134253.png]]

3.  Lê-se a resposta do servidor:

![[Pasted image 20260202134422.png]]

4. Fecha-se ou reutiliza-se a conexão para requisições futuras.

Normalmente, uma requisição deve ser concluída para outra ser requisitada. No entanto, e a linha de montagem (pipelining) estiver ativada, isso não é necessário. Hoje em dia, essa linha vem sido substituída por multiplexações mais robustas.

# Mensagens HTTP

Antigamente, mensagens HTTP eram legíveis a pessoas comuns. No entanto, por fins de otimizações e compressão, hoje elas são embutidas em estruturas binárias chamadas quadros (frames). Mesmo assim, essa semântica permanece inalterada a nível de máquina, sendo ainda importante entendê-las como eram anteriormente.

### Requisições

![Overview of a HTTP GET request with headers](https://mdn.github.io/shared-assets/images/diagrams/http/overview/http-request.svg)


Acima, temos um exemplo de uma requisição. Ela é composta pelos seguintes elementos:

* Método HTTP, que define qual operação o cliente quer fazer. Alguns métodos são GET, POST, DELETE, PUT, OPTIONS, HEAD, etc. Os mais usados são GET, para obter recursos, e POST, para publicar dados;

* O caminho do recurso a ser buscado;

*  A versão do protocolo HTTP;

*  Cabeçalhos (headers), informações opcionais para os servidores;

*  Corpo de dados, para alguns métodos, que contém o recurso requisitado. Por exemplo, ao utilizar o POST, temos a informações que queremos levar ao servidor.

### Respostas

![Overview of a '200 OK' HTTP response to a GET request including response headers.](https://mdn.github.io/shared-assets/images/diagrams/http/overview/http-response.svg)


Agora, temos um exemplo de resposta, que consistem dos seguintes elementos:

*  A versão do protocolo HTTP;

*  Um código de status, indicando se a requisição foi bem sucedida, ou não, e por quê. Há inúmeros códigos, mas os mais comuns são de sucesso (200 - 299), de erro do cliente (400 - 499) e de erro do servidor (500 - 599);

*  Uma mensagem de status, que descreve informalmente o código de status;

*  Cabeçalhos HTTP, semelhantes aos das requisições;

*  Opcionalmente, um corpo com dados do recurso requisitado. Acima, pode-se ver uma resposta que retornou uma página HTML. Portanto, o corpo terá o código dessa página.

