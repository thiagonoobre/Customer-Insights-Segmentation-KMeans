# Projeto: INSIGHTS E SEGMENTAÇÃO DE CLIENTES - MODELO KMEANS
## Descrição Geral
Nesse projeto estaremos trabalhando com conjunto de dados da ***Contoso Corporation***, que é uma empresa fictícia da **Microsoft**, no qual eles disponibilizaram um Banco de dados, que simula uma multinacional no setor de varejo ([link](https://www.microsoft.com/en-us/download/details.aspx?id=18279)). Seu banco de dados contém informações relacionadas a vendas, produtos, clientes e transações financeiras, oferecendo um cenário realista para explorar técnicas de análise de dados e gerar insights de negócios.
OEste projeto tem como objetivo realizar uma segmentação de clientes por meio da análise de clusters, utilizando técnicas estatísticas e algoritmos de Machine Learning. A análise foi conduzida com base nos dados relacionados a venda e características demográficas de clientes, buncando gerar insights que possam auxiliar em estratégias de negócios, como ofertas personalizadas e melhoria na experiência do cliente.

## Dados Utilizados
Os dados utilizados para este projeto contêm informações sobre as vendas e o perfis demográficos dos clientes. As tabelas principais incluem:

### 1. **Tabela - FactOnlineSales**:
```sql
SELECT COLUMN_NAME
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME = 'FactOnlineSales'
```
- **OnlineSalesKey**: Id das vendas
- **DateKey**: Data da venda
- **StoreKey**: Id da Loja
- **ProductKey**: Id do Produto
- **PromotionKey**: Id da Promoção
- **CurrencyKey**: Id da Moeda
- **CustomerKey**: Id do Cliente
- **SalesOrderNumber**: Número do pedido de venda
- **SalesOrderLineNumbe**: Número da linha do pedido de vendas
- **SalesQuantity**:Quantidade de vendas
- **SalesAmount**: Valor das vendas
- **ReturnQuantity**: Quantidade de devolução
- **ReturnAmount**: Valor da devolução
- **DiscountQuantity**: Quantidade do desconto
- **DiscountAmount**: Valor do desconto
- **TotalCost**: Custo total
- **UnitCost**: Custo unitário
- **UnitPrice**: Preço unitário

### 2. **Tabela - DimCustomer**:

```sql
SELECT COLUMN_NAME
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME = 'DimCustomer'
```
- **CustomerKey**: Id do Cliente
- **GeographyKey**: Id da Geografia
- **CustomerLabel**: Rótulo do Cliente
- **Title**: Título
- **FirstName**: Primeiro Nome
- **MiddleName**: Nome do Meio
- **LastName**: Sobrenome
- **NameStyle**: Estilo do Nome
- **BirthDate**: Data de Nascimento
- **MaritalStatus**: Estado Civil
- **Suffix**: Sufixo
- **Gender**: Gênero
- **EmailAddress**: Endereço de Email
- **YearlyIncome**: Renda Anual
- **TotalChildren**: Total de Filhos
- **NumberChildrenAtHome**: Número de Filhos em Casa
- **Education**: Educação
- **Occupation**: Ocupação
- **HouseOwnerFlag**: Indicador de Proprietário de Casa
- **NumberCarsOwned**: Número de Carros Possuídos
- **AddressLine1**: Endereço Linha 1
- **AddressLine2**: Endereço Linha 2
- **Phone**: Telefone
- **DateFirstPurchase**: Data da Primeira Compra
- **CustomerType**: Tipo de Cliente
- **CompanyName**: Nome da Empresa

## Etapas do Projeto

### 1. **Exploração de Dados**
- Estatísticas descritivas foram geradas para identificar padrões gerais nos dados.
- Um **boxplot** foi utilizado para identificar outliers em variáveis como `ReceitaTotal` e `FrequenciaCompra`.
![](https://raw.githubusercontent.com/thiagonoobre/Customer-Insights-Segmentation-KMeans/refs/heads/main/Imagens/OutliersReceita.png)
![](https://raw.githubusercontent.com/thiagonoobre/Customer-Insights-Segmentation-KMeans/refs/heads/main/Imagens/OutliersFrequencia.png)

### 2. **Tratamento de Outliers**
- Foram analisados separadamente os outliers superiores em receita total e frequência de compra.
- Foi avaliado os outliers para entender o impacto nas vendas.

### 3. **Preparção dos Dados**
- Variáveis numéricas como `YearlyIncome`, `ReceitaTotal` e `FrequenciaCompra`, foram normalizadas usando o metodo de padronização.
- Variáveis categóricas foram codificadas:
  - **Education** (ordinal): Transformada para representar ordem hierárquica.

### 4. **Análise de Clusters**
- O algoritmo **KMeans** foi utilizado para identificar grupos de clientes.
- O número ideal de clusters foi determinado com base no método do cotovelo.
![](https://raw.githubusercontent.com/thiagonoobre/Customer-Insights-Segmentation-KMeans/refs/heads/main/Imagens/cotovelo.png)


### 5. **Visualização e Interpretação**
- Pairplots foram utilizados para visualizar os clusters identificados.
- Insights sobre os perfis dos grupos foram gerados.
![](https://raw.githubusercontent.com/thiagonoobre/Customer-Insights-Segmentation-KMeans/refs/heads/main/Imagens/cluster04.png)

## Resultados e Insights
- **Clientes Valiosos**:
  - **Cluster 3**: Programas de fidelidade e recomendações personalizadas para manter o engajamento.
  - **Cluster 0**: Ofertas promocionais para aumentar a frequência de compra e ticket médio.
  - **Cluster 1** e **2**: Aprofundar a análise para entender subgrupos e o  tipo de produto comprado para criar estratégias específicas.
- **Relações entre Variáveis**: Observou-se uma correlação positiva entre `YearlyIncome` e `ReceitaTotal`, mas nem todos os clientes com alta renda apresentam alta frequência de compra.

## Tecnologias e Bibliotecas Utilizadas
- **Linguagem**: Python e SQL 
- **Bibliotecas**:
  - Manipulação de Dados: `pandas`, `numpy`
  - Visualização: `matplotlib`, `seaborn`
  - Machine Learning: `scikit-learn`

## Como Reproduzir
1. Clone o repositório:
   ```bash
   git clone https://github.com/thiagonoobre/Customer-Insights-Segmentation-KMeans.git
   ```
2. Execute o notebook `Customer-Insights-Segmentation-KMeans.ipynb` para reproduzir a análise.

## Possíveis Expansões
- Implementar outros algoritmos de clustering (como DBSCAN ou Agglomerative Clustering).
- Realizar análises preditivas baseadas nos grupos identificados.
- Integrar dados de vendas com outras fontes, como o tipo de produto comprado.

---

## Contribuição
Sinta-se à vontade para abrir uma issue ou enviar um pull request caso deseje contribuir com melhorias ao projeto.

---

**Autor**: Thiago Nobrega 

**Linkedin**: ([link](https://www.linkedin.com/in/thiagosnobrega/))
