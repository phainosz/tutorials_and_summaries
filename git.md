# Anotações gerais sobre Git

## Instalação
- [Git](https://git-scm.com/)
- Verificar versão com `git version`

## Comandos gerais
- Para iniciar um repositório `git init`
- Configurar usuário global `git config --global user.name "<USER>"`
- Configurar email global `git config --global user.email "<EMAIL>`
- Para clonar um repositório remoto para local `git clone <URL>.git`

## Commits
- Verificar modificações e arquivos alterados `git status`
- Adicionar itens para a área staged `git add <FILE>` ou `git add .`
    - Arquivos em staged são os que farão parte do próximo commit
    - Arquivos modificados que não estão na área de staged são chamados de 'Untracked files'
- Para fazer um commit `git commit -m "<MESSAGE>"`
    - -m Serve para adicionar a mensage
    - Quando precisar alterar a mensagem do último commit sem ter feito o envio para o repositório, utilizar amend
        - Ex: `git commit --amend -m "<NEW_MESSAGE>"`
    - Também é possível altera o último commit com mais arquivos usando o amend, basta adicionar com o add e depois fazer o amend
    - Quando o commit for com todos os arquivos alterado, pode-se utilizar add + commit `git commit -am "<MESSAGE>"`
- Após fazer o commit, fazer o envio para o repositório remote com `git push`

## Branchs
- Criar nova branch `git checkout -b <NAME>`
- Listar todas as branchs local `git branch`
- Listar todas as branchs remotas `git branch -r`
- Listar todas as branchs `git branch -a`
- Mudar de branch `git checkout <NAME>`
- Mudar de branch para uma branch remota fazendo o tracking local com remota `git checkout -t <NAME_REMOTE>/<NAME>`
    - NOME_REMOTE indica o nome do repositório remote, podendo ser encontrado através de `git remote -v`
    - NOME seria o nome da branch remota
- Deletar branch local `git branch -D <NAME>`
- Deletar branch remota `git branch <NAME_REMOTE> --delete <NAME>`
- Alterar o nome da branch local. mudar para a branch que quer mudar e fazer `git branch -m <NEW_NAME>`
- Alterar o nome da branch remota `git push <NAME_REMOTE> <OLD_BRANCH> <NEW_BRANCH>`

## Remote
- Para verificar os repositórios remotos mapeados `git remote -v`
- Adicionar um repositório remoto `git remote add <NAME> <URL>.git`
- Renomear o remoto `git remote rename <OLD> <NEW>`
- Remover o remoto `git remote rm <NAME>`
- Alterar o endereco remoto `git remote set-url <NAME> <URL>.git`

## Stash
- É como um arquivo temporário das alterações feitas localmente. Funciona como uma pilha LIFO.
- Para adicionar no stash `git stash`
- Para adicionar ao stash com nome `git stash push -m <NAME>`
- Para listar itens do stash `git stash list`
    - Irá retornar algo como `stash@{0}: WIP on something: f2c0c72... My super commit message`
    - stash@{0} é a identificação do stash na pilha mudando apenas do número {0} para frente
- Para recuperar o último stash adicionado `git stash pop`
- Para recuperar por um stash específico `git stash pop stash@{n}`
    - Usar `git stash list` e trocar n com o número do stash desejado
- Para remover o primeiro item da lista de stashes `git stash drop`
- Para remover um stash específico, semelhante ao pop `git stash drop stash@{n}`