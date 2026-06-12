---
title: "Ati 8.42 + mobility radeon x1600"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by Sharaazad on 2007-10-24
Hi,i hope somebody can help me.
I install the new driver using the guide on cchtml wiki.
Here the result:
>  fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
So no 3D accelleration :(

in my  /var/log/Xorg.0.log :
> (EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* * 

Please help :\

---

### Post by xocekim on 2007-10-24
Same problem here on Radeon 9600 :(

---

### Post by F-3582 on 2007-10-24
Did you blacklist the fglrx module as advised?

---

### Post by Sharaazad on 2007-10-24
> **F-3582 said:**
> Did you blacklist the fglrx module as advised?
in my linux-restricted-modules-common i add
DISABLED_MODULES="fglrx"

---

### Post by kaolin on 2007-10-25
I had a similar problem with the Xpress 200M. I tried to look up the answer on google and got down to this: 

If I type in the following:
> sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
and then restart x using ctrl-del-bspace, fglrx will start correctly. After restart mesa comes up again and the link I made was overwritten by a different file. 

I enabled fglrx in the restricted driver manager, maybe this has something to do with the problem? I am merely guessing.

---

### Post by dirtboy on 2007-10-25
Do you also get an error in your log file claiming "Incompatible Kernel Module Version"?

---

### Post by LeBurt on 2007-10-26
I have the same problem with a Radeon 9600. I get:

```
burt@Desktopita-L:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

and also have in Xorg.0.log:
```
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

Are these two problems related?

---

### Post by kaolin on 2007-10-26
> **dirtboy said:**
> Do you also get an error in your log file claiming "Incompatible Kernel Module Version"?

Yes, the same as everyone else:

```
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *

```

---

### Post by andreeh on 2007-10-26
You need to update your module dependencies.

Press CTRL+ALT+F1, log in and type:
```
sudo invoke-rc.d gdm stop
```
```
sudo modprobe -r fglrx
```
```
sudo rm /lib/modules/`uname -r`/volatile/fglrx.ko
```
```
sudo depmod -a
```

To start X/GDM again:
```
sudo invoke-rc.d gdm start
```

---

