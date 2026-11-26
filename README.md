# Atividade4NeuroStartup
Aluno:Gabriella Sousa de Oliveira RA:2869704 Turma:BCC

## 📋 Resumo do projeto

### 1. Conhecendo os dados
**Problema:** uma loja online precisa classificar manualmente as fotos de roupas que recebe. Criamos um modelo que olha a foto e diz a categoria da peça, entre 10 opções (camiseta, calça, pulôver, vestido, casaco, sandália, camisa, tênis, bolsa e bota).

**Dados:** Fashion-MNIST, com 70.000 fotos 28x28 em tons de cinza.

**Gráficos e conclusões:**
- **Fotos por categoria:** todas as categorias têm 7.000 fotos, então os dados estão equilibrados e a acurácia é uma métrica justa. Chutando sempre a mesma categoria, o acerto seria só 10%.
- **Foto média de cada categoria:** calça, bolsa e calçados têm formatos bem diferentes. Já camiseta, pulôver, camisa e casaco são parecidos, então esperávamos que o modelo confundisse essas peças.

**Separação dos dados:**
| Grupo | Quantidade | Uso |
|---|---|---|
| Treino | 42.000 (60%) | o modelo aprende |
| Validação | 14.000 (20%) | comparar os modelos |
| Teste 🔒 | 14.000 (20%) | usado uma única vez, no final |

### 2. Baseline x Rede neural
- **Baseline:** regressão logística nos 784 pixels → 85,2% na validação
- **Bônus:** árvore de decisão (max_depth=15) → 80,5% na validação
- **Rede Keras:** Flatten → Dense (relu) → Dropout → Dense(10, softmax), otimizador Adam
- **Early stopping:** o treino para quando a perda na validação não melhora por 3 épocas e a rede volta para os melhores pesos.

**Experimentos (`experimentos.csv`):**
| Tentativa | Neurônios | Dropout | Épocas | Acurácia validação |
|---|---|---|---|---|
| 1 | 64 | 0.0 | 87,9%% |
| 2 | 128 | 0.2 | 88,6% |
| 3 | 256 | 0.3 | 88,7%

**Melhor rede:** tentativa ___. Nas curvas de aprendizado, a perda da validação parou de cair por volta da época ___, e o early stopping parou o treino ali.

### 3. Resultado no teste (cofre)
| Modelo | Validação | Teste |
|---|---|---|
| Regressão logística (baseline) | 84,5%|
| Árvore de decisão (bônus) | 80,9% |
| **Rede neural** |89%|

A rede foi ___ pontos percentuais melhor que o baseline no teste. Pela matriz de confusão, os maiores erros aconteceram entre ___ e ___, como esperávamos pela foto média.

> **Frase de negócio:** a cada 1.000 produtos cadastrados, nosso modelo acerta a categoria de ___ sozinho, contra ___ do modelo simples. São ___ produtos a menos para corrigir na mão.

### 4. Produto
- Modelo salvo em `modelo_fashion.keras`, que pode ser carregado sem treinar de novo.
- Tela interativa no notebook: você escolhe uma foto do teste e a tela mostra a categoria real, o palpite do modelo e a confiança dele.

<img width="711" height="390" alt="image" src="https://github.com/user-attachments/assets/6395ac89-c186-43e9-8c13-f78e294b741e" />


### 5. Como rodar
1. Abra o `classificadorroupas.ipynb` no Google Colab (Arquivo → Fazer upload de notebook).
2. Rode tudo em Ambiente de execução → Executar tudo.
3. A última célula baixa o `experimentos.csv` e o `modelo_fashion.keras`.

## Declaração de uso de IA

Neste projeto usei o assistente de IA **Claude (Anthropic)** como apoio. A IA foi usada para:

- **Explicar o código inicial** (carregamento dos dados, gráficos, separação treino/validação/teste e modelos baseline) em linguagem simples;
- **Conferir o projeto em relação à rubrica** e apontar o que estava faltando;
- **Gerar o código das etapas que faltavam**: rede neural no Keras, experimentos com early stopping, curvas de aprendizado, avaliação no teste, matriz de confusão, salvamento do modelo e tela interativa;


**O que eu fiz:**
- Escrevi o código inicial de exploração dos dados e dos modelos baseline;
- Rodei o notebook completo e conferi os resultados;
- Escrevi as conclusões, a frase de negócio e as tabelas de resultados com os números obtidos;
- Revisei todo o conteúdo e me certifiquei de entender cada etapa do código.

Sou responsável por todo o conteúdo entregue.
