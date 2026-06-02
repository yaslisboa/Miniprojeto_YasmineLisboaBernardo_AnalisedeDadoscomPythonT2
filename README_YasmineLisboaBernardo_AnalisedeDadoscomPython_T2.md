# Mini-Projeto Avaliativo - Módulo 1 - Semana 07
Autora: Yasmine Lisboa Bernardo

Turma: Análise de Dados com Python T2


Este projeto apresenta uma análise exploratória da base de dados de um varejo, desenvolvida como parte da **Mini-Projeto Avaliativo do Curso de Análise de Dados com Python**. O objetivo desse projeto foi realizar uma **Análise Exploratória de Dados (AED)** em uma base de varejo utilizando Python e Pandas para compreender, limpar e analisar os dados, além de preparar uma base para que sejam feitas análises mais avançadas ou para construção de um dashboard.


## Objetivos:

- Carregar e explorar a base de dados utilizando Pandas.
- Identificar problemas de qualidade dos dados, como valores nulos, inconsistências e possíveis duplicidades.
- Realizar a limpeza mínima necessária e preparação dos dados para análise.
- Converter e ajustar tipos de dados quando necessário.
- Gerar estatísticas descritivas para compreender o perfil dos clientes.
- Aplicar técnicas de agrupamento para responder perguntas operacionais do varejo.
- Extrair insights relevantes sobre clientes, produtos e vendas.


### Como executar o projeto:

**Pré-requisitos:**

Visual Studio Code

Extensão Jupyter para VS Code

Python 3 instalado

**Bibliotecas utilizadas:**

pandas
numpy

Caso as bibliotecas não estejam instaladas, utilize:

pip install pandas numpy

**Organização dos arquivos:**

O arquivo Varejo.csv deve estar na mesma pasta do notebook, pois a leitura dos dados foi realizada utilizando:

varejo = pd.read_csv("Varejo.csv")

**Execução:**

Abra a pasta do projeto no Visual Studio Code.

Abra o arquivo .ipynb.

Selecione um ambiente Python com as bibliotecas instaladas.

Execute as células na ordem em que aparecem no notebook.

### Base Varejo

A base de dados Varejo reúne registros de compras contendo informações sobre clientes, produtos e transações realizadas entre os anos de 2019 e 2022.

- **DATA**: Data da compra;
- **CO_ID**: Identificação do número de compra (número da nota fiscal);
- **CL_ID**: Identificação do cliente (número do cliente);
- **CL_GENERO**: Sexo biológico informado pelo cliente;
- **CL_EC**: Estado civil do cliente, sendo:
1. Casado ou união estável;
2. Divorciado;
3. Separado;
4. Solteiro;
5. Viúvo.
- **CL_FHL**: Número de filhos do cliente;
- **CL_SEG**: Segmentação econômica do cliente (classe A, B ou C);
- **PR_ID**: Código do produto (SKU) adquirido;
- **PR_CAT**: Categoria do produto adquirido;
- **PR_NOME**: Nome do produto adquirido.

## Limpeza e Tratamento dos Dados

Antes da análise exploratória, foi realizada uma etapa de inspeção da base para identificar possíveis problemas de qualidade dos dados, incluindo valores nulos, registros duplicados, inconsistências nas informações e tipos de dados inadequados.

### Colunas vazias

Foram identificadas colunas contendo apenas valores nulos. Como essas colunas não possuíam informações relevantes para a análise e não contribuíam para os objetivos do projeto, optou-se pela sua remoção.

### Valor #N/D

Também foram encontrados registros contendo o valor #N/D nas colunas PR_CAT (categoria do produto) e PR_NOME (nome do produto). Como a ausência da informação estava restrita a esses campos e os demais dados da compra permaneciam válidos, optou-se por manter os registros na base e substituir os valores por descrições mais adequadas:

**Coluna PR_CAT**

#N/D foi transformado em Sem Categoria

**Coluna PR_NOME**

#N/D foi transformado em Produto Desconhecido

### Valores Duplicados

Foram identificadas ocorrências consideradas duplicadas pelo Pandas, mas a análise mostrou que a base varejo registra produtos individualmente dentro de cada compra, permitindo que um mesmo produto apareça mais de uma vez na mesma nota fiscal. Não é possível confirmar que representa erro no cadastro ou que o cliente decidiu adquirir mais de um mesmo produto na mesma compra, então, os registros foram mantidos na base para evitar a perda de informações úteis para futuras análises.


### Conversão da coluna DATA

A coluna DATA foi convertida para o tipo datetime, permitindo a realização de análises por mês e ano. 

Após essas etapas, a base ficou padronizada e adequada para a geração das estatísticas descritivas e análises exploratórias propostas no projeto.

