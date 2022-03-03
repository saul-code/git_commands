# Git

Created: March 1, 2022
Created by: Anonymous
Tags: Programación

# Git comandos

## Comandos Básicos

---

- *$ **git** init*
    
    inicializar el repositorio en la carpeta actual (se crea la carpeta .git)
    
- *$ **git** status*
    
    ves las carpetas y archivos que se modificaron que no están en el stage
    
- *$ **git** status -s -b*
    
    estiliza el git status y te indica la rama
    
- $ ***git** commit -m “Nombre del commit”*
    
    commiteas los archivos en el stage para agregar una versión en la línea de tiempo
    
- $ ***git** commit --amend -m “Nuevo nombre del commit”*
    
    amend es cómo enmendar, está enmendando el error del nombre del commit
    
- *$ **git** log*
    
    ves tu línea del tiempo de versiones
    
- $ ***git** log --oneline --decorate --all --graph*
    
    Crear un git log estilizado
    
    ```bash
    $ **git** log --oneline --decorate --all --graph
    * 0cf21t6 (HEAD -> master) Se modifico el index.html
    * c431a97 Se modifico el main.css
    * 37dsqw1 Indez html has been created
    
    ```
    
- $ **git** diff
    
    ve las diferencias entre el commit actual a los cambios fuera del staged
    
- $ **git** diff --staged
    
    si agregaste archivos al stage los compara con los archivos del commit actual
    
- $ ***git** diff (rama actual) (rama con la que quieres comparar)*
    
    te compara los cambios hechos entre ramas
    
- $ ***git** mv (nombre del archivo) (nuevo nombre del archivo)*
    
    cambia el nombre del archivo y lo guarda en staged, para agregar el nuevo commit
    
- $ ***git** rm (nombre del archivo)*
    
    borra un archivo, y guarda esa info de que se borró el archivo en staged y lo puedes commitiar
    
- $ **git** checkout (nombre de la rama)
    
    te cambia la rama en la que estés a la que escribiste
    
- $ ***git** reflog*
    
    veremos todas la modificaciones que hemos hecho a la línea del tiempo aunque las hemos borrado
    
    ![Untitled](Git%20f9576/Untitled.png)
    

## Stash

---

- $ **git** *stash*
    
    guarda temporalmente los cambios que hayas hecho sin hacer ningún commit y te regresa al último commit
    
    ```bash
    $ git s
    ## master
    M main.py
    $ git stash
    Directorio de trabajo guardado y estado de índice WIP on master : 0cf21t6 Agregamos misiones
    $ git lg 
    * f5494ec (refs/stash) WIP on master : 0cf21t6 Agregamos misiones
    |\
    | * d66f12c index on master : 0cf21t6 Agregamos misiones
    |/
    * 0cf21t6 (HEAD -> master) Se modifico el index.html
    * c431a97 Se modifico el main.css
    * 37dsqw1 Indez html has been created
    ```
    
- $ **git** stash list
    
    Muestra los stash que tienes
    
    ```bash
    $ git stahs list
    stash@{0} : WIP on master : 0cf21t6 Agregamos misiones
    ```
    
- $ ***git** stash pop*
    
    Elimina los stash que tienes y regresa al stash deseado (puede haber conflictos y se resuelve como un merge)
    
    ![Untitled](Git%20f9576/Untitled%201.png)
    
- $ ***git** stash drop*
    
    Elimina un stash que ya no quieras y te deja en el HEAD
    
- $ ***git** stash -u*
    
    Guarda en el stash los archivos no seguidos por git
    
- $ ***git** stash clear*
    
    Borra todos los stash en la lista como un drop
    

## Tag

---

- $ ***git** tag*
    
    muestra los tags existentes
    
- $ ***git** tag (nombre del tag)*
    
    se pone el tag en el commit actual
    
- $ ***git** tag -a (nombre del tag ) -m “Anotaciones del tag”*
    
    nombra el tag y crea una anotación
    
- $ ***git** tag -a (nombre del nuevo tag) (ssh del commit) -m “Anotación del tag”*
    
    Crea un tag con cierta anotación a un commit especificado que puede que no sea el commit actual
    
- $ ***git** tag -d (nombre del tag)*
    
    Borra el tag
    
- $ ***git** show (nombre del tag)*
    
    Muestra información del tag
    
    ![Untitled](Git%20f9576/Untitled%202.png)
    

## Tipos de Reset

---

- $ ***git** reset (Nombre del archivo)*
    
    lo que hace es quitar del staged ese archivo
    
- $ ***git** reset --soft HEAD^*
    
    resetea el commit al commit anterior
    
- $ ***git** reset --mixed  e77ed28(el commit al que quieres ir )*
    
    se regresa al commit especificado sin perder los cambios hechos posterior a ese commit, se quedan en el staged
    
- $ ***git** reset  --hard e77ed28(el commit al que quieres regresar)*
    
    -se regresa al commit especificado perdiendo todos los cambios posteriores a ese commit
    
    -también sirve para revertirse a sí mismo, viendo el hash en git reflog y usando el mismo comando de git reset --hard  *e77ed28()* vuelves al futuro
    

## Branchs

---

- $ ***git** branch (nombre de la nueva rama)*
    
    crea una rama llamada (nombre de la nueva rama)
    
- $ **git** branch -d (rama que quieres borrar)
    
    borra la rama que quieres
    
- $ ***git** branch -a*
    
    te muestra una lista de todas las ramas, hasta las ramas remotas
    
- $ ***git** checkout -b (nombre de la nueva rama)*
    
    Crea una nueva rama y te mueve a ella
    
- $ ***git** merge (rama que quieres unir)*
    
    Une la rama actual con la que quieres, puede que sea fast-forward si no hay conflictos
    
- $ ***git** rebase (master)*
    
    mueve el inicio de tu rama al Head de master y luego hace un merge fast forward, entonces tu rama master se queda con el historial de de tu otra rama
    
- $  ***git** rebase -i HEAD~(numero)*
    
    Es un rebase interactivo, usamos el reword y el squash para juntar commit
    es como un amend pero a lo bestia
    
    ![Untitled](Git%20f9576/Untitled%203.png)
    

## Configuraciones

---

- $ **git** config --global -e
    
    Abre un archivo que te dice las configuraciones que se han hecho, se puede modificar pero recomendable no hacerlo porque tiene un formato y si no lo sigue da error
    
    ```
    [user]
    				email = esoteriko@ciencias.unam.mx
    				name = Saul
    
    [alias]
    				lg = log --oneline --decorate --all --graph
    				s = status -s -b
    ```
    
- $ **git** config --global alias.nombredelalias “comando”
    
    crea un alias a un comando largo para hacerlo más rápido
    

## Comandos de Gitghub

---
