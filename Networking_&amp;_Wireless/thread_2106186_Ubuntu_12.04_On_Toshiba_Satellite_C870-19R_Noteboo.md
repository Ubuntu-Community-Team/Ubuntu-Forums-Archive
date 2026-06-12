---
title: "Ubuntu 12.04 On Toshiba Satellite C870-19R Notebook With Wireless Connection"
date: 2013-01-18
forum: Networking &amp; Wireless
---

### Post by joch3n on 2013-01-18
Hi There,

i have exactly the same problem like this two people:
[http://ubuntuforums.org/showthread.php?t=2040656](http://ubuntuforums.org/showthread.php?t=2040656)
[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized/165002#165002](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized/165002#165002)

 and i tried to fix it with the following:
(with the file from: [http://askubuntu.com/questions/13963...not-recognized]("http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized"))
cd /home/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514  .201 (work)
sudo su (work?)
make clean
**make: *** No rule to make target `clean'.  Stop.**

make
**make: *** No targets specified and no makefile found.  Stop.**

sudo make install
**make: *** No targets specified and no makefile found.  Stop.**

sudo modprobe rtl8723e
**FATAL: Module rtl8723e not found.**

did i something wrong or is the file defect?

thanks in advance for your help!

cheers, Jo

---

### Post by praseodym on 2013-01-19
Here the file works (without hardware). Did you install all necessary files?
```

sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r`
cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
make
sudo make install
```
without "sudo su".

---

### Post by joch3n on 2013-01-19
the problem is resolved :D

thanks for your help, love ubuntu :)

---

