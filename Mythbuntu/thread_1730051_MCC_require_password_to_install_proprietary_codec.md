---
title: "MCC require password to install proprietary codec"
date: 2011-04-15
forum: Mythbuntu
---

### Post by domv on 2011-04-15
I performed a fresh MythBuntu 10.10 install from ISO downloaded from [http://www.mythbuntu.org/downloads](http://www.mythbuntu.org/downloads).
ISO was ok according MD5checker and I burnt it on CDx52 at x8 speed with K3B (CD verified ok)
 
HW:
µp : I3 2100 with IGP HD2000
mobo: ASUS P8-H67-M pro B3
4Go Ram
64Go SSD SATA 6
Bluray drive SATA 2
no TV card at the moment (debug phase)
LCD on VGA output
 
role backend + frontend
 
During install I had a message about broken pakages but I have no idea of which pakages were broken (which logs to look at ?)
 
The system booted up correctly in MythTV.
I tried to read unencripted DVD but MythTV hangs up => hard reset
The system rebooted, then i exit mythTv to access the ubuntu desktop and then tried with VLC. VLC hangs up also with unencripted DVD and freeze ubuntu => hard reset
 
I tried also to activate proprietary codecs or install KUBUNTU desktop from MCC, but no way as I had a pop up window requesting a password to perform actions (message: System policy prevents systemwide changes to configuration files password ?)
 
Is this normal behaviour of MCC? What is the password requested ? I tried the one I provided during user account creation at install but does not work
May be this is linked to the broken packages ?
 
Any idea ?

---

### Post by domv on 2011-04-23
error during install: /boot partition too small (40MB) which led to uncomplete install
Repartitioning solved the problem

---

