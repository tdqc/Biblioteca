# Biblioteca
Script banco

CREATE DATABASE BIBLIOTECA
GO
USE BIBLIOTECA

CREATE TABLE ALUNO (
	IDALUNO INT PRIMARY KEY IDENTITY,
	NOME VARCHAR(100) NOT NULL,
	MATRICULA VARCHAR(20) UNIQUE NOT NULL,
	CPF VARCHAR(11) UNIQUE NOT NULL,
	TELEFONE VARCHAR(10),
	EMAIL VARCHAR(50) UNIQUE NOT NULL,
	CODCARTAO VARCHAR(10)
);
										
CREATE TABLE LIVRO (
	IDLIVRO INT PRIMARY KEY IDENTITY,
	NOME VARCHAR(50) NOT NULL,
	EDITORA VARCHAR(30),
	VERSAO VARCHAR(10),
	AUTOR VARCHAR(100),
);

CREATE TABLE RESERVA (
	IDRESERVA INT PRIMARY KEY IDENTITY,
	DATAINICIO VARCHAR(10),
	DATAFIM VARCHAR(10),
	IDALUNO INT FOREIGN KEY (IDALUNO) REFERENCES ALUNO,
);

CREATE TABLE EMPRESTIMO (
	IDEMPRESTIMO INT PRIMARY KEY IDENTITY,
	DATA_INICIO VARCHAR(10),
	DATA_FIM VARCHAR(10),
	DATA_DEVOLUCAO VARCHAR(10),
	IDALUNO INT FOREIGN KEY (IDALUNO) REFERENCES ALUNO,
);

CREATE TABLE RESERVA_EMPRESTIMO (
	IDRESERVA INT FOREIGN KEY (IDRESERVA) REFERENCES RESERVA,
	IDEMPRESTIMO INT FOREIGN KEY (IDEMPRESTIMO) REFERENCES EMPRESTIMO,
);