## Estatísticas Descritivas - Número de Filhos (CL_FHL)

Contagem          -   830.000

Média             -   1,15 

Mediana           -   0 

Moda              -   0 

Desvio Padrão     -   1,42

Mínimo            -   0 

1º Quartil (25%)  -   0 

2º Quartil (50%)  -   0

3º Quartil (75%)  -   2 

Máximo            -   4

A maioria dos clientes possui poucos ou nenhum filho. A média foi de aproximadamente 1,15 filho por cliente, enquanto a mediana e moda foram iguais a 0, indicando que mais da metade dos clientes não possui filhos na base de dados varejo.

## Análises Realizadas

- Gênero que comprou mais produtos
- Categoria de produtos mais vendida
- Variação de vendas de produtos ao longo do tempo

## Insights


### 1. Gênero teve pouca relevância

**Sexo Feminino** = 432.576 registros (52,1%)

**Sexo Masculino** = 397.424 registros (47,9%)

**Insight**: Clientes do gênero biológico feminino representaram uma parcela pouco maior dos registros de compra da base analisada. Ambos os gêneros têm participação relevante no volume de transações da base.


### 2. Segmento econômico B concentra a maior parte das vendas

Segmento B = 530.163 registros (63,9%)

Segmento C = 232.101 registros (28,0%)

Segmento A = 67.736 registros (8,2%)

**Insight**: Mais da metade das compras registradas na base foram realizadas por clientes do segmento econômico B (classe média). O segmento A (alta renda) representa apenas 8,2% das transações, sugerindo que o perfil predominante do varejo é de consumidores de renda média a média-baixa.

### 3. Mais da metade dos produtos vendidos é da categoria Alimentos

Alimentos = 434767 registros (52,38%)

Higiene = 155574 registros (18,74%)

Limpeza = 145754 registros (17,56%)

Bebidas = 43299 registros (5,22%)

Pet = 32399 registros (3,90%)

Acessórios = 14557 registros (1,75%)

Sem Categoria = 3650 registros (0,44%)

**Insight**: A categoria Alimentos concentra mais da metade das vendas da base, seguida por Higiene e Limpeza, reforçando a predominância de produtos essenciais no consumo dos clientes.

### 4. Variação considerável na quantidade de produtos vendidos entre os meses
Do mês com mais produtos vendidos para o mês com menos

Janeiro = 83963 registros (10.12%)

Maio = 82275 registros (9.91%)

Fevereiro = 76201 registros (9.18%)

Outubro = 73900 registros (8.90%)

Dezembro = 70449 registros (8.49%)

Julho = 68983 registros (8.31%)

Setembro = 68594 registros (8.26%)

Junho = 67808 registros (8.17%)

Abril = 66935 registros (8.06%)

Agosto = 65609 registros (7.90%)

Março = 64371 registros (7.76%)

Novembro = 40912 registros (4.93%)

**Insight**: Foi observada variação no volume de vendas entre os meses analisados, com a maior concentração de produtos vendidos em Janeiro e menor volume de produtos vendidos em Novembro.


## Conclusão

Ao longo deste mini projeto foi possível aplicar as técnicas de Análise Exploratória de Dados (AED) aprendidas durante as aulas do curso para compreender melhor a base de dados Varejo transformando os dados brutos em informações úteis. 

Depois de carregar o arquivo foi iniciada a etapa de inspeção dos dados, identificação de inconsistências e em seguida a etapa de limpeza e padronização. Durante a etapa de limpeza foram encontrados valores inconsistentes e registros que exigiram padronização, além da conversão de tipos de dados para formatos mais adequados.

Após todo o tratamento da base foi possível gerar as estatísticas descritivas solicitadas e identificar padrões de consumo utilizando agrupamentos. Os resultados mostraram diferenças no volume de vendas entre os meses analisados, uma predominância de produtos da categoria Alimentos, uma distribuição relativamente equilibrada entre os gêneros dos clientes e o perfil predominante do varejo sendo de consumidores de renda média a média-baixa.

A utilização da AED demonstrou a importância de tratar os dados antes da extração de informações, garantindo análises mais confiáveis e fornecendo uma base organizada para estudos futuros, relatórios e dashboards.

#### Possíveis limitações da base ####

A variável de estado civil (CL_EC) diferencia clientes "separados" e "divorciados". Dependendo do objetivo da análise, essas categorias podem representar situações semelhantes e gerar interpretações diferentes dos resultados. 

Não há informações adicionais que permitam entender o critério utilizado para essa classificação, o que pode dificultar comparações ou agrupamentos futuros. Em análises mais avançadas, pode ser necessário avaliar se essas categorias devem permanecer separadas ou ser agrupadas em uma única classificação.




