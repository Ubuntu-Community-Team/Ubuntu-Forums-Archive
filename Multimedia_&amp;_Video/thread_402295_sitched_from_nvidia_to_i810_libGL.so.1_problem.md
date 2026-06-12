---
title: "sitched from nvidia to i810 libGL.so.1 problem"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by monkman on 2007-04-05
hello. i'm using ubuntu 6.10.

because my "old" fx5600 is making trouble when going 3d, i get visible errors on the sreen which look like screens from an oscilloscope on every edge. they are like dancing. so that i'm not in games i thought i use the onbard intel solution. i removed the nvidia driver using envy removed envy shut the pc down and took the nvidia card out startet the pc and ran ```
sudo dpkg-reconfigure xserver-xorg
```

everything seemed to be fine until i startet google earth:```
error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```
glxinfo and everything else what is dependeing on opengl causes this error.
what have i to do now to make the switch complete?
thanks!

---

### Post by kspn on 2007-11-20
I am interested in this as well. I have the Same Issue

---

