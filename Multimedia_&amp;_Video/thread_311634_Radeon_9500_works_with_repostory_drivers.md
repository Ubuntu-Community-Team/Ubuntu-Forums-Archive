---
title: "Radeon 9500 works with repostory drivers"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by mulperi on 2006-12-03
After several hours of trying the ATI drivers I finally gave up.
HW acceleration works well also with the drivers in repostory.

What you need to do is follow this guide:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

In my case:

Use packet manager and:
Uninstall (complete removal) any fglrx- drivers (from your trial'n'error with ati propietary drivers)

Install linux-restricted-modules-common (version 2.6.17.6-1)

Install linux-restricted-modules-general (not sure if needed)

Install xorg-driver-fglrx (version 7.1.0-8.28.8+2.6.17.6-1)

Then in terminal:
Make sure fglrx is not disabled: 
```
sudo gedit /etc/default/linux-restricted-modules-common
```
..DISABLED should be empty, or at least not contain fglrx

```
sudo depmod -a
```
to start the drivers

Check that fglrx starts by 
```
sudo modprobe fglrx
```
and 
```
lsmod | grep fglrx

```
that should show fglrx running

prepare /etc/X11/xorg.conf file using
```
sudo aticonfig --initial 
```
```
sudo aticonfig --overlay-type=Xv
```

Reboot

Verify result with 
```
fglrxinfo 
``` (no more MESA!)

Hope this helped.

---

### Post by RudolfMDLT on 2006-12-03
Hi! 

Looks like a pretty good guide! Did you do this under Dapper or Edgy?

---

### Post by mulperi on 2006-12-04
I use Edgy.

---

### Post by accel on 2006-12-04
Problably this will also work for the Radeon 9550. Tonight I will find out.
I will let you know the result ;-)

---

### Post by accel on 2006-12-05
For the Radeon 9550 this method doesn't work for me.
More luck I had with Method 2 of this thread: [http://ubuntuforums.org/showthread.php?t=195845](http://ubuntuforums.org/showthread.php?t=195845)

I now get 3D accelleration with the latest 8.31.5 ATI "fglrx"-driver :D :
> $ glxinfo | grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON 9550 Generic

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.6174 (8.31.5)

BTW: I use Edgy

---

