---
title: "Wireless Problems"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by tlbrow23 on 2010-05-05
I'm having some troubles trying to get my wireless to work on ubuntu. My wireless card is an Intell Wireless 1000 GNB however I cannot figure out how to install my drivers and cannot get ubunut to recoginze the drivers. Any suggestions?

---

### Post by mcoleman44 on 2010-05-05
Have you checked hardware drivers? 
If nothing is listed open a terminal and type
```
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```
Now check hardware drivers again

You may have to use ndiswrapper

---

