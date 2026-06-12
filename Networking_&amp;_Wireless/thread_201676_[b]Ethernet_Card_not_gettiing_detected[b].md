---
title: "[b]Ethernet Card not gettiing detected[/b]"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by infin?ty on 2006-06-22
Hi

My ehernet card is not getting detected by ubuntu. 
RTL8139D PCI Fast Ethernet Adapter (Realtek)

i tried pppoeconf, but that said card not detected, try modconf. But bash says modconf command doesnt exist.

I had got drivers for the card fo a linux OS, on a floppy it caontained a C src file , a makefile and some other files, but wen i typed make it gave many errors in C src file itself which i am not able to correct. So wat should i do because its proving out to be a big pain, as i access internet thru windows and to make anycanges have to reboot comp and go to ubuntu.

---

### Post by linuchsan on 2006-06-22
Your card is supported. It is the 8139too module.
Try lsmod if it is there.

---

### Post by infin?ty on 2006-06-22
Please can u explain a bit more... and if the card is supported then y is it not getting detected. And y is modconf not working.

---

### Post by infin?ty on 2006-06-23
Comeon ppl, Plz help me i have no clue as to y this is happening. Please help or gimme some outside links.

---

### Post by Syzzer on 2006-06-23
What does

lsmod | grep 9139

tell you?

---

### Post by infin?ty on 2006-06-23
Here are the results of some commands i tried

**modprobe 8139too**

WARNING: Error installing mii (/lib/modules/2.6.12-9-386/kernel/drivers/net/mii.ko):operation not permitted

WARNING: Error installing 8139too (/lib/modules/2.6.12-9-386/kernel/drivers/net/8139too.ko):operation not permitted

**lspci**

0000:01:0a.0 Ehternet controller: unknown device 1904:8139 (rev 01)

**dmesg | grep eth**
no o/p

** lsmod | grep 8139**
no o/p

** dmesg | tail **

lists some bluetooth stuff, nothing conected to ethernet

** sudo insmod /lib/modules/2.6.12-9-386/kernel/drivers/net/8139too.ko** 

error inserting (the above path): -1 unknown symbol in module

I hope this will help to figure out wat problem i am having.

---

### Post by nitinrao on 2007-10-23
am havin the same prob mate , same card ....  my frnd gave me "modconf", which i ran, n found drivers 4 the very same card.... after installing it, i get the same error tat " no network card found"... ive bridged my modem in windows, do i have 2 switch back 2 pppoe???

---

