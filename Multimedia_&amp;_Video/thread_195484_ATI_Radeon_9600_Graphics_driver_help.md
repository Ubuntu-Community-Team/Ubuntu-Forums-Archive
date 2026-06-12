---
title: "ATI Radeon 9600 Graphics driver help"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by fatalfury24 on 2006-06-12
I am currently on my hp nc6000 notebook, with a ATI Radeon 9600 mobility edition graphics card. I cant get any graphics drivers to work. I've tried using this guide: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI) and the linux drivers on the ATI website are only for radeon 8500 and above. Does anyone know how to get the drivers working?

---

### Post by caldevil on 2006-06-12
The specific guide you mentioned should work. Can you tell us what is the specific problem you are facing?

---

### Post by dudus on 2006-06-13
There seems to be issues with some ati chips...
Check if you're experimenting bug #47371

[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/47371](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/47371)

---

### Post by elamericano on 2006-06-13
[QUOTE=fatalfury24]the linux drivers on the ATI website are only for radeon 8500 and above.[/QUOTE]
So that would include your Radeon 9600 Mobility...

---

### Post by fatalfury24 on 2006-06-13
The drivers from the ati website did not work. It kept on giving me an error when I tried to generate a distrobution specific package. This is the error from the log:
```
/tmp/fglrx.fuzSJv ~/My Downloads/fglrx-install
Package build failed!
Package build utility output:
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is
~/My Downloads/fglrx-install
[Error] Generate Package - error generating package : Ubuntu/6.06
```
The automatic install didn't work properly, even with running it with gksudo
I keep on getting this problem from both drivers:
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```
Edit: Nevermind, I got it working. I had to use an older driver

---

