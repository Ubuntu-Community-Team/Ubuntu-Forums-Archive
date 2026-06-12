---
title: "Xorg high Cpu Utilization - Ubuntu Lucid 10.04 64 Bit"
date: 2010-06-19
forum: Multimedia Software
---

### Post by harmandeep on 2010-06-19
Hi Guys , Linux Newbie here.
Switching from windows and finding a bit difficult to set Graphics  acceleration properly.
 
Mine Config:
Ubuntu Lucid 64 Bit | AMD Athlon II x3 ( ACC Enabled ) | Biostar TA785GE  128 M | 785g chipset | Installed ubuntu using WUBI Feature i.e mine HDD  devices are loop devices. | CPU Scaling set to 100 % | Enabled Desktops Effects ( set to EXTRA ) --- no extra software,themes ... installed ---- all default |
 
Previously, i was having ISSUE with installation of FGLRX 10.4,10.5 and  10.6. Installation would be proper , but when i would restart, i could  strange rectangular cube and nothing else, although that issue was  located and solved earlier today. It was related SidePort Memory with  FGLRX and Xorg Server ... details here

[http://ubuntuforums.org/showthread.php?t=1258371](http://ubuntuforums.org/showthread.php?t=1258371)
[http://ati.cchtml.com/show_bug.cgi?id=16](http://ati.cchtml.com/show_bug.cgi?id=16)

Now, i had switched to UMA - 128 Mb , installed FGLRX 10.6 ( downloaded  from ATI Site ) and i can see Elements properly.
 
 
 
Now ISSUE is related to High CPU
utilzation of Xorg Process , when desktops effects takes place or when a  HD Content movie - H.264 coded .
xvid play normally without any high utilization.
 
I am attaching mine Xorg Log file and Xorg.conf file via PasteBin.
 
IMHO, now Xorg load modules dynamically, do i need to add modules in  Xorg.conf to enable proper hardware acceleration ( which can eliminate  this issue ) ?
 
Wud be editing post in a ShortWhile to add results for default RADEON  driver installed by Ubuntu ....
 
Regards...
 
 
PasteBin Links
[http://pastebin.com/9Z6SBMg3](http://pastebin.com/9Z6SBMg3)
[http://pastebin.com/dWPZ9SxA](http://pastebin.com/dWPZ9SxA)

---

### Post by harmandeep on 2010-06-29
switched back to default open source RADEON ... now Xorg Utilization max. scales to 8% at the most .... GoodBye Crappy FGLRX ... ):P

---

