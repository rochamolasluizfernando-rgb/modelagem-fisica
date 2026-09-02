## Criação do banco de dados 

```sql
CREATE DATABASE microblog CHARACTER SET utf8mb4;
```

## Criação da tabela usuarios 
```sql
CREATE TABLE usuarios(
    id INT NOT NULL AUTO_INCREMENT PRIMARY KEY, 
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    senha VARCHAR(255) NOT NULL,
    tipo ENUM('admin','editor') NOT NULL
);
```

## Criação da tabela noticias
```sql
CREATE TABLE noticias(
    id INT NOT NULL AUTO_INCREMENT,
    titulo VARCHAR(100) NOT NULL,
    resumo TEXT NOT NULL,
    texto TEXT NOT NULL,
    imagem VARCHAR(100) NULL,
    destaque ENUM('sim','nao') NOT NULL,
    data DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
    usuario_id INT NOT NULL,
    categoria_id INT NOT NULL,
    PRIMARY KEY (id),
    FOREIGN KEY (usuario_id) REFERENCES usuarios(id) ON DELETE CASCADE,
    FOREIGN KEY (categoria_id) REFERENCES categorias(id) ON DELETE CASCADE
);
```

## Criação da tabela categorias
```sql 
CREATE TABLE categorias(
    id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL
);
```