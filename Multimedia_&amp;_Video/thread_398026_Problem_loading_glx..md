---
title: "Problem loading glx."
date: 2007-03-31
forum: Multimedia &amp; Video
---

### Post by parkermauney on 2007-03-31
Hi.  I've used Ubuntu for quite a long time, and am on 6.10 Edgy Eft.  I try to run games and programs, such as blender and toribash, and I recieve the message "GLX" missing on display ":0.0".   I followed [https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl") to install drivers for my geforce5200 card.  Everything works fine, but when I select GLX in my session manager, it claims it can't find /usr/bin/startxgl.sh, and boots gnome default.  I know the file is there, and checked it for errors.  What am i doing wrong, do I need to edit my xorg.conf file?  If so please tell me how.:)

---

### Post by Trab on 2007-03-31
using that method is rather outdated.

i suggest you clear your system of all the stuff you did, and try using Envy to install the nVidia driver.

or if its in edgy, fix your system to normal, and ```
sudo apt-get install nvidia-glx
```. but Envy is usually easier.
cheers,
Trab

---

### Post by parkermauney on 2007-03-31
Thank you!

---

