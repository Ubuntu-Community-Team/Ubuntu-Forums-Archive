---
title: "crash 6600 GT 8x AGP  on feisty"
date: 2007-08-11
forum: Multimedia &amp; Video
---

### Post by squareline on 2007-08-11
Hello,

i have an 6600gt 8x AGP card, Asus K8U-X (NO Intel integrated card) , AMD 3200+
 and i follow this instructions:

[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

and i try install the nvidia driver this way

sudo apt-get remove nvidia*

and install width nvidia-glx-new driver

sudo apt-get install nvidia-glx-new nvidia-kernel-common linux-restricted-modules-`uname -r` linux-restricted-modules-common

disable the composite

 sudo nvidia-xconfig --no-composite

and i got a black screen!

anyone else have success working 6600gt AGP on feisty ?

here is the confing and log file

---

