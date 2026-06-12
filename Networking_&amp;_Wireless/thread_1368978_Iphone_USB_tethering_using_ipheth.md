---
title: "Iphone USB tethering using ipheth"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2009-12-31
Has anyone had any luck with ipheth in karmic?  I've tried to install, but when I run the pair script I get the following error.

```
root@laptop:~/ipheth/ipheth-pair# python2.5 ./ipheth-pair.py 
Traceback (most recent call last):
  File "./ipheth-pair.py", line 10, in <module>
    from libiphone.iPhone import *
ImportError: No module named libiphone.iPhone

```

and if I use python2.6

```
root@laptop:~/ipheth/ipheth-pair# ./ipheth-pair.py 
Traceback (most recent call last):
  File "./ipheth-pair.py", line 10, in <module>
    from libiphone.iPhone import *
  File "/usr/lib/python2.6/dist-packages/libiphone/iPhone.py", line 7, in <module>
    import _iPhone
ImportError: /usr/lib/python2.6/dist-packages/libiphone/_iPhone.so: undefined symbol: _ZTIN5PList10DictionaryE

```

Can anyone help, or point me to a real USB iphone tethering solution that doesn't use proxies?
-J

---

### Post by marano on 2009-12-31
Hello!
Im having the same problem here :(
Anyone can fix it? It looks like its a lib version problem.
Thanks! :)

---

### Post by miatawnt2b on 2010-01-01
I contacted Diego this morning and he promptly emailed me back. He patched some things and it is working now.  Make sure to read the new instructions as there are some new packages to be installed. Grab the new ipheth from git and compile.  Mine is working great!
-J

---

