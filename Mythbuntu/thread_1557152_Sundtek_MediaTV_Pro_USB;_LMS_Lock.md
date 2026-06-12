---
title: "Sundtek MediaTV Pro USB; LMS| Lock"
date: 2010-08-20
forum: Mythbuntu
---

### Post by Dreamofabox on 2010-08-20
Hello
Sorry for my English :)

PCI 8400 GS
PCI Asus Xonar D1
Motherboard MSI K8TM-IL
CPU Athlon 64 3000+
1GB RAM
Sata HD 1TB at 1,5 (old VIA chipset)

I using Mythbuntu 10.04.
Used mythbuntu-10.04-desktop-i386.iso.
Testeted with and without updates.

My Dvb-C Tuner is a Sundtek MediaTV Pro  (USB with DVB-C,T,..).
Tuner ist OK.  
DVB-C tuner is working without any Problems with:
Linux (Debian, Ubuntu) yavdr, freevdr;Windows XP, Vista and 7 DVBviwer

Scan was successful. 
Found every channel. 
EIT channel information are displayed and loaded correctly.

But I cant watch TV!
There is short poping up a blank screen.
Signal 99%|BE 0| LMS| Lock 
At the bottom the right EPG .
Setup the right start channel.
Changed channel without sucess.

I've successfully used Mythtv before with a PCI Mantis Tuner card (Cinergy C).
Installed Mythbuntu many times new.

---

### Post by LowSky on 2010-08-20
On the frontend, Utilities/Setup>Setup>TV Settings>Playback, 3rd screen.
change the playback profile to something else. Try each one until video looks clean and crisp without having problems

---

### Post by ian dobson on 2010-08-20
Hi,

Or maybe have a look in the frontend log file (/var/log/mythtv/mythfrontend.log)

Also try recording a program then playing it back (not liveTV).

Regards
Ian Dobson

---

### Post by Dreamofabox on 2010-08-20
**Change video settings don't change anything.**
 **But i installed an older driver for my ****[B]MediaTV Pro.**[/B]
 **[B]sundtek_installer_100506.sh (6085KB)**[/B]
 **[B]I'm getting a livetv picture, but picture with many artifacts. **[/B] 
 **[B]Live TV is stopping.**[/B]
 

 **Sundtek_installer_development.sh (8240KB) driver works fine with yavdr 0.2 and freevdr.**
 **But don't work with Mythbuntu 10.04.**

****
**Take a look at my mythfrontend.log from ****Mythbuntu 10.04 with ****[B]MediaTV Pro.**[/B]

---

