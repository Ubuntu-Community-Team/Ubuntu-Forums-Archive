---
title: "Stuck at very low resolution"
date: 2008-06-30
forum: Multimedia Software
---

### Post by CLomax on 2008-06-30
Hello, finally managed to install the nVidia drivers for my 9600GT...
(In case someone comes here wanting to know how, sudo apt-get install envyng-gtk did the trick for me.)
... now that I have, the fan is finally silent but I've run into a new but small problem; the resolution is stuck at 640x480.

> ~$ xrandr -q 
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 (normal left inverted right) 0mm x 0mm
   640x480        50.0*    51.0     52.0     53.0  
   512x384        54.0     55.0  
   400x300        56.0  
   320x240        57.0     58.0 

I am trying to step it up to 1440x900.

> ~$ lspci | grep VGA 
02:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)


Thank you for your help.

---

### Post by xc3RnbFO8P on 2008-06-30
Did you try:
> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by CLomax on 2008-06-30
> **Ringi said:**
> Did you try:

Yup, no luck.

---

### Post by xc3RnbFO8P on 2008-06-30
Read this (if you haven't):
[http://ge.ubuntuforums.com/showthread.php?t=798881]("http://ge.ubuntuforums.com/showthread.php?t=798881")

---

