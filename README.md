# API BLOG PESSOAL

🔗 **Link de Teste da API:** [Link do Deploy no Render - *Substituir pelo link real*]

🔐 **Acesso Padrão:**

*   **Usuário:** `root@root.com`
*   **Senha:** `rootroot`

* * *

Este projeto é uma API RESTful para um **Blog Pessoal**, desenvolvida como parte de um estudo prático com **Spring Boot**. A aplicação permite o gerenciamento de usuários, temas e postagens, implementando autenticação e autorização com **JWT (JSON Web Token)** via **Spring Security**.

## 📚 Endpoints da API

### 👤 Usuários

*   `GET /usuarios` - Lista todos os usuários (Pode requerer permissão de ADMIN)
*   `GET /usuarios/{id}` - Busca um usuário por ID
*   `POST /usuarios/cadastrar` - Cadastra um novo usuário
*   `POST /usuarios/logar` - Autentica um usuário e retorna um token JWT
*   `PUT /usuarios/atualizar` - Atualiza os dados de um usuário existente (requer autenticação)

### 🏷️ Temas

*   `GET /temas` - Lista todos os temas
*   `GET /temas/{id}` - Busca um tema por ID
*   `GET /temas/descricao/{descricao}` - Busca temas pela descrição (contendo a string)
*   `POST /temas` - Cria um novo tema (requer autenticação)
*   `PUT /temas` - Atualiza um tema existente (requer autenticação)
*   `DELETE /temas/{id}` - Deleta um tema por ID (requer autenticação)

### 📝 Postagens

*   `GET /postagens` - Lista todas as postagens
*   `GET /postagens/{id}` - Busca uma postagem por ID
*   `GET /postagens/titulo/{titulo}` - Busca postagens pelo título (contendo a string)
*   `POST /postagens` - Cria uma nova postagem (associada a um tema e usuário - requer autenticação)
*   `PUT /postagens` - Atualiza uma postagem existente (requer autenticação)
*   `DELETE /postagens/{id}` - Deleta uma postagem por ID (requer autenticação)

### 🔐 Autenticação (Spring Security + JWT)

*   As rotas de criação, atualização e exclusão de Temas e Postagens, além da atualização de Usuário, são protegidas e exigem um token JWT válido no cabeçalho `Authorization`.

* * *

## 🛠 Tecnologias Utilizadas

*   **Java 17**
*   **Spring Boot 3**
*   **Spring Web**
*   **Spring Data JPA**
*   **Spring Security**
*   **JWT (Json Web Token)**
*   **MySQL** (Desenvolvimento Local)
*   **PostgreSQL** (Produção - Render)
*   **Docker** (Para deploy no Render)
*   **Insomnia/Postman** (Testes de API)
*   **SpringDoc (Swagger)** (Documentação automática da API - se implementado)

* * *

## 🔗 Relacionamento entre Entidades

O projeto possui os seguintes relacionamentos principais:

*   Um **Tema** pode conter **muitas Postagens** (OneToMany)
*   Cada **Postagem** pertence a um único **Tema** (ManyToOne)
*   Um **Usuário** pode criar **muitas Postagens** (OneToMany)
*   Cada **Postagem** pertence a um único **Usuário** (ManyToOne)

* * *

## 🚀 Como usar a API (Rotas Protegidas)

Para acessar as rotas protegidas:

1.  Cadastre um usuário com `POST /usuarios/cadastrar`.
    *   Exemplo de Body:
        ```json
        {
          "nome": "Seu Nome Completo",
          "usuario": "seu_email@exemplo.com",
          "senha": "sua_senha_min_8_chars",
          "foto": "link_da_sua_foto.jpg"
        }
        ```
2.  Faça login com `POST /usuarios/logar` usando o email e senha cadastrados.
    *   Exemplo de Body:
        ```json
        {
          "usuario": "seu_email@exemplo.com",
          "senha": "sua_senha_min_8_chars"
        }
        ```
3.  Copie o `token` JWT retornado na resposta do login.
4.  Nas requisições para rotas protegidas (POST/PUT/DELETE de Temas/Postagens, PUT de Usuário), adicione o token no cabeçalho (Header) `Authorization`:
    ```
    Authorization: Bearer <seu_token_jwt_aqui>
    ```

* * *

Desenvolvido por [**Thiago Tasseli**](https://www.linkedin.com/in/thiagotasseli-tech/)

Fique à vontade para tirar dúvidas, dar sugestões ou contribuir! 😄

