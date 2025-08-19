# 🤖 Assistente Virtual da Receita Federal

Um sistema de inteligência artificial baseado em RAG (Retrieval-Augmented Generation) que utiliza LlamaIndex para fornecer respostas precisas sobre questões tributárias da Receita Federal do Brasil.

## 📋 Descrição

Este projeto implementa um assistente virtual especializado em questões fiscais e tributárias, capaz de responder perguntas sobre:

- **Imposto de Renda Pessoa Física (IRPF)**: Deduções, isenções, declaração de bens, rendimentos de aluguel, ganho de capital
- **Imposto de Renda Pessoa Jurídica (IRPJ)**: Tributação de empresas, regimes de apuração (Lucro Real, Lucro Presumido)
- **Contribuições Sociais**: PIS/Pasep, Cofins, CSLL
- **MEI (Microempreendedor Individual)**: Questões específicas para pequenos empresários

## 🏗️ Arquitetura

O sistema utiliza uma arquitetura RAG com os seguintes componentes:

- **LlamaIndex**: Framework para construção de aplicações RAG
- **Gemini (Google)**: Modelo de linguagem para geração de respostas
- **Gemini (Google)**: Modelos de embedding para busca semântica
- **Vector Store**: Indexação vetorial dos documentos da base de conhecimento

## 🚀 Instalação

### Pré-requisitos

- Python 3.8+
- Conta no [Groq](https://groq.com/) para API key
- Conta no [Hugging Face](https://huggingface.co/) para API key
- Conta no [Google AI Studio](https://aistudio.google.com/) para API key do Gemini

### Configuração

1. **Clone o repositório:**
```bash
git clone <url-do-repositorio>
cd projeto-rag
```

2. **Crie um ambiente virtual:**
```bash
python -m venv .venv
source .venv/bin/activate  # Linux/Mac
# ou
.venv\Scripts\activate     # Windows
```

3. **Instale as dependências:**
```bash
pip install -r requirements.txt
```

4. **Configure as variáveis de ambiente:**
Crie um arquivo `.env` na raiz do projeto:
```env
GROQ_API_KEY=sua_chave_groq_aqui
HF_API_KEY=sua_chave_huggingface_aqui
GOOGLE_API_KEY=sua_chave_google_aqui
```

## 💻 Como Usar

### Opção 1: Notebook Jupyter

1. Inicie o Jupyter:
```bash
jupyter notebook
```

2. Abra o arquivo `projeto-av-receita-federal.ipynb`

3. Execute as células sequencialmente para:
   - Configurar o ambiente
   - Carregar a base de conhecimento
   - Fazer consultas ao assistente

### Opção 2: Script Python

Execute o script principal:
```bash
python assist_receita-federal.py
```

### Exemplos de Uso

```python
# Consulta sobre IRPF
response = pf_query_engine.query("Como declaro o aluguel que recebi de um imóvel?")

# Consulta sobre IRPJ
response = pj_query_engine.query("Em que casos a Contribuição para o PIS/Pasep e a Cofins são apuradas pelo regime de caixa?")

# Usando o agente inteligente
response = agent.run("Como declaro o aluguel que recebi de um imóvel?")
```

## 🔧 Configurações

### Modelos Utilizados

- **LLM**: Gemini 2.5 Flash (Google)
- **Embedding**: Gemini Embedding 001
- **Chunk Size**: 1024 tokens
- **Chunk Overlap**: 200 tokens
- **Similarity Top-K**: 3 documentos

### Prompt Template

O sistema utiliza um prompt template personalizado para gerar respostas acessíveis e em português:

```
"Atue como um assistente de imposto de renda amigável. 
Use apenas as informações de contexto fornecidas para responder à pergunta do usuário. 
Responda em português, de forma simples, direta e fácil de entender, 
como se estivesse explicando para alguém sem conhecimento do assunto."
```

## 📊 Funcionalidades

### 1. Busca Semântica
- Indexação vetorial dos documentos PDF
- Busca por similaridade semântica
- Ranking de relevância das fontes

### 2. Agente Inteligente
- Seleção automática da base de conhecimento apropriada
- Respostas contextualizadas
- Rastreamento das fontes utilizadas

### 3. Múltiplas Bases de Conhecimento
- **Pessoa Física**: Questões sobre IRPF
- **Pessoa Jurídica**: Questões sobre IRPJ e contribuições
- **MEI**: Questões específicas para microempreendedores

### 4. Transparência
- Exibição das fontes consultadas
- Scores de relevância
- Trechos dos documentos utilizados

## 🛠️ Tecnologias

- **LlamaIndex**: Framework RAG
- **Gemini**: Modelo de linguagem (Google)
- **Hugging Face**: Embeddings e transformers
- **PyTorch**: Framework de machine learning
- **Jupyter**: Ambiente de desenvolvimento
- **Python-dotenv**: Gerenciamento de variáveis de ambiente

## 📝 Dependências Principais

```txt
llama-index-core>=0.10.0
llama-index-llms-gemini
llama-index-embeddings-gemini
transformers>=4.40.0
sentence-transformers>=2.6.0
torch>=2.1.0
jupyter
python-dotenv
```

## 🤝 Contribuição

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.

## ⚠️ Aviso Legal

Este assistente virtual é uma ferramenta educacional e informativa. As respostas fornecidas são baseadas na documentação oficial da Receita Federal, mas não substituem a consulta a um profissional contábil ou jurídico. Sempre consulte um especialista para questões fiscais específicas.

## 📞 Suporte

Para dúvidas ou problemas:
- Abra uma issue no repositório
- Consulte a documentação do LlamaIndex
- Verifique as configurações das APIs

---

**Desenvolvido com ❤️ para facilitar o acesso à informação tributária** 
