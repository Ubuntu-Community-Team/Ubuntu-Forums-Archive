---
title: "ATI Driver - Cannot Display This Video Mode"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by novus721 on 2007-06-11
Hi all

I have been trying to install the driver for my 9800pro card, following largely on the directions provided at [this website.]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") 

I tried to do the manual installation, but started to get an error whenever I tried to create the symbolic link
```
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
```, it said the file wasn't there, and again whenever I tried to skip it and go to the config command line```
sudo aticonfig --initial
``` - where I found out that my /etc/X11 file does not exist

I tried to go through and do it the "ubuntu way" as shown on the site ```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) # (Okay if it is already installed)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
``` but that did not yield me any success or a X11 file either

so now - grub loads, my kernel loads, and after it is done it breaks to a black screen with the error message (assuming it is from my monitor) "Cannot Display This Video Mode" - and I cannot find any way to get back into my system to be able to do work - please please PLEASE any help would be greatly appreciated!

---

