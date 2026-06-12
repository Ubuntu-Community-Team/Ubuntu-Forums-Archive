---
title: "Wireless Firmware Missing"
date: 2012-02-26
forum: Networking &amp; Wireless
---

### Post by TizNarnaiz2 on 2012-02-26
> **wildmanne39 said:**
> Hi, it looks like you are missing the firmware we can try to get it working with this driver, and if we can not we will have to switch to the wl driver.

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```run the commands one line at a time.
Thank you
It didn't work for me :( I'm not sure if we restart are computers or not after I did all of this it just said disconnected from network and then it reconnected and it still said firmware missing. please help!

---

### Post by TizNarnaiz2 on 2012-02-26
Well my wireless just seem to say FIRMWARE MISSING and I have gone through tutorials but they all need internet. I am used Wubi to install Ubuntu. Please Help Me

---

### Post by TizNarnaiz2 on 2012-02-26
My wirelees says Wireless Firmware is missing. I installed Ubuntu on wubi. Please Help!

---

### Post by praseodym on 2012-02-26
Looks like a Broadcom device?! Install the firmware for this via cable connection (copy/paste) and terminal (CTRL+ALT+T):

```
wget [http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
```
If its not enough, show the outputs of

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

---

### Post by praseodym on 2012-02-26
Firmware installation via cable:

```
wget [http://media.cdn.ubuntu-de.org/forum...irmware.tar.gz](http://media.cdn.ubuntu-de.org/forum...irmware.tar.gz) 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
```

---

### Post by wildmanne39 on 2012-02-26
Hi, did you make sure there were no errors when you ran each of the commands one line at a time?

If not run them again please and watch for errors, and you do not need to reboot.
Thanks

---

### Post by Iowan on 2012-02-26
Duplicate threads merged

---

### Post by Iowan on 2012-02-26
From the Code of Conduct:
> Do not cross post, or post the same thing in multiple locations.
This is your third mention of the problem. All have been merged into this thread

---

