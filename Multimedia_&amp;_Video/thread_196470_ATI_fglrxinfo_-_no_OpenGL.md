---
title: "ATI fglrxinfo - no OpenGL"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by gorgor_bay on 2006-06-14
I've been experiencing real issues with the ATI video drivers, and I've not found any answer to my problem.

I've got an ATI X700 Mobility, that was running 3D acceleration great before the latest xorg.

```
$ lspci
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
```

But now there is no way to get the 3D acceleration running. I've got :

```
$ fglrxinfo
Error: couldn't find RGB GLX visual!

```

and :

```
$ glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x3d 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

Now if I try to use the trick given in this thread : [http://ubuntuforums.org/showthread.php?t=185033](http://ubuntuforums.org/showthread.php?t=185033) i.e. replacing the libGL.so.1.2 file with the old version, here is what I get :

```
$ fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

```
$ glxinfo
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

Even if I have :

```
$ ls -la /usr/lib/libGL.so*
lrwxrwxrwx 1 root root     12 2006-06-14 14:05 /usr/lib/libGL.so.1 -> libGL.so.1.2
-rw-r--r-- 1 root root 635084 2006-06-14 14:48 /usr/lib/libGL.so.1.2

```

So if anybody has a hint to solve this issue, it will be most welcome !

---

### Post by Patsoe on 2006-06-14
What worked for me - but I must add I don't understand why it made a difference - is adding a line saying "fglrx" at the end of /etc/modules, after which you need to reboot - there's no escaping that, since if the thing makes any difference at all it will be in the order of module-loading.

It's a fairly harmless thing to change, so you might well try it out. Please let us know how it works out - I'd like to know if this is a real fix, or if I'm just hallucinating here ;)

---

### Post by gorgor_bay on 2006-06-14
Thanks for the reply, I've eventually sorted out this bug by reinstalling everything and most important making sure all is really cleanly uninstalled, with :

```
sudo apt-get --reinstall install xorg-driver-fglrx
```

I'll edit the title of the topic
Now I can stick to trying to get xgl/compiz running, which is another huge challenge !

---

