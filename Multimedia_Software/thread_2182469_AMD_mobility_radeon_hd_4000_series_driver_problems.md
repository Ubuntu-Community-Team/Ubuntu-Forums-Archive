---
title: "AMD mobility radeon hd 4000 series driver problems"
date: 2013-10-21
forum: Multimedia Software
---

### Post by brick2 on 2013-10-21
So in essence I can not get my OS to recognise my graphics card.
I am using ubuntu 12.04 LTS 64 bit on a dell laptop.

Here is what I have done thus far:

I tried installing the driver package that was offered on the official site. This really did not help me as it messed up my screens resolution to an extent but things still remind functional. This is the driver I used

[http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux%20x86_64](http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux%20x86_64)





I also tried doing this

sudo apt-get install ia32-libs

wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run)


It did not work!


There are two this that I need here.
First I would like to now how to remove the drivers and return everything to the previous state.
Second if anybody could help me out with my graphics card drivers.

Thank you all for your time.

---

### Post by Yellow Pasque on 2013-10-21
> So in essence I can not get my OS to recognise my graphics card.
I;m guessing you hit this bug: [https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)

> First I would like to now how to remove the drivers and return everything to the previous state.
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx)

> Second if anybody could help me out with my graphics card drivers.
The open-source radeon driver is the best (and in your case, only good) choice and it is installed by default.

---

### Post by brick2 on 2013-10-22
Thank you for your time and info

---

