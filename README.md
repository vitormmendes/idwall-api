# Introdução

*Esta documentação reúne informações da API oficial da IDwall.* 

Navegue pela documentação completa aqui: https://idwall.readme.io/

### O que a IDwall faz?

A IDwall existe para agilizar e automatizar seu processo de *onboarding* de novos usuários, clientes ou parceiros, de maneira segura através de *Background Check*.

Nosso sistema faz consultas em diversas fontes públicas e privadas, trazendo informações em forma de relatórios personalizados que podem te ajudar a aprovar e cadastrar mais pessoas na sua plataforma. Todo este processo é automático, e pode ser feito através do nosso [Dashboard](https://dashboard.idwall.co) ou da nossa API.

### Como utilizar esta documentação
<!--Para implementação da API em seu sitema, selecione na coluna ao lado a linguagem de programação que gostaria de usar para fazer requisições aos endpoints. Códigos de exemplo serão gerados ao lado de cada endpoint para auxiliá-lo na implementação.-->

Enquanto estiver seguindo esta documentação, recomendamos que utilize o [Postman](https://www.getpostman.com/). Nele você irá importar a *Collection* da IDwall usando o menu *Import > Import from Link >* https://api-v2.idwall.co/postman.
O artigo [Importar a documentação da API v2 através do Postman](https://intercom.help/idwall/api/testes-da-api/importar-a-documentacao-da-api-v2-atraves-do-postman) explica o processo de importação passo a passo.

### Uso da API

Utilizamos uma [API REST](https://pt.wikipedia.org/wiki/REST). Seguimos um padrão comum entre todos os *endpoints* para maior previsibilidade: 
- Todos as requisições executadas com sucesso retornam o ```HTTP Status 200```.
- Requisões com falha retornarão o número de status pertinente ao erro, além de chaves com informações extras sobre este erro.
- Utilizamos [parâmetros de query](https://en.wikipedia.org/wiki/Query_string) como auxílio para paginação, filtros e informações adicionais que podem ser solicitadas na consulta.
- Todas as requisições retornam conteúdos JSON (application/json) e possuem corpos padrões:

### Requisições de sucesso

```json
{
    "status_code": 200,
    "result": { }
}
```

### Requisições falhas

```json
{
    "status_code": 404,
    "error": "Not Found",
    "message": "O protocolo requisitado não foi encontrado."
}
```

Cada endpoint possui um *schema* diferente para o campo `result`, que poderá ser consultado
conforme necessidade no decorrer desta documentação.

Nosso *endpoint* base para a implementação é:

```
https://api-v2.idwall.co
```

Os *endpoints* mostrados ao longo da documentação devem ser utilizados ao final do *endpoint* base. Por exemplo, o *endpoint* ```/validacoes``` é acessado através da URL ```https://api-v2.idwall.co/validacoes```

O ```header``` de todas as requisições deve conter a chave:

```json
{
  "Authorization": "{token}",
}
```

onde ```{token}``` é a chave de acesso do seu usuário. Sua chave de acesso pode ser encontrada acessando nosso Dashboard, em [https://dashboard.idwall.co/api](https://dashboard.idwall.co/api).
