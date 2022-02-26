# Notas das Aulas - Introdução ao Git e GitHub 



## Informações Básicas

**Professor:** Otávio Reis

**Tempo de duração:** 5h

**Descrição:** Curso de condução do usuário com o primeiro contato com as tecnologias Git e GitHub.



**Conteúdo trabalhado / Habilidades Desenvolvidas:**

- Entendo o que é Git e sua importância;

- Comandos básicos em terminais; 

- Instalação do Git;

- Tópicos fundamentais para entender o funcionamento do Git;

- Objetos internos do Git;

- Chave SSH e Token;

- Iniciando o Git e criando um commit;

- Passo a passo no ciclo de vida;

- Trabalhando com o GitHub;

- Como os conflitos acontecem no GitHub e como resolvê-los.

  

## Softwares utilizados em aula

- [Git](https://git-scm.com/download/win);

- [GitHub](https://github.com/).

  

## Notas Pessoais a Respeito do Conteúdo

**Git:**

 - Software de sincronização de códigos

 - Existem outros sincronizadores: CRV... (Não tão bons)

 - Desenvolvido por Linus Torvald (criador Linux) motivado pelos péssimos softwares da época

  

**GitHub:**

 - Repositório onde se armazena os códigos e que utiliza a tecnologia GIT para sincronizar
 - Existem outros repositórios: Gitlab... (bons que variam daí conforme o pacote de oferta)
 - Interfaces: GUI (Grafic User Interface) x CLI (Comand Line Interface)
 - Comandos p/ Windows ser usados em CLI:
  	- CMD (pra abrir terminal)
  	- dir (lista de diretórios da pasta)
  	- cd (change directory ) - (entra na pasta)
  		- cd / - vai pra pasta raiz
  		- cd windows vai pra pasta windows
  		- cd .. - volta uma pasta (retrocede um nível)
  	- cls (clear screen) - (limpar a tela)
  	- TAB (para autocompletar)
  	- mkdir (make directory) - Criar pasta
  	- echo (printa alguma coisa no terminal)
  	- echo > texto que quer printa.txt (cria um arquivo txt na pasta)
  	- del nomedapasta - (remove todos os arquivos que estão dentro da pasta)
  	- rmdir nomedapasta /S /Q (remove directory) - (apaga a pasta)



- Comandos p/ Unix (Linux/Mac):
  - ls (lista de diretórios da pasta)
  - ls -a (mostra as pastas ocultas)
  - cd (change directory ) - (entra na pasta)
    - cd .. - volta uma pasta (retrocede um nível)
    - clear (ou CTRL + L) - (limapr a tela) 
    - mkdir (make directory) - Criar pasta
    - echo > texto que quer printa.txt (cria um arquivo txt na pasta)
    - rm -rf nomedapasta (apagar a pasta)	



**Entendendo o funcionamento do Git**

- SHA1 (Secure hash algorithm)

  -  Desenvolvido pela NASA

  - Encriptografa objetos

  - Encriptogração gera conjunto de caracteres identificador de 40 dígitos único

  - Se o conjunto de caracteres for igual significa que o texto/código está exatamente igual.

    

- Objetos Fundamentais
  - Blobs
    - Contém metadados
    - Os arquivos ficam guardados em blobs (bolhas)
    - Os blobs possuem tipo, tamanho, \0, conteúdo do arquivo(texto)
      echo -e 'blob 9\0conteudo' | openssl sha1
      =
      echo 'conteudo'| git hasj-object --stdin
  - Trees
    - Armazenam Blobs
    - Responsável por montar a estrutura de onde estão os arquivos 
    - Contém metadados: tipo(trees), tamanho, \0, blob, sha1, nome do arquivo
  - Commits
      - Commits junta tudo
      - Commits aponta para: árvores, parente (úlitmo commit realizado antes dele), autor, mensagem, timestamp (carimbo de tempo)
      - Commits também possuem SHA1



- Sistema Distribuído

  - Distribuição segura da mesma versão entre o servidor e vários computadores ao mesmo tempo baseados nos itens anteriores

    

- Chave SSH P/ Windows:

  - Comando para criar SSH (Usar no Git Bash): ssh-keygen -t ed25519 -C e-mail

  - local onde a pasta foi armazenada: (/c/Users/User/.ssh/id_ed25519)

  - criar senha 

  - Entrar na pasta cd /c/Users/User/.ssh/

  - Comando para mostrar codigo publico: cat id_ed25519.pub 

  - Copiar o código exibido e colar na página do github chave ssh

  - Depois voltar para Git Bash, na pasta cd /c/Users/User/.ssh/

  - Colocar o comando  eval $(ssh-agent -s) ---> isso exibe o número do processo que está rodando em 2plano

  - Precisa entregar a chave privada:  ssh-add id_ed25519

  - Como clonar um repositório para sua máquinas:

  - git clone ("cola o caminho SSH pego lá no repositório do github)

    - (primeira vez dá uma mensagem: reponde yes)

      

- Token

- No github: Settings --> Developer settings --> Prersonal access tokens -->  Generate new token

- Dá um nome, Marca opção Repo e Clica lá embaixo Generate Token

- Copiar e salva esse token em algum lugar seguro

- Para clonar um repositório pelo link https, é preciso utilizar o tolken



**Iniciando no Git**

 - git init (inicia um repositório dentro da pasta)

Primeira vez que acessa o git, precisa configurar para identificar o usuário
	- git config --global user.email "digita@email.com"
	- git config --global user.name escolhe um username
	- git config --global unset user.email (quando quiser apagar o e-mail inserido)
	- git config --global unset.user.name (quando quiser apagar o nome inserido)
 - git add *  (função que faz o Git enviar todas as modificações pra Staged)
- git add .  (função que faz o Git enviar todas as modificações pra Staged)
- git add "nomedoarquivo" (adiciona arquivo específico no Staged)
- git status (mostra o status das alterações)
- git commit -m "mensagem do commit" (commita as alterações - tira do Staged e coloca na posição unmodified)
- git remote add origin "link-https-do-repositório no github" (adicionando em qual repositorio do github o projeto vai ser linkado)
- git remove -v (exibe quais repositórios ele está linkad)
- git push origin master (empurra o repositório para o link setado)
	- vai pedir validação



**Tracked e Untracked**

	- Untracked arquivos que o GIT não tem ciência deles
	- Tracked arquivos que o GIT tem ciência deles
		- Unmodified: Arquivo sem alterações
		- Modified: Arquivo que já sofreu alguma alteração
		- Staged: Arquivos prontos aguardando serem salvos em um commit
		- Quando os arquivos são salvos em um commit (volta ao status unmodified)
		**Snapshot (Fotografia de como o código está -- tirada quando dá um commit)	

**Repositórios:**

- 2 ambientes: 

  - Ambiente de desenvolvimento (máquina)

    Working Directory (o que você criou)

      - Staging Area 
      - Local Repository (vai p/ cá quando dá commity) (coisas daqui podem ir para o repositório remoto)

  - Remote Repository (Servidor/GitHub)

    

**Como gerenciar conflitos**

- ele avisa que as versões estão diferentes

- o usuário puxa o que tá lá pra sua máquina pra você verificar utilizando:

  - git pull origin master

- o usuário encontra manualmente o erro

- verifica qual versão quer manter 

- empurra novamente o código para o GitHub

  - git push origin master

    

**Como clonar diretório https**

	- git clone "colar_link_https_do_diretorio"