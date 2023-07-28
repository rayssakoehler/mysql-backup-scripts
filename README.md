# mysql-backup-scripts
dados_bancarios_java
│   README.md
│
└───src
    └───main
        └───java
            │   CriarTabelaDadosBancarios.java
            │
            └───model
                    DadoBancario.java
# Dados Bancários Java

Este é um projeto Java simples que cria uma tabela no MySQL para armazenar dados bancários.
.

## Estrutura do Projeto

O projeto não utiliza ferramentas de gerenciamento de pacotes, como o Maven. A estrutura do projeto é simples:

- `src/main/java`: Contém o código-fonte Java.

## Criar a Tabela de Dados Bancários

Para criar a tabela de dados bancários, execute o programa Java `CriarTabelaDadosBancarios.java`.

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;

public class CriarTabelaDadosBancarios {

    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:3306/dados_bancarios";
        String user = "seu_usuario";
        String password = "sua_senha";

        try (Connection connection = DriverManager.getConnection(url, user, password)) {
            String sql = "CREATE TABLE dados_bancarios ("
                    + "id INT AUTO_INCREMENT PRIMARY KEY,"
                    + "nome_titular VARCHAR(100) NOT NULL,"
                    + "numero_conta VARCHAR(20) NOT NULL,"
                    + "agencia VARCHAR(20) NOT NULL,"
                    + "saldo DOUBLE NOT NULL"
                    + ")";

            try (Statement statement = connection.createStatement()) {
                statement.execute(sql);
            }

            System.out.println("Tabela dados_bancarios criada com sucesso.");
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
