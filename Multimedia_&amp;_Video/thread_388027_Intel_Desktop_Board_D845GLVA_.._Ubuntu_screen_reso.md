---
title: "Intel Desktop Board D845GLVA .. Ubuntu screen resolution"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by nasirazizawan on 2007-03-19
I have installed ubuntu 6.10 on intel desktop board D845GLVA , screen resolution is set to 800x600. and its so annoying. please help me to set it 1024x786 at least (;0)

i have tried resoluton95 and lot of other, many times my system crashes... and i have to sometime reinstall and sometime recover it..

please help me ASAP.


thanks in advance.

---

### Post by teaker1s on 2007-03-19
```
 lspci | grep VGA
``` find out the exact graphics you have

commonly with intel graphics  you need
```
sudo apt-get install 915resolution
```

also 
```
sudo dpkg-reconfigure xserver-xorg
``` you can configure resolutions that will then be usable in gnome/kde etc

---

