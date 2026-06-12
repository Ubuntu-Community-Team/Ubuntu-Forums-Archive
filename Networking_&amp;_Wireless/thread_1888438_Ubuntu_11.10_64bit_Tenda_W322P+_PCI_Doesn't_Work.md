---
title: "Ubuntu 11.10 64bit Tenda W322P+ PCI Doesn't Work"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by Piszi on 2011-11-29
[LEFT]Hello,

I read a lot of threads here and googled a lot but i couldn't make my wifi work.
I installed the latest Ralink driver and copyed the latest firmware file to the /lib/firmaware
Blacklisted rt28xx modules
added rt3562 to /etc/modules but still no wifi
etc...

here are some outputs:
[http://dl.dropbox.com/u/47106937/grep.txt](http://dl.dropbox.com/u/47106937/grep.txt)
[http://dl.dropbox.com/u/47106937/iwconfig.txt](http://dl.dropbox.com/u/47106937/iwconfig.txt)
[http://dl.dropbox.com/u/47106937/lshw.txt](http://dl.dropbox.com/u/47106937/lshw.txt)
[http://dl.dropbox.com/u/47106937/lspci.txt](http://dl.dropbox.com/u/47106937/lspci.txt)

Please help me what should I do to get this work.
thx
[/LEFT]

---

### Post by chili555 on 2011-11-29
> I installed the latest Ralink driver Before you did so, did you make the required changes to os/linux/config.mk?

[http://ubuntuforums.org/showpost.php?p=10040247&postcount=1](http://ubuntuforums.org/showpost.php?p=10040247&postcount=1)

If you did not, please do so and recompile:```
cd Desktop/Ralinkfolder or wherever
sudo su
make clean
make
make install
modprobe -rv rt3562sta
modprobe rt3562sta
exit
```

---

### Post by Piszi on 2011-11-29
Yes I modded the conf file but I dind't do modprobe -rv rt3562sta just the modprobe rt3562sta
I will try it recompile it but i don't know why :)
Than install again

Did you added these to the black list?
blacklist rt2800pci
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2800lib

And this to the /etc/modules
rt3562sta.ko
rt3562sta

or not?

---

### Post by chili555 on 2011-11-29
> Did you added these to the black list?
blacklist rt2800pci
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2800libYes.> And this to the /etc/modules
rt3562sta.ko
rt3562sta

or not? Not exactly. ".ko" is implied so you only need, in addition to whatever is there in a default install:```
rt3562sta
```Let us know how it goes.

---

### Post by Piszi on 2011-11-29
Thanks 

It is working!

I think the secret was the modprobe -rv and removing the rt3562sta.ko from modules.

Thank again.

---

### Post by chili555 on 2011-11-29
Excellent! Would you please use thread tools at the top to Mark Solved?

---

