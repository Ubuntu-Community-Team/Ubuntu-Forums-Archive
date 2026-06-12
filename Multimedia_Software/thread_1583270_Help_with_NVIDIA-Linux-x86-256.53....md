---
title: "Help with NVIDIA-Linux-x86-256.53..."
date: 2010-09-27
forum: Multimedia Software
---

### Post by Grifftology on 2010-09-27
So, yes i'm very new to linux...yes i've tried to research this topic BEFORE posting (but i apparently lack the general skill set to fight my way out of a paper bag)... I got the driver for my Gtx 280 from nvidia and just tried double clicking it...said i had to do it as root or whatever...so i looked that up...ran through a WHOLE bunch of things in terminal...to no avail...i feel really childishly helpless because i cant figure it out BUT thats kinda what attracted me to linux; the learning process. :) i guess if i may be so bold i would LOVE it broken down REAL simple like...i'm talking its time to break out te crayons.... :guitar:

thanks SO much!
Josh

---

### Post by darkstarbyte on 2010-09-27
I am the same way with Linux, and I think I know how to solve this.

Ok go to your package manager type nvidia and a list of nvidia stuff will pop up, and one of the optimized driver packages should be it.

---

### Post by Linuxforall on 2010-09-28
Open up terminal, copy paste

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update
sudo apt-get upgrade
```

This will add Ubutu X ppa and keep your nvidia driver to latest automatically.

---

