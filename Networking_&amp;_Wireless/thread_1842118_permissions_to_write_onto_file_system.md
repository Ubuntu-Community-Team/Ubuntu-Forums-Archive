---
title: "permissions to write onto file system"
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by Brizlitman on 2011-09-10
i cant place my wireless driver(b43) in the firmware folder because i don't have the permissions to do so. Ubuntu 11.04

---

### Post by praseodym on 2011-09-10
Hi,

the driver already is a part of the kernel. You mean you want to install the firmware? Do you have a wired connection? If so:

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

should do the trick. Alternatively download the firmware from here:

[http://media.cdn.ubuntu-de.org/forum/attachments/2480236/Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2480236/Broadcom_Firmware.tar.gz)

and unpack it:

```
sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---

### Post by Brizlitman on 2011-09-10
i don't have access to a wired connection and i can't write onto the ubuntu partition. It says i'm not the owner

---

### Post by haqking on 2011-09-10
> **Brizlitman said:**
> i don't have access to a wired connection and i can't write onto the ubuntu partition. It says i'm not the owner


What location ?

i suspect it is owned by root. Root is the superuser in Linux, in Ubuntu the account is disabled by default but still exists so we can still elevate to its priveleges using Sudo.

root owned locations are usually only read only.

See [RootSudo ]("https://help.ubuntu.com/community/RootSudo")for how to access these areas.

However first of all let us know where you are trying to write to, as doing things with sudo isnt necessarily the best thing just cos you can ;-)

---

### Post by Brizlitman on 2011-09-10
yes it is owned by root. I am trying to write onto the firmware folder in the ubuntu filesystem

---

### Post by wildmanne39 on 2011-09-10
Hi, do you have access to a computer with internet connection? I have the driver and firmware in a zip file and you could put it on a flash drive and I will give you directions to install it.

Also please post the results of this command so we can make sure what card you have.
```
lspci -nn | grep 0280
```
Thank you

---

### Post by Brizlitman on 2011-09-10
i already have the zip file. When i enter the sudo codes, the zip file appears under wireless but the hardware does not work

---

### Post by wildmanne39 on 2011-09-10
Hi, I need the information I asked for please, to be able to help you.

The zip file I have is on my computer so I have exact directions for installing it, I do not have directions for installing a zip file of unknown origin.
Thank you

---

### Post by Brizlitman on 2011-09-10
01:00.0 Network controller
[0280]: Broadcom Corporation
BCM4311 802.11b/g WLAN
[14e4:4311] (rev 02)

---

### Post by wildmanne39 on 2011-09-10
Hi, here are the directions and the zip file I have. We might have to change the commands a little since you have tried to install it already but lets try then we will go from there.

Download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here, then disconnect your wired connection. 

Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Run the commands one at a time.
Thank you

---

