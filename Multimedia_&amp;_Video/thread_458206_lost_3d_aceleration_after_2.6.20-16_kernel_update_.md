---
title: "lost 3d aceleration after 2.6.20-16 kernel update [ati]"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by SpanishFranks on 2007-05-29
Xgl boots with artifacts and running restricted-manager gives the output
```
modinfo: could not find module /lib/modules/2.6.20-16-386/volatile/fglrx.ko
modinfo: could not open /lib/modules/2.6.20-16-386/volatile/fglrx.ko: No such file or directory
modinfo: could not open /lib/modules/2.6.20-16-386/volatile/fglrx.ko: No such file or directory

```
fglrxinfo gives
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

at the moment I'm using 2.6.20-15 to write this which is ok. Although for the 2.6.20-15 kernel I am using the fglrx-kernel-2.6.20-15-386 kernel module and not the restricted-modules. I installed the restriced modules for the 2.6.20-16 kernel but no luck.

Any ideas?

---

### Post by ronocdh on 2007-05-29
Have you tried reinstalling the fglrx driver and then running the following?
```
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

---

### Post by SpanishFranks on 2007-05-29
Yep, tried your suggestion but no luck. I even completely reinstalled xorg and everything that goes along with it. Still have the problem.

---

### Post by SpanishFranks on 2007-05-30
OK, fixed the problem. I uninstalled the fglrx drivers, recompiled them and reinstalled them. I guess I thought I wouldn't need to recompile the drivers. Silly me.

---

### Post by grahams on 2007-05-30
Hi

I'm having the same problem and reinstalling fglrx 8.36.5-1 does not fix it for me. What method did you use to fix this? thanks in advance

---

### Post by SpanishFranks on 2007-05-31
I uninstalled xorg-driver-fglrx and fglrx-kernel-source. Then I did the following to rebuild and install fglrx:

```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
```

Hope it works out. ATI drivers and kernel updates don't seem to mix too well.

---

### Post by grahams on 2007-06-01
Thanks

I think this is what I tired, but I'll try one more time.

How did you  to uninstall fglrx ? "apt-get remove" ?

Was this on 2.6.20-16 ? and which fglrx driver version are you using? I was using 8.36.5-1 and I'm wondering if that doesn't work with 2.6.20-16

---

