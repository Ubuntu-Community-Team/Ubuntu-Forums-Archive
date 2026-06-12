---
title: "Whistle and hiss on speakers"
date: 2015-02-26
forum: Multimedia Software
---

### Post by Cyber72 on 2015-02-26
Having trouble with unwanted whistle and hiss on my speakers. I want to 

1 find which driver I have installed
2 what alternives there are
3 how to uninstall the existing driver
4 how to install an alternaive driver

I have 14.04 32 bit on a Vostro 1000

---

### Post by dino99 on 2015-02-26
you can install htop to check the active processes, or from a terminal:

lspci -vvnn | grep  driver

but first check warnings/errors logged inside /var/log/

---

### Post by mörgæs on 2015-02-26
Changed the thread title. There can be many other reasons for unwanted sounds than drivers. 

[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

---

