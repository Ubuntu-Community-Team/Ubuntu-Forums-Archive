---
title: "[SOLVED] Strange libGL.so.1 error"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by hammad1337 on 2007-07-26
I am using Ati Radeon 7000 Which works with the default driver supplied by Ubuntu (no fglrx needed)
Recently, I have been gettin the strange error messages when ever I try running any thing 3D:
with ```
glxinfo
``` I get ```
 glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```
with ```
glxgears
``` I get ```
glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```
I dont know whether this is the instance of the same problem:
```
compiz
``` gives ```
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
```

I checked /usr/lib/ but I did not find libGL.so.1 or libGL.so there.
I also tried ```
getlibs -32 libGL.so.1
``` I get ```

Matched library libGL.so.1 to libgl1-mesa-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgl1-mesa-glx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
``` and it does not solve the problem, I continue getting the same error messages.
Please also note that these things used to work before something went wrong.

---

### Post by Cappy on 2007-07-28
Hi, see thread [http://ubuntuforums.org/showthread.php?t=361136](http://ubuntuforums.org/showthread.php?t=361136) since this is a video driver problem.

You may only need to 
```

sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx xserver-xorg-video-ati
```
```

sudo cp /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

```

---

