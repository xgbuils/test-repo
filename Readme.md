Inicialmente tengo dos commits en el repositorio local y en github.

```
commit a200541743477ef80efd99c45dbe93320f2689e3
Author: Xavier Garcia Buils <xgbuils@gmail.com>
Date:   Sun Jan 4 13:56:02 2015 +0100

    2 commit

commit 9c9a74a9592087dff533cf380b145e0088ef7892
Author: Xavier Garcia Buils <xgbuils@gmail.com>
Date:   Sun Jan 4 13:53:21 2015 +0100

    primer commit
```

Entonces las ramas `master` y `origin/master` del repositorio local apuntan al último commit.

Yo quiero que en github `master` apunte al primer commit pero de momento esta apuntando al segundo commit.

Para ello voy a crear una nueva rama `experimental` en el commit actual (segundo commit) del repositorio local así:

```
$ git branch experimental
```
Ahora tengo dos ramas en el segundo commit del repositorio local: `experimental` y `master`
Subo la rama `experimental` al repositorio de github:

```
git push origin experimental
```
Ahora intento eliminar la rama master del repositorio local:
```
$ git branch -d master
error: Cannot delete the branch 'master' which you are currently on.
```
¡Vaya! me dice que no puedo eliminar master si yo estoy en la rama master. Pues nada, me muevo al primer commit, en mi caso:
```
$ git checkout 9c9a74a9592087dff533cf380b145e0088ef7892
```
Y, ahora sí, elimino la rama master del repositorio local:
```
$ git branch -d master
```
Y ahora que estoy en el primer commit, vuelvo a crear la rama master aquí:
```
$ git branch master
```

Y ahora, subo la rama master a github:
```
$ git push origin master
Username for 'https://github.com': xgbuils
Password for 'https://xgbuils@github.com': 
To https://github.com/xgbuils/test-repo
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'https://github.com/xgbuils/test-repo'
hint: Updates were rejected because a pushed branch tip is behind its remote
hint: counterpart. Check out this branch and integrate the remote changes
hint: (e.g. 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

Parece que no me deja, por internet he visto que en este caso siempre se puede forzar el push:
```
$ git push --force origin master
```

Ahora ya tengo tanto en master como en github apuntando al primer commit. Y tengo una rama experimental apuntando al segundo.
