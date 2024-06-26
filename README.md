# Guia Definitivo do Git - Comandos

O guia tem como objetivo ser um recurso prático, reunindo os comandos mais comuns e necessários para iniciantes que estão se familiarizando com o Git e o versionamento de código.

É fundamental que os leitores deste post estejam familiarizados com a plataforma GitHub e tenham compreensão dos conceitos do Git. O foco será na aplicação prática, portanto as explicações são diretas e concisas.

## Configuração
O primeiro passo essencial é configurar o Git em sua máquina após concluir o processo de instalação, o qual deve estar finalizado neste momento. Para auxiliar nesse processo, você consultar vídeos que mostram como instalar essa ferramenta adequadamente.

1. Verifique a instalação do Git

No terminal digite o comando abaixo para confirmar que a ferramenta está pronta para uso com a versão que foi instalada.

        git --version

2. Configure seu nome de usuário e seu endereço de e-mail

        git config --global user.name "Seu Nome"
        git config --global user.email "seu-email@example.com"

## Criando um Repositório Local
Com o diretório criado, abra o terminal.

    git init
Isso cria automaticamente a pasta `.git` no diretório, confirmando que o Git foi configurado e instalado corretamente. Se desejar remover o Git do diretório, basta excluir a pasta `.git`.


## Criando um Repositório Remoto
Você deve criar um repositório remoto no GitHub e se certificar de que tem um repositório local na sua máquina para fazer a conexão com os dois.
Em seguida, você pode conectar os dois utilizando um dos dois protocolos disponíveis: HTTPS ou SSH.

- HTTPS:

        $ git remote add origin https://github.com/nome-do-usuario/nome-do-repositorio.git
- SSH:

        git@github.com:nome-do-usuario/nome-do-repositorio.git
Após configurar o repositório remoto, você pode enviar suas alterações locais para o GitHub. 

    git push origin master

## Clonando um repositório
Você pode começar a trabalhar em um projeto rapidamente, clonando um repositório do GitHub para sua máquina local e começando a contribuir ou trabalhar no código existente.

      git clone https://github.com/nome-do-usuario/nome-do-repositorio.git

## Rastreando Arquivos
Este comando informa o status dos arquivos no repositório Git.

    git status

## Enviando Modificações (branch padrão)

    git add .
    git commit -m "mensagem"
    git push

## Verificando Alterações Realizadas
Para ver o histórico de alterações no repositório, mostrando todos os commits com informações detalhadas:

    git log
Para ter um histórico resumido, esse comando mostra cada commit em uma única linha:

    git log --oneline
Para ver apenas os dois últimos commits:

    git log -n 2
Para sair do `git log`, pressione a tecla `q`.

## Ignorando Arquivos 
Para ignorar arquivos que você não deseja versionar em seu projeto Git, você pode utilizar o arquivo .gitignore. Você deve criar caso ainda não tenha no projeto e não esqueça de adicionar na área de stage para que as alterações sejam registradas.

    git add .gitignore
Aqui estão alguns exemplos de como você pode especificar quais arquivos e diretórios devem ser ignorados pelo Git:
Para ignorar um arquivo específico:

    arquivo.txt
Para ignorar todos os arquivos de um diretório:

    /diretorio/
Para ignorar todos os arquivos com uma extensão específica:

    *.js

## Removendo Arquivos
Para remover um arquivo do repositório Git, você precisa executar o comando abaixo, não esqueça de adicionar essa alteração à área de stage e realiza um commit para efetivar a remoção.

    git rm arquivo.html
    git add .
    git commit -m "removendo o arquivo html"

## Renomeando e Movendo Arquivos
Para essas duas ações utilizamos do mesmo comando com algumas modificações. Isso também requer que você adicione as mudanças à área de stage e realize um commit.

- Renomear um Arquivo:

        git mv arquivo.html produtos.html

- Mover um Arquivo para um Novo Diretório:

        git mv icon.png img/icon.png


## Verificar mudanças ainda não rastreadas
O comando mostra as alterações feitas nos arquivos que já foram comitados pelo menos uma vez e expõe as diferenças entre o que foi comitado e o que foi alterado fora da área de stage.

    git diff

## Verificar mudanças rastreadas
Para verificar as mudanças entre os arquivos que estão na área de stage, utilize o mesmo comando, mas com o parâmetro --staged:

    git diff --staged

## Verificar mudanças rastreadas e não rastreadas ao mesmo tempo
Os comandos anteriores são específicos para essas funções portanto para reunir os dois tipos de mudanças em um único comando é necessário especificar a commit.

- Primeiro obtenha o código da commit

        git log -n 1 --oneline
- E use o código da commit para ver todas as mudanças

        git diff <commit-codigo>

- Exemplo:

        git diff 333ccdd

## Verificar mudanças já comitadas
Para verificar mudanças que já foram comitadas é necessário especificar quais commits você quer comparar.

- Verificando a partir do commit `333ccdd` até o commit `995eede`:

        git diff 222cccc..995eede

- Uma forma mais simples seria o código para verificar dois commits anteriores a commit especificada:

        git diff 995eede~

## Desfazendo mudanças não rastreadas
O comando `git checkout` é utilizado para navegar entre branches, mas também pode ser usado para desfazer alterações em arquivos que ainda não foram adicionados à área de stage.

Esse comando desfaz as alterações feitas que ainda não foram adicionadas à área de stage:

    git checkout -- produtos.html

Também pode recuperar arquivos apagados acidentalmente.

## Desfazendo mudanças já rastreadas
O `git reset` remove todos os arquivos da área de stage e mantém as alterações no diretório de trabalho para que possam ser revisadas.

     git reset

Para desfazer as alterações no arquivo em um único arquivo que foram adicionadas na área de stage:

    git reset --produtos.html
Diferente do `git reset`, o parâmetro `--hard` define que todas alterações na área de stage devem ser descartadas e as mudanças no diretório de trabalho também são deletadas.

    git reset --hard

## Desfazendo mudanças já comitadas
O `git revert` é útil para desfazer commits sem alterar o histórico do repositório, criando um novo commit que desfaz as mudanças de um commit anterior. 

Ele requer um commit específico a ser revertido portanto não pode ser especificado sem parâmetros.

Esse comando cria um novo commit que desfaz as alterações do commit `88877ee`:

    git revert --no-edit 88877ee

O parâmetro `--no-edit` serve para que o editor de texto não abra para editarmos a mensagem do novo commit. Também é possível trocar o código da commit por `HEAD` que referencia o último commit.

    git revert --hard 88877ee

O comando redefine o repositório para o estado do commit `88877ee`, descartando todos os commits subsequentes e todas as mudanças não commitadas.

## Em breve

Conteúdo sobre branch remota e local, merge e tags.

## Finalização

Obrigado por chegar até aqui! Espero que este material facilite seus estudos e seja útil na sua prática com esta excelente ferramenta para versionamento de código.
