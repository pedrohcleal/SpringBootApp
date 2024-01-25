# Projeto Spring Boot CRUD Example
[![Build Status](https://travis-ci.org/pedrohcleal/SpringBootApp.svg?branch=main)](https://travis-ci.org/pedrohcleal/SpringBootApp)
[![Java Version](https://img.shields.io/badge/Java-11-blue.svg)](https://openjdk.java.net/projects/jdk/11/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

Este é um exemplo de aplicação Spring Boot que demonstra operações CRUD (Create, Read, Update, Delete) em uma entidade de produtos. O objetivo deste projeto é acadêmico, servindo como um exemplo simples de uma aplicação Spring Boot com funcionalidades CRUD.

## Estrutura do Projeto

- **ProductController:** Controlador responsável por manipular as requisições HTTP relacionadas aos produtos.

- **ProductRecordDto:** DTO (Data Transfer Object) que representa os dados de entrada/saída para a entidade de produto.

- **ProductModel:** Entidade que representa um produto e é mapeada para a tabela `TB_PRODUCTS` no banco de dados.

- **ProductRepository:** Interface que estende JpaRepository para realizar operações de persistência na entidade ProductModel.

- **SpringbootApplication:** Classe principal que inicia a aplicação Spring Boot.

- **application.properties:** Arquivo de configuração do Spring Boot, que define as configurações do banco de dados PostgreSQL.

## Endpoints

- **POST /products:** Cria um novo produto com base nos dados fornecidos no corpo da requisição.

- **GET /products:** Retorna todos os produtos cadastrados.

- **GET /products/{id}:** Retorna os detalhes de um produto específico com base no ID fornecido.

- **PUT /products/{id}:** Atualiza os dados de um produto específico com base no ID fornecido.

- **DELETE /products/{id}:** Exclui um produto específico com base no ID fornecido.

## Configuração do Banco de Dados

O projeto está configurado para usar um banco de dados PostgreSQL. Certifique-se de ter um banco de dados chamado `products-api` configurado localmente, com o usuário `postgres` e senha `root`. O Hibernate está configurado para atualizar automaticamente o esquema do banco de dados.

```properties
spring.datasource.url = jdbc:postgresql://localhost:5432/products-api
spring.datasource.username= postgres
spring.datasource.password= root
spring.jpa.hibernate.ddl-auto= update

# Configuração adicional para evitar problemas de criação de tabela no contexto não contextual do Hibernate
spring.jpa.properties.hibernate.jdbc.lab.non_contextual_creation = true
```

## Executando o Projeto

Certifique-se de ter o JDK 21 e o Maven instalados em sua máquina. Abra o projeto no IntelliJ IDEA usando o arquivo pom.xml para baixar todas as dependências.
Para iniciar a aplicação, execute o seguinte comando na raiz do projeto:
```bash
mvn spring-boot:run
```

A aplicação estará disponível em [http://localhost:8080](http://localhost:8080).

## Testando com Postman

Abaixo estão exemplos de como testar os endpoints usando o Postman.

### 1. Cadastrar um Novo Produto

- **Endpoint:** POST /products
- **Corpo da Requisição (JSON):**
```json
{
  "name": "Produto Teste",
  "value": 19.99
}
```
- **Resultado Esperado:** Retorno do produto recém-criado.

### 2. Obter Todos os Produtos

- **Endpoint:** GET /products
- **Resultado Esperado:** Lista de todos os produtos cadastrados.

### 3. Obter Detalhes de um Produto Específico

- **Endpoint:** GET /products/{id}
- **Resultado Esperado:** Detalhes do produto com o ID específico.

### 4. Atualizar um Produto Existente

- **Endpoint:** PUT /products/{id}
- **Corpo da Requisição (JSON):**
```json
{
  "name": "Produto Atualizado",
  "value": 29.99
}
```
- **Resultado Esperado:** Retorno do produto atualizado.

### 5. Excluir um Produto

- **Endpoint:** DELETE /products/{id}
- **Resultado Esperado:** Confirmação de exclusão bem-sucedida.

## Observações
Este projeto utiliza o Hibernate e o Spring Data JPA para facilitar a interação com o banco de dados. Certifique-se de ajustar as configurações do banco de dados conforme necessário para o seu ambiente.

Este é um exemplo básico e pode ser expandido para incluir autenticação, autorização, validações mais avançadas, etc., dependendo dos requisitos do projeto.
