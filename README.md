Detecção e Auditoria de Fraudes em Entregas de E-commerce
Este projeto foi desenvolvido com o objetivo de identificar e mitigar comportamentos fraudulentos (desvios de carga e falsas alegações de não recebimento) no ecossistema de entregas de uma operação de e-commerce, mapeando o risco tanto de clientes quanto de entregadores.

A Pesquisa e Pilares de Análise
Para diferenciar erros operacionais comuns de fraudes reais, a pesquisa estabeleceu um perfil de risco baseado na combinação de 3 pilares fundamentais:
Volume/Frequência: Identifica se a taxa de problemas (pedidos com itens faltantes) está acima da média normal histórica do sistema (> 15%).
Impacto Financeiro: Avalia o montante do prejuízo acumulado gerado por aquela entidade (> $100).
Direcionamento (Alvo): Analisa a categoria dos itens que sumiram. Fraudes profissionais costumam focar em produtos com alto valor de revenda, como Eletrônicos.

O Algoritmo de Score
A inteligência do projeto centraliza esses pilares em um modelo preditivo de pontuação que varia de 0 a 4 pontos, aplicando pesos de acordo com a gravidade das métricas calculadas em tempo real:
+1 Ponto: Se a taxa de problemas for maior que 15%.
+1 Ponto: Se o prejuízo total causado for maior que $100.
+2 Pontos: Se houver sumiço de itens da categoria Eletrônicos (peso dobrado devido ao risco do produto).

Matriz de Interpretação
Score 0 a 1 (Erro Operacional Comum): Falhas logísticas ou de separação rotineiras.
Score 2 a 3 (Comportamento Suspeito): Requer atenção e auditoria leve direcionada.
Score 4 (Altíssima Probabilidade de Fraude): Foco principal da análise e acionamento de travas de segurança.

Estrutura do Código Central
O pipeline de dados foi totalmente construído em Python (Pandas) para garantir estabilidade e performance no tratamento das tabelas brancas (orders, missing_items, products, customers, drivers), executando os seguintes passos automáticos:
Engenharia de Recursos (Feature Engineering): Limpeza de strings de preços e reestruturação de tabelas de formato wide para long.
Consolidação de Métricas: Agrupamento e cálculo de taxas e prejuízos financeiros por indivíduo.
Modelagem de Risco: Aplicação das regras de negócio do score e classificação das tabelas de "Top Fraudes".
Exportação Otimizada: Geração de arquivos .csv e .json estruturados para autodeclaração de colunas e auto-expansão automática no Excel / Power Query / Power BI.
Tecnologias Utilizadas: Python, Pandas, Numpy, Análise Preditiva de Risco.
