---
title: "Error installing SOAR 7.3 in ubuntu 10.10"
date: 2010-09-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Lewke on 2010-09-26
Ran into what seems to be a small error with SOAR, this is the make file:

```

#!/bin/csh
pushd kernel
./configure --with-tcl-lib-dir=/usr/lib --with-tk-lib-dir=/usr/lib
make
popd
pushd interface
./configure --prefix=../.. --with-tcl-lib-dir=/usr/lib  --with-tcl-doc-dir=/usr/tcl --with-tk-lib-dir=/usr/lib   --disable-static-soar --disable-static-soartk --enable-dynamic-soar  --with-kernel=../kernel
make
cp  libsoar7.3* ../library
popd

```but the first line keeps giving error as the directory doesn´t  exist on the system, not really sure what it should be changed to  either. I edited the rest of the things in the file to what they need to  be.

error:
```

luke@luke-laptop:~/Downloads/soar-7.3$ ./make-soar
bash: ./make-soar: /bin/csh: bad interpreter: No such file or directory


```

---

### Post by Lewke on 2010-09-26
Nevermind, just did this:

```

sudo apt-get install csh

```

and that fixed it.

---

