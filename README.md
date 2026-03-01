📅 Sistema de Agendamento de Horários
📖 Descrição

API REST desenvolvida com Spring Boot para gerenciamento de agendamentos de serviços.

O sistema permite cadastrar, consultar, alterar e excluir agendamentos, aplicando regras de negócio para evitar conflitos de horário no mesmo período.

Este projeto foi desenvolvido com o objetivo de praticar arquitetura em camadas, persistência de dados com JPA e implementação de validações na camada de serviço.

----------------------------------------

🛠 Tecnologias Utilizadas

Java 21

Spring Boot

Spring Data JPA

Hibernate

Maven

Lombok

Banco de Dados: (coloque aqui H2 ou MySQL)


----------------------------------------
🧱 Arquitetura do Projeto

O sistema foi desenvolvido utilizando arquitetura em camadas:

Controller → Responsável pela exposição dos endpoints REST

Service → Responsável pela implementação das regras de negócio

Repository → Responsável pela persistência de dados

Entity → Mapeamento objeto-relacional (ORM)
----------------------------------------



🔄 Fluxo da Aplicação

📌 1. Criação de Agendamento

Cliente envia requisição para POST /agendamentos

Controller recebe os dados

Service verifica se já existe agendamento no mesmo horário

Caso não exista conflito:

O agendamento é salvo no banco

Caso exista conflito:

É lançada uma exceção informando que o horário já está preenchido

----------------------------------------


📌 2. Consulta por Dia

Cliente envia data como parâmetro

Service converte para:

Início do dia (00:00)

Final do dia (23:59:59)

Repository busca agendamentos dentro do intervalo

----------------------------------------


📌 3. Alteração

Busca agendamento existente por cliente e data

Caso exista:

Atualiza os dados mantendo o ID original

Caso não exista:

Lança exceção informando que o horário não está preenchido

----------------------------------------


📌 4. Exclusão

Cliente informa data e nome

Repository executa exclusão baseada nos dois parâmetros

⚙ Funcionalidades

✅ Criar agendamento

✅ Buscar agendamentos por dia

✅ Alterar agendamento

✅ Deletar agendamento

✅ Validação de conflito de horário

----------------------------------------


📌 Regras de Negócio Implementadas

Não permite dois agendamentos do mesmo serviço no mesmo intervalo de horário

Impede atualização de agendamento inexistente

Busca por intervalo de datas utilizando LocalDateTime

Exclusão baseada em múltiplos parâmetros

----------------------------------------


📚 Conceitos Praticados

API REST

Injeção de Dependência

Arquitetura em Camadas

Spring Data JPA

Query Methods

Manipulação de datas com LocalDate e LocalDateTime

Separação de responsabilidades

Implementação de regras de negócio na camada de serviço

----------------------------------------


🧪 Testes da API

A API foi testada utilizando Postman, validando:

Cenário de sucesso na criação

Cenário de conflito de horário

Busca por intervalo de data

Atualização de registro existente

Exclusão de registro

Base URL:

http://localhost:8080/agendamentos

🔗 Endpoints


➜ Criar Agendamento
POST /agendamentos

➜ Alterar Agendamento
PUT /agendamentos?cliente=João Silva&dataHoraAgendamento=2026-02-28T14:00:00


➜ Buscar por Dia
GET /agendamentos?data=2026-02-28


➜ Deletar Agendamento,
DELETE /agendamentos?cliente=João Silva&dataHoraAgendamento=2026-02-28T14:00:00







