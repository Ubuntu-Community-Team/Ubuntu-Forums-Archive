---
title: "cannot make; make install lsyncd-2.0.4"
date: 2011-04-05
forum: Networking &amp; Wireless
---

### Post by slashwannabe94 on 2011-04-05
Hey all, i am trying to make; make install lsyncd-2.0.4 and keep getting this error can anyone help me? 

make  all-am
make[1]: Entering directory `/home/sherron/lsyncd-2.0.4'
luac lsyncd.lua
luac: <name> expected;
  last token read: `function' at line 79 in file `lsyncd.lua'
make[1]: *** [luac.out] Error 1
make[1]: Leaving directory `/home/sherron/lsyncd-2.0.4'
make: *** [all] Error 2
luac lsyncd.lua
luac: <name> expected;
  last token read: `function' at line 79 in file `lsyncd.lua'
make: *** [luac.out] Error 1
sherron@sherron-laptop:~/lsyncd-2.0.4$ nano lsyncd.lua
sherron@sherron-laptop:~/lsyncd-2.0.4$ make; make install
make  all-am
make[1]: Entering directory `/home/sherron/lsyncd-2.0.4'
luac lsyncd.lua
luac: <name> expected;
  last token read: `function' at line 79 in file `lsyncd.lua'
make[1]: *** [luac.out] Error 1
make[1]: Leaving directory `/home/sherron/lsyncd-2.0.4'
make: *** [all] Error 2
luac lsyncd.lua
luac: <name> expected;
  last token read: `function' at line 79 in file `lsyncd.lua'
make: *** [luac.out] Error 1
----------------------------------------------------------------------

If anyone knows how to fix this and allow me to make; make install the program i would be very thankful. 

Thanks, 

SlashWannabe94

---

### Post by slashwannabe94 on 2011-04-05
Definitely something to do with Lua.

---

### Post by lorello on 2011-08-18
Post the output of 
```

luac -v

``` 

Mine is

```
lorello@motoko:/usr/local/src/lsyncd-2.0.4$ luac -v
Lua 5.1.4  Copyright (C) 1994-2008 Lua.org, PUC-Rio

```

if it's something like 5.0.?, you must probably upgrade your lua interpreter.

On my lucid servers, I've compiled lsyncd after installing 5.1 lua packages

```

sudo aptitude install lua5.1 liblua5.1-0-dev

```

---

### Post by slashwannabe94 on 2011-08-18
It's alright man. I fixed this months ago with the same thing you have told me to do. Thanks for the input though. I forgot to mark this thread as solved. :P 

thanks,
SlashWannabe94

---

