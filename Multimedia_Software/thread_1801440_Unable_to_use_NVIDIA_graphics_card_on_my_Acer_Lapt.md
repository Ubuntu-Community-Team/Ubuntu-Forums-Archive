---
title: "Unable to use NVIDIA graphics card on my Acer Laptop."
date: 2011-07-10
forum: Multimedia Software
---

### Post by ashish14 on 2011-07-10
Hi,

Am using ACER Aspire 5745G which has switchable graphics.

I recently installed Ubuntu 11.04 - the Natty Narwhal i updated everything after the installation. 

Now the issue is that when i go to NVIDIA X Server Settings, its giving me an error message:-

" You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

[ATTACH]197172[/ATTACH]

also tried searching in the forum but it was so confusing, as am Newbie i have no idea where to start. 

Any help will be really appreciated. 

Summary: NVIDIA Graphic Card GeForce GT330M not working.

Thanks !!!

---

### Post by zero2xiii on 2011-07-10
Hay, try this:

pop open a terminal (Applicationss, accesories, terminal) and run:

```
sudo nvidia-xconfig
```

that should reconfigure your xorg file.. Also, make sure you are using nvidia drivers version 270.41.06.

Hope it helps ;)

---

### Post by SeijiSensei on 2011-07-11
You probably have an "Optimus" video adapter which has well-known problems in Linux.  Do a search here for 'optimus' to learn more.

---

