---
title: "impossible installation any chess game"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by neburzaragoza on 2007-11-09
hi, I have a problem with the chess games:

- I have XBoard but I want something better.
- 3dchess, forget it! I think it's not for me and for anybody
- brutalchess: everybody is telling me it's in the repositories, but 
```

sudo apt-get install brutalchess
```

is not working, and I think i have everything open ¿?

-Pychess: impossible to install, i have a problem
```
PyChess was not able to import pysqlite2 which is a dependency to run the game.

```

i am supposed to be able to install pysqlite [here]("PyChess was not able to import pysqlite2 which is a dependency to run the game.") but i don't have a *configure* doc to install it, and i don't know how to do it

-dreamchess:
```
./congifure
make 
make install
```

but nothing at all, at the end of *./configure* i have this:
```
  Requirement  | Found
------------------------
"SDL_image.h"  |  no
"SDL_opengl.h" |  yes
libSDL         |  yes (-L/usr/lib -lSDL -lpthread)
libSDL_image   |  no
libGL          |  yes (-lGL -lGLU)

Supported:        no
Build:            no

You can now run `make'.
```

to sum up.... too bad, nothing is working yet... i think i'll check the online chess games because installing one it's harder than succeding my career!

thank for any suggestion, idea, answer you all can give  me. I'll appreciate

---

### Post by Lobais on 2007-11-12
The pysqlite package you need in order to run PyChess, is a little ambivious in its name.
I know of the following possible package names:
python2.4-pysqlite2
python-pysqlite2
python-sqlite2
python-sqlite
Try to see if you can apt-get one of them.

---

### Post by neburzaragoza on 2007-11-15
thanks for packages, i've succeded to isntall all of them except one... now it's working correctly.
thanks for your help

---

