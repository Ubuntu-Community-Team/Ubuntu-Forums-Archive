---
title: "Ubuntu and Belkin F7D1101 v1 USB Wireless N help!"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by xaxtree on 2010-05-24
Well I've only seen 2 topics about this certain USB Wireless device, but I just need some professional help or good help on how I can attempt to get this card to work, I bought it today and I'm a linux newbie, can someone please help?  I can't scan for network, nor am I sure if it will work.

---

### Post by xaxtree on 2010-05-24
Please I would love some help, I know there isn't much info, but is there anyway I can extract the drivers .exe and get the .inf file for ndiswrapper?

---

### Post by squeezy on 2010-05-24
I am in a similar boat. I have dabbled with Linux plenty in the past, and decided to dive back in with Ubuntu 10.04. To my surprise, my Linksys WMP54G was having driver issues. No matter what I did in ndiswrapper something kept conflicting and my connection would stay connected for a minute at a time. Then I popped in another card, Edimax EW-7128g. Wouldn't it be my luck, both cards use the EXACT same chipset, so same results with that card. So today I went out and bought this Belkin Basic USB wireless adapter. I popped it in, open ndiswrapper, installed the INF file, rebooted, nothing. It has the driver listed in the -l command, though I do not know what I am doing wrong. Any help would be greatly appreciated!

---

### Post by xaxtree on 2010-05-24
did you check for any errors in dmesg?

---

### Post by squeezy on 2010-05-24
> **xaxtree said:**
> Well I've only seen 2 topics about this certain USB Wireless device, but I just need some professional help or good help on how I can attempt to get this card to work, I bought it today and I'm a linux newbie, can someone please help?  I can't scan for network, nor am I sure if it will work.

You should find the INF files located on the CD that came with the USB card, I found them under InstallationFiles / Driver / Win7x64 are the drivers I'm trying with.

> **xaxtree said:**
> did you check for any errors in dmesg?

I will reboot and check, and report back, thanks.

---

### Post by xaxtree on 2010-05-24
> **squeezy said:**
> You should find the INF files located on the CD that came with the USB card, I found them under InstallationFiles / Driver / Win7x64 are the drivers I'm trying with.



I will reboot and check, and report back, thanks.

alright ill try that thanks

---

### Post by squeezy on 2010-05-24
I am looking at a lot and I'm not sure what alot of it means, but I did see these ndiswrapper related bits

a lot of "ndiswrapper import:242 unknown symbol

ndiswrapper (load sys files 206) couldnt prepare driver net8192su

ndiswrapper (load wrap driver:108) couldnt load driver net8192su - check system log for messages from 'loadndisdriver'

---

### Post by xaxtree on 2010-05-24
here is something interesting i looked through the installation files and noticed that one of the sys files is the name of the chipset which is rtl8192su or better known as Realtek :)?

---

### Post by squeezy on 2010-05-24
If you have any progress getting your card to work please let me know! ndiswrapper says the driver is installed the device ID, it just wont turn on!

---

### Post by xaxtree on 2010-05-24
i will indeed keep you updated right now i used the ndiswrapper GUI installer and selected the winxp driver and it seemed to have worked, i selected my network and its scanning but i don't think it is connecting

---

### Post by squeezy on 2010-05-24
I am not using the GUI version, so I'm doing all this kind of blind. In the terminal when I type ndiswrapper -l I get these messages before it shows the driver I have installed

All config files need .conf - modprobe.d/ndiswrapper & blacklist

I am going back and installing the XP64 driver, in the meantime what do those messages mean and how should I respond to them?

---

### Post by xaxtree on 2010-05-24
the best answer i could honestly give you is to try to look up each one specifically and see what you find out :\

---

### Post by xaxtree on 2010-05-24
bump

---

### Post by xaxtree on 2010-05-24
well what ever i did my ubuntu wont boot anymore, i tried installing the drivers from the actual chipset of the the belkin usb device itself, from the realtek website i grabbed its linux drivers installed, and rebooted, something might have messed up :\

---

### Post by Anonymous Citizen on 2010-05-24
> **xaxtree said:**
> well what ever i did my ubuntu wont boot anymore, i tried installing the drivers from the actual chipset of the the belkin usb device itself, from the realtek website i grabbed its linux drivers installed, and rebooted, something might have messed up :\

I had this same problem, my thread [here]("http://ubuntuforums.org/showthread.php?t=1491797"). I had to follow [these instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Compiling%20the%20latest%20version%20of%20ndiswrapper") from recovery mode. I basically just removed the ndiswrapper packages in recovery mode terminal without networking. My ubuntu installation would just hang at the log in screen, but it seems removing ndiswrapper solved the problem.

---

### Post by xaxtree on 2010-05-24
> **Anonymous Citizen said:**
> I had this same problem, my thread [here]("http://ubuntuforums.org/showthread.php?t=1491797"). I had to follow [these instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Compiling%20the%20latest%20version%20of%20ndiswrapper") from recovery mode. I basically just removed the ndiswrapper packages in recovery mode terminal without networking. My ubuntu installation would just hang at the log in screen, but it seems removing ndiswrapper solved the problem.

thank you for this i'll try to boot into recovery thank you

---

### Post by xaxtree on 2010-05-25
still no luck :(

---

