# Classificação do Tempo de Inatividade em Kpi´s de Manutenção na Industria da Mineração, com Base no Modelo de Uso do Tempo e Autoencoder.

----------------------------------------------------------------------------------------------------------------------------------------------------------
Aluno: [Rodolfo Gustavo Stocker Seguel](https://github.com/rodolfostocker).

Orientador: [Leonardo Forero Mendoza](https://github.com/leofome8).

Co-orientadora: [Manoela Kholer](https://github.com/manoelakohler).

----------------------------------------------------------------------------------------------------------------------------------------------------------


Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

[Link para o código](https://github.com/rodolfostocker/TCC_BI2019_4_RS/blob/main/TCC_BI2019_4_RS_TS.ipynb).

----------------------------------------------------------------------------------------------------------------------------------------------------------


Resumo

Hoje em dia,  a principal fonte de preocupação na indústria primária é a ameaça constante de paralisações não planejadas. Mesmo que as orientações de manutenção sejam seguidas para todos os componentes da linha, essas paradas são comuns e afetam a produtividade.
A maior parte do que é feito atualmente nas usinas de mineração envolve estatísticas clássicas e, às vezes, monitoramento de condição online. No entanto, na maioria das indústrias, os dados relacionados ao processo são monitorados e salvos para fins regulatórios. Infelizmente, quase não é usado, enquanto as tecnologias atuais oferecem uma ampla perspectiva de possibilidades.

Introdução:

Uma instalação de mineração não está em conformidade com os números orçados, isso significa que a produção em relação ao orçamento apresentou um déficit no FY11 devido a uma queda na tonelagem de produção menor do que o esperado:
A pré-análise indica que o déficit de produção ocorre porque as tonelagens processadas produzidas foram menores do que o esperado, o que pode estar parcialmente relacionado a uma diminuição no tempo de operação.
O objetivo deste estudo é descobrir explicações ou motivos pelos quais a produção e a saída do britador apresentam uma variação negativa se comparada com o orçamento. Portanto, pode-se presumir que existem algumas variáveis que afetam o rendimento do britador.
Recomenda-se um diagnóstico abrangente, incluindo o modelo de uso de tempo para plantas fixas, que exigirá compreender e levar em consideração, pelo menos, os seguintes pontos:

• Identificar os gargalos de produção (equipamentos).

• Modelo de uso de tempo considerando: Kpi de entradas (atributos) e saídas.

• Dados encontrados nos relatórios diários foram compilados na planta da área de planejamento de curto prazo.

• A análise de dados incluída é de o  período analisado inclui 12 meses de produção dentro do orçamento.

• A disciplina operacional certa para planejar e executar a manutenção programada e não programada, não incluindo a operação do britador rio acima e rio abaixo. 

Definições:

Atualmente no mundo dos negócios, uma das maneiras mais poderosas de usar dados não processados é colocar  os dados para trabalhar para apoiar a tomada de decisão: quanto mais detalhado for aprendido no início, é a primeira etapa na tomada de decisão baseada em dados *.
Todo tipo de tomada de decisão baseada em dados é estabelecida usando fatos para orientar a estratégia de negócios, de forma que a análise de dados possa ser usada para melhorar o processo de negócios, identificar oportunidades de negócios, como um gargalo em uma instalação de processo. Uma vez que isso seja definido, um analista de dados encontrará os dados, então ele os analisará e os usará para encontrar tendências, padrões e relacionamentos.
Os analistas irão questionar os especialistas no assunto (neste caso hipotético em particular, para o engenheiro de confiabilidade **) para definir o problema a ser resolvido e o que poderia ser um resultado bem-sucedido ou pelo menos ajudar a resolvê-lo. A chave é descobrir a combinação exata de dados e conhecimento de negócios, para esta definição de projeto em particular, portanto, combinar fatos e dados com conhecimento de negócios fará parte do processo.

(*) Modelo de uso de tempo: Modelo utilizado para alocar o tempo em diferentes categorias, comparando desempenhos para melhorá-lo.
  
A análise começa com a exploração dos dados do um sub processo de mineração para a  cominuição de minério encontrados em relatórios diários na planta da área de planejamento de curto prazo. Os dados analisados incluem informações de 1º de julho de 2010 a outubro de 2011. O período analisado inclui 12 meses de produção dentro do orçamento.

A primeira pré-análise consiste em descrever estatisticamente um ano do Kpi de manutenção  a partir de um registro operacional off-line para um equipamento de mineração de britagem pesada. Por exemplo, KPI : a Utilização U ***, a disponibilidade A **** e assim por diante.

(*) Processo de tomada de decisão:
A sequência do processo é: definir o problema, coletar informações, coletar dados, desenvolver, pesar opções e selecionar a melhor opção possível, planejar e executar modelos.

(**) Engenheiros de confiabilidade abordam 3 questões básicas:

• Quando algo falha?

• Por que ele falha?

• A probabilidade de falha pode ser reduzida e como?

• observação: Engenharia de confiabilidade é a disciplina que garante que um sistema funcionará conforme necessário, ao longo de um período de tempo especificado, quando operado e mantido de uma maneira específica.

(***) U expresso em porcentagem de utilização: A parte do tempo do calendário em que o equipamento executa sua função principal.

(****) A expresso em porcentagem de disponibilidade: A porcentagem de tempo no calendário em que o equipamento está fisicamente disponível para o trabalho.


Fases do projeto:

Como cientista de dados, irei criar as perguntas certas, abordando os dados apropriados e focando no objetivo principal. Enquanto os analistas e especialistas no assunto (algumas vezes o usuário final) encontram respostas para as perguntas existentes. Criar insights a partir de fontes de dados e análise de dados é o processo de transformar dados em insights.
Assim, do o conceito até o desenvolvimento no pré-lançamento de um produto conceitual, os dados dos ecossistemas são compostos por vários elementos que interagem entre si a fim de gerenciar o processo:
A coleta, transformação e organização de dados para tirar conclusões, leva a classificações e test drive para obter tomadas de decisão informadas.
Um ciclo de fluxo de trabalho de dados começa com a construção de um cronograma de estágios estruturados em uma sequencia finita e única, resumindo as etapas importantes do projecto e colocando as coisas em contexto para gerenciar as expectativas das partes interessadas.

Compreender os requisitos específicos:

Vou começar fazendo algumas perguntas SMART. Essas perguntas devem ser facilmente respondidas por dados históricos mensuráveis e relacionadas a um problema de negócios específico:

Como posso definir o sucesso deste projeto?
“Rápido e preciso o suficiente para ajudar os tomadores de decisão mensalmente, semanalmente e diariamente”. 

Uma análise bem-sucedida deve ser precisa? Quão precisa é a solução? 
Com a precisão adequada, "ou seja, o resultado final deve ser melhor * do que a linha de base", os melhores parâmetros do modelo serão salvos.

(*) Melhor desempenho do modelo: além das explicações acima, deve ser bem executado em termos de custo computacional, impressão de memória e questionar, se o subprocesso será escalável usando, por exemplo, OOP.

Existe uma descrição do conjunto de dados disponível para contextualizar o problema enfrentado?
Este é um conjunto de dados de "domínio não público", consistindo em 360 linhas e 17 atributos.

Compreendendo o dicionário do caso de negócios específico:

Modelo de uso do tempo:Modelo de alocação de tempo em diferentes categorias, com o objetivo de comparar desempenho.

Calendário:(dtype float) Calendário gregoriano acordado internacionalmente, 365 dias por ano, com ano bissexto a cada quatro anos; 24 horas por dia; 60 minutos por hora, 60 segundos por minuto.

Utilização: (dtype float) A porcentagem de tempo no calendário em que o equipamento está executando sua função principal.
Utilização: Tempo de produção / tempo disponível

Disponibilidade: (dtype float) A condição inerente de um equipamento (sob aspectos combinados de confiabilidade, manutenibilidade e suporte de manutenção) para desempenhar a função necessária em um determinado momento, em um período de tempo ou em qualquer momento. A disponibilidade de um equipamento não significa necessariamente que ele esteja funcionando, porém, está pronto para operar.
(Tempo disponível / tempo necessário)

Tempo disponível: (dtype float) O período de tempo em que o item é capaz de executar sua função exigida e é necessário para executar essa função.
Tempo disponível: Tempo de produção- (Processo planejado + Processo não planejado).

Tempo de produção: (dtype float) Tempo medido quando um volume de material mensurável está sendo processado, incluindo atividades incidentais necessárias para manter o ciclo de produção do sistema.

Tempo requerido: (dtype float) Tempo durante o qual o equipamento ou equipe são necessários para operação ou manutenção. (Calendário - Tempo em 'Standby')

Detenção programada: (dtype float) Tempo de detenção programado para um equipamento devido a atividades de manutenção preventiva ou correções programadas. Inclui paralisações devido a equipamentos upstream ou downstream programados.

Tempo de detenção por Manutenção Planejada: (dtype float) Tempo para organizar e realizar as atividades de manutenção com previsão, controle e utilização dos registros de acordo com o processo de planejamento. Manutenção realizada em intervalos predeterminados ou de acordo com critérios prescritos para reduzir a probabilidade de falhas ou degradação do desempenho de um item.

Tempo de detenção agendado para um processo (processo planejado): (dtype float) Tempo de detenção agendado devido às atividades do processo, que interrompe as atividades normais de produção. Estas são atividades de apoio à produção, mas não são produzidas diretamente e geralmente podem ser realizadas a critério da gestão do processo.

Detenção de equipamento: (dtype float) O tempo em que um processo é interrompido quando um equipamento de processo está indisponível para operar. Soma dos tempos de detenção não programados.

Tempo de detenção não programado de um equipamento: (dtype float) É o tempo de inatividade não programado causado por falha ou uma hora extra que excede o tempo de inatividade programado do equipamento além do tempo de manutenção programado planejado.

Standby não programado: (dtype float) O tempo em que um equipamento não é necessário ou não está disponível devido a condições ou razões além do controle direto dos responsáveis pelo processo.

Desconhecido não planejado: (dtype float) O momento em que um processo é interrompido como resultado de um problema desconhecido no equipamento que se torna incapaz de operar e precisa ser atendido ou reparado o mais rápido possível.

Stakeholders, Quem será informado?

Os especialistas no assunto, também o Engenheiro de Confiabilidade (RCM *), compartilhando suas descobertas e recomendações com os líderes de equipe. Posteriormente, a liderança trabalha nos resultados e se concentra na melhoria das áreas-chave da Manutenção.
Estou respondendo à pergunta?
Com o conjunto de dados final rotulado, é possível obter insights valiosos, verificar suposições, reconhecer melhores oportunidades e desafios, apoiar objetivos, fazer melhores planos de manutenção. Ao atualizar o desempenho de manutenção do KPI, os engenheiros de confiabilidade levarão as informações e os efeitos do equipamento para declará-lo fisicamente disponível para o trabalho.

(*) RCM Reliability Centered Maintenance, é uma estratégia de manutenção a nível corporativo implementada para otimizar o programa de manutenção de uma empresa ou instalação.

Entregáveis do projeto:

Apresentação das fases.
Dados disponíveis, o ciclo de vida da análise de dados compilados. O processo de ir da recuperação de dados off-line para a ação. Os dados passam por várias fases: criado, consumido, testado, processado e reprocessado.

Como decido qual modelo se encaixa melhor? Os modelos univariado ou multivariado baseado em proximidade ou densidade, IsoRF, classificador de RF ou regressão logarítmica para classificação. Alem do anterior, sempre que me envolvo em atividades de modelagem, é necessário entender primeiro os dados envolvidos; este é o EDA*.

• O objetivo principal da * EDA é compreender melhor os dados, como transformá-los, se necessário, como avaliar as limitações, suposições 
  inerentes à estrutura de dados e como os dados se encaixam nas estruturas subjacentes, a fim de decidir quais sera o melhor abordagem 
  para o modelagem.

Objetivos de la EDA: 

Como entender os dados para uma modelagem adequada:
• Limpeza de dados: Renomear variáveis, conversão de tipo de dados, codificação de dados se necessário, mesclar conjuntos de dados,  
 transformar variáveis, gerenciar valores ausentes, gerenciar valores anômalos. Nesses casos, será necessário lidar com eles usando outra   abordagem, porque eles podem conter as pistas para novos insights.
  
• Seleção preliminar de modelos apropriados e coleções de ferramentas. 

• Os dados estão em um formato adequado (ponto de verificação), como conjuntos de dados Tidy?

• Revisão da suposição: Fornecendo um resumo descritivo do conjunto de dados.

• Determinar relações entre variáveis.


Modelagem

Várias abordagens para apoiar a tomada de decisão para Análise de Causa Raiz podem ser obtidas usando um Método Clássico amplamente usado em ecossistemas Industriais primários, com base no desvio padrão para detecção de anomalias em um conjunto de dados organizado e, por exemplo, dois Algoritmos de Aprendizado de Máquina para abordagens não supervisionadas (IsoForest) e semi-supervisionadas (Deep Anomaly Detection).
O procedimento final de seleção do modelo ajustado.

• Comecei com o tipo de modelo simples, mas poderoso para classificação. Assim, tive uma idéia do desempenho possível.

• Em seguida, ajustei o modelo mais simples e claro.

• Avaliei o custo de desempenho de usar um modelo mais simples.


Abordagem Não Supervisionada e Semi Supervisionada usando o Modelo AE de Aprendizado Profundo *:


Modelos não supervisionados, como K-Means e AE (para clustering) mais uma regressão logística (como classificador) para anomalias classificadas de parada de equipamentos com o ajuda e know-how dos especialistas no assunto.

O processo de modelagem não supervisionado começa agrupando e reduzindo, capturando poucos atributos em um espaço menor (2D) e, em seguida, marcando a classificação com o objetivo de classificar todos os tipos de anomalias em tipos atípicos, estejam eles presentes nos conjuntos de dados ou em um novo conjunto de dados.

(*) AE, como funciona?
Enquanto o modelo é treinado, ele pode ser aprendido como os recursos ficarão em dados normais e serão compactados em um espacio latente (w) e decodificá-lo de volta como entrada com um pequeno erro. Quando uma anomalia é enviada através do modelo, ele não conseguirá reproduzi-la, pois foi treinado para reproduzir apenas os dados normais e acabará com um grande MSE. Nesse caso, precisamos calcular o MSE da saída em comparação com a entrada e diferenciar corretamente as anomalias, verificando as saídas, precisamos definir um valor limite para MSE de acordo com nossas necessidades para que ele preveja com boa precisão e recuperação.


Modelo final
Uma regressão logística (como classificador) para classificar anomalias de parada de equipamentos com o know-how dos especialistas no assunto.

Conclusão:

Quando descrevemos um modelo contendo variáveis dependentes e independentes, é importante ser o mais preciso possível, mas ao mesmo tempo, usar menos, as variáveis essenciais.
Na melhor das hipóteses, gostaríamos de um modelo parcimonioso e compreensível com excelente desempenho.
Geralmente, há uma relação inversa entre flexibilidade / poder do modelo e interpretabilidade, e este deve ser o foco do trabalho para encontrar as respostas às suas perguntas e, por esse motivo, deve ser apoiado por um especialista no assunto.



'''Downtime classification in mining maintenance Kpi`s, Based on time usage model.’’’ 

Abstract

Nowadays,  remains ones of major source of concern in the primary industry is the constant threat of unplanned downtime. Even if the maintenance guidelines are followed for all the components of the line, these downtimes are common and they affect the productivity.
Most of what is done currently in the mining plants involves classical statistics, and sometimes online condition monitoring. However, in most of the industries the data related to the process is monitored and saved for regulatory purposes. Unfortunately it’s barely used, while the actual technologies offer a wide outlook of possibilities.

Introduction:

A Mining facility  does not comply with the budgeted figures, this means that the  production against budget showed a shortfall in FY11 due to a fall in the production tonnage lower than the expected:
The pre analysis indicates that the production shortfall is because the produced processed tonnages  were less than the expected,  which could be partially related to  a decrease in the run time.
The objective of this study is to find out explanations or reasons why the production and the crusher output have a negative variation if compared with the budget.  Therefore, it could be assumed that there are some variables impacting the crusher throughput.
A comprehensive diagnosis is recommended, including the Time usage model for fixed Plants, which will require to understand and take into consideration at least the following points:

• Identify the  bottlenecks (equipment) in the  process. 

• Time usage model* considering: inputs (attributes) and output Kpi`s, in annual (52 weeks) and monthly timeframes.

• Data found in the compiled daily reports at the Short Term Planning area plant.

• The included data analysis is from 1 July 2009 through October 2010. The period analyzed includes 12 months of on-budget production.

• The right operational discipline to plan and execute the programmed and non-programmed maintenance, not including crusher upstream 
	  and downstream operation.

Definitions:

Currently in business, one of the most powerful ways to use unprocessed data is to put data to work to support decision-making: The more detailed  learned early is the first step in data-driven decision-making*.
All kind of data-driven decision-making is established by using facts to guide the business strategy, so data Analysis can be used to improve the business process, identify business opportunities, such as a bottleneck in a process facility. Once this is defined, a data analyst will find data, then he will analyse and use them to find trends, patterns and relationships.
The analysts will question the subject matter experts (in this particular hypothetical case, to the Reliability engineer ** ) to define both the problem to be solved and what could be a successful result or at least help to solve it. The key is to figure out the exact mix of data and business knowledge for this particular project definition, therefore combining facts and data with business knowledge will be part of the process.

(*) Time Usage Model:Model used to allocate time in different categories, comparing performances in order to improve it.

The analysis begins with the exploration of the comminution mining process data found in daily reports at the Short Term Planning area plant. The analysed data includes information from 1 July 2010 through October 2011 . The period analysed includes 12 months of on-budget production.

The first pre analysis consists in statistically describing one year of KPI ́s maintenance from an off-line operational record for a heavy duty crusher mining equipment. Such as, KPI ́s Result : the Utilisation  U***, the availability A**** and so on.

(*) Decision Making Process
The process sequency is: define the problem, collect information, collect data, develop, weigh options and selection of the best possible option, plan and execute models.

(**) Reliability engineers address 3 basic questions:

• When does something fail?
  
• Why does it fail?
  
• Could the probability of failure be reduced and how?

(*) note: Reliability engineering is the discipline ensuring that a system will function as required over a specified time period when operated and maintained in a specific manner.

(***) U expressed in percentage of Utilisation: The portion of calendar time when the equipment performs its main function.

(****) A expressed in percentage of  Availability: The percentage of calendar time when the equipment is physically available for work.

Project Phases:

As Data scientist, I will create the  right questions, approaching the appropriate data and focusing into the main objective. While the analysts and matter experts (some times the final user) find answers to the existing questions. Creating insights from data sources and data analysis is the process of turning data into insights. 
So, from concept to development in the pre launch of a conceptual product in the ecosystems data is made up of various elements that interact with one another in order to manage the process:  
The collection, transformation, and organisation of data in order to draw conclusions, leads to classifications, and test drive to get informed decision-making.


A data workflow cycle starts with building a timeline of structured stages in a finite, single sequence, summarizing process milestones, and putting things in context to manage stakeholder expectations.

Understanding the Specific requirements:

I will start by asking a few SMART questions. These questions should be easily answered by measurable historical data and related to a specific business problem:

How do I define success for this project?
“Fast and accurate enough to help decision-makers on monthly, weekly and daily regular basis”

Successful analysis needs to be accurate? 
How accurate is the solution? adequate accuracy,” i.e. The bottomline must be better than the baseline,” the best model parameters will be saved. 
Best model meaning: beyond the explanations above, well performed in terms of computational cost, memory impression and inquiring if the subprocess will be scalable by using for instance OOP.

Is there a data set description available to contextualise the faced problem? 
This is data set a non public domain, consisting in 360 rows and 17 attributes.

Understanding the specific Business case dictionary:

Time Usage Model: A model used to allocate time in different categories, with the purpose of comparing performance.

Calendar time: (dtype float) Internationally agreed Gregorian calendar, 365 days per year, with leap year every four years; 24 hours per day; 60 minutes per hour, 60 seconds per minute.

Utilisation: (dtype float) The percentage of calendar time when the equipment is performing its primary function. 
Utilisation: Production time/Available time.

Availability: (dtype float)The inherent condition of an equipment (under combined aspects of reliability, maintainability and maintenance support) to perform the required function in a determined moment, in a period of time, or in any given time. The availability of an equipment does not necessarily imply that it is working, however, it is ready to operate. 
(Available time/Required time).

Available time: (dtype float) The period of time when the item is able to perform its required function and it is required to perform that function. 
Available time: Production Time- (Planned Process + Unplanned Process).

Production time: (dtype float) Time measured when a measurable material volume is under process, including incidental activities needed to maintain the system´s cycle of production.

Time Required: (dtype float)Time during which the equipment or staff are required for operation or maintenance. (Calendar Time – Time in 'Standby')

Scheduled Detention: (dtype float) Detention Time Scheduled for a equipment due to preventive maintenance activities or scheduled corrections. Includes Shutdowns due to scheduled upstream or downstream equipment.

Planned Maintenance: (dtype float) Time to organise and carry out maintenance activities with forecasting, control and use of records according to pre-default planning process.Maintenance performed at predetermined intervals or according to prescribed criteria to reduce the probability of failures or degradation of an item's performance.

Detention Time Scheduled for a process (Planned Process): (dtype float) Scheduled Detention Time due to process activities, which disrupts normal production activities. These are activities to support the production, but are not directly produced and can usually be carried out to discretion of the process management.

Unscheduled Equipment (downtime) / Equipment Detention Time: (dtype float) The time when a process is stopped when a process equipment is unavailable to operate. Sum of unscheduled Detention Times.

Unscheduled detention time of an equipment: (dtype float) It is the unscheduled downtime caused by failure or an overtime that exceeds the equipment's scheduled downtime beyond the scheduled maintenance time planned.

Unscheduled ‘Standby’: (dtype float) The time when an equipment is not required or unavailable due to conditions or reasons beyond the direct control of those responsible for the process.

Unplanned Unknown: (dtype float) The time when a process is stopped as result of an unknown problem in the equipment that becomes unable to operate and needs to be attended or repaired ASAP.

Stakeholders

Who will be informed?
The matter experts, also the Reliability Engineer (RCM *) sharing their findings and recommendations with team leaders. Afterward, the leadership works on the results and focuses on improving key areas of Maintenance.

Am I answering the question?
With the final dataset labeled, is possible to get valuable insights, verify assumptions, recognize better opportunities and challenges, support objectives, make better maintenance plans.  By updating the KPI Maintenance Performance, the Reliability Engineer centers will take equipment information and effects to declare it physically available for work.  

(*) RCM Reliability Centered Maintenance, is maintenance strategy at corporate-level implemented to optimise the maintenance program of a company or facility.

Project Deliverables:

Matter Submission Phases
Data available: Compiled data analysis life cycle.The process of going from off-line Data retrieval (from ERP Qry) to action. 
Data goes through several phases: created, consumed, tested, processed, and reprocessed.

How do I decide which model will fit better? (i.e., Proximity or Density based univariate or multivariate model, IsoRF,RF Classifier or Logarithmic Regression for classification).
Whenever I engage in modelling activity, it is necessary to understand first the involved data; this is EDA*.

(*) The primary purpose for the EDA is to better understand the data, how to transform it, if necessary, how to assess limitations,  inherent assumptions in the data structure and how the data fits in underlying structures in order to decide the best approach to the modelling. 

EDA objectives: How to understand data in order to proper modelling?


• Data Cleaning: Rename variables, data type conversion, encoding data if necessary, merge datasets, transform variables, managing 
	 missing values, managing anomalous values.  In these cases it will be necessary dealing with them using another approach because  
	 they can hold the clues to new insights.
    
• Preliminary select of appropriate models libraries and  data mining tools.
  
• Check point; Is the data in an appropriate format, as Tidy datasets?
  
• Reviewing assumption: Provide descriptive dataset summary
  
• Determining relationships between variables.


Modeling:

Several approaches to support the decision making for Root Cause Analysis is obtainable using a Classical Method widely used on primary Industrial ecosystems based on standard deviation to anomaly detection on tidy dataset and for instance two Machine Learning Algorithms for unsupervised (IsoForest) and semi supervised approaches (Deep Anomaly Detection).
The final model selection procedure could be useful.

• Start with the most powerful simple type of model for classification. Get a sense of the possible performance.
  
• Then fit the more simple /clear model.
  
• Evaluate the performance cost of using a simpler model.

Unsupervised and Semi Supervised Approach using Deep Learning Model AE*:

Unsupervised Models, such as K-Means and AE (for clustering) plus a logistic Regression (as classifier) to classified anomalies of equipment stoppage with the know-how from the matter experts. The unsupervised modeling process begin by clustering and reducing, capturing few features into a latent space (w) and then tagging the classification with the aim of classifying all types of anomalies into outlier types, whether they are present in the datasets or in a new unseen dataset.
(*) AE, how it works? 
While the model is trained it could be learned how the features will look like in normal data and are compressed into a small element and decode it back as input with a small error. When an anomaly is sent through the model, it will fail to reproduce it, since it is trained to reproduce only normal data and will end up with a large MSE. In  that case we need to calculate the MSE of the output compared with the input and correctly differentiate the anomalies, by checking the outputs we need to set a threshold value for MSE according to our needs so that it will predict with good precision and recall.

Final Model

A logistic Regression (as classifier) to classified anomalies of equipment stoppage with the know-how from the matter experts.

Conclusion:

When we describe a model containing dependent and independent variables, it is important to be as accurate as possible, but at he same time to use fewer, the essentials variables.
The best case, we would like a parsimonious and understandable model with excellent performance.
There is usually an inverse relationship between model flexibility/power and interpretability, and this should be the headlights the work over to find the answers to your questions and for that reason is import be supported by subject matter expert.



Matrícula: 123.456.789

Pontifícia Universida de Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
