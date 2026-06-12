---
title: "Nvidia enabled, 3D acceleration lost after sudo dpkg-reconfigure xserver-xorg"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by JulianLx on 2007-06-15
Hi All,

I just updated to 7.04. After the update my resoltion was downgradede to 800X640. I made ```
sudo dpkg-reconfigure xserver-xorg
```
After getting back my 1280X1024 resolution, my 3D acceleration was gone and I´m getting nasty outputs as
```
$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```
What may I check or do?

Thanks,

Julian

---

### Post by JulianLx on 2007-06-16
Solved with this

[http://ubuntuforums.org/showthread.php?t=434038&highlight=Xlib%3A+extension+GLX%26quot%3B+missing+on+display+%26quot%3B%3A0.0](http://ubuntuforums.org/showthread.php?t=434038&highlight=Xlib%3A+extension+GLX%26quot%3B+missing+on+display+%26quot%3B%3A0.0).

---

