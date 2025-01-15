import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;

public class GerarArquivoARFF {

    public static void main(String[] args) {
        String arquivoARFF = "educacao_brasileira.arff";
        StringBuilder conteudoARFF = new StringBuilder();

        // Cabeçalho do arquivo ARFF
        conteudoARFF.append("@relation educacao_brasileira\n\n")
                    .append("@attribute estado {AC, AL, AM, AP, BA, CE, DF, ES, GO, MA, MG, MS, MT, PA, PB, PE, PI, PR, RJ, RN, RO, RR, RS, SC, SE, SP, TO}\n")
                    .append("@attribute taxa_alfabetizacao numeric\n")
                    .append("@attribute anos_escolaridade_media numeric\n")
                    .append("@attribute taxa_evasao numeric\n")
                    .append("@attribute investimento_educacao numeric\n")
                    .append("@attribute regiao {Norte, Nordeste, Centro-Oeste, Sudeste, Sul}\n\n")
                    .append("@data\n");

        // Dados do conjunto
        conteudoARFF.append("BA,85.3,6.5,10.2,5400,Nordeste\n")
                    .append("SP,95.6,10.8,5.3,12000,Sudeste\n")
                    .append("AM,88.0,7.2,12.5,4600,Norte\n")
                    .append("RS,96.2,9.7,3.1,8600,Sul\n")
                    .append("GO,92.3,8.5,7.8,6200,Centro-Oeste\n");

        // Escrevendo o conteúdo no arquivo
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(arquivoARFF))) {
            writer.write(conteudoARFF.toString());
            System.out.println("Arquivo ARFF criado com sucesso: " + arquivoARFF);
        } catch (IOException e) {
            System.err.println("Erro ao criar o arquivo ARFF: " + e.getMessage());
        }
    }
}

