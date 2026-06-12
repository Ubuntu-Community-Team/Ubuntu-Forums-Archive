---
title: "Installing ATI driver"
date: 2006-11-24
forum: Multimedia &amp; Video
---

### Post by DreamerHxC on 2006-11-24
Hello:
Im trying to install ATI drive like explained at [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) but when I do ```
glxinfo | grep vendor
``` I get ```
Error: unable to open display (null)
```
Sometimes I can boot up in graphic mode, then I try to do glxinfo in graphic mode and I get ```
02. Xlib:  extension "GLX" missing on display ":0.0".
03. Xlib:  extension "GLX" missing on display ":0.0".
04. Xlib:  extension "GLX" missing on display ":0.0".
05. Error: couldn't find RGB GLX visual
06. Xlib:  extension "GLX" missing on display ":0.0".
07. Xlib:  extension "GLX" missing on display ":0.0".
08. Xlib:  extension "GLX" missing on display ":0.0".
09. Xlib:  extension "GLX" missing on display ":0.0".

``` while in text mode I get the error written up.
Any idea please?

---

### Post by ReaderRat on 2006-11-24
```
glxinfo |grep vendor
```
should be:
```
glxinfo | grep vendor
```

---

### Post by DreamerHxC on 2006-11-24
yes, sorry, I made a mistake posting, but I do it correctly in my system.
As what posted above didn't work, I tried like in [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) but it shows  ```
$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```
But I realized:
```
#

Make sure that the resctricted-modules package installed correspond to the kernel your are running and that you can load the fglrx driver, either by issuing the command "sudo modprobe fglrx" or by verifying that the module appears in the list of loaded modules, by issuing the command "lsmod";


```

sudo modprobe fglrx says:
```
 FATAL: Error running install command for fglrx
```
and I can't see fglrx with lsmod

---

