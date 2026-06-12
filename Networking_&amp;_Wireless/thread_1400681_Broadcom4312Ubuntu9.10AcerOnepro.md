---
title: "Broadcom4312\Ubuntu9.10\AcerOnepro"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by matt3206 on 2010-02-07
Ok I installed Ubuntu 9.10 Karmic Kola on to my Acer One pro notebook. I have no wired internet connection so I must update via USB. I have most features working except for the wireless card. I have tried most of what others have posted in this forum. Re-installing the bcm-kernel, which didn't help. I go to Hardware Drivers and I see the STA Broadcom driver and I will tell it to activate but each time it won't activate. I have also tried to download and install a new wl driver the way the readme on the tar file hybrid-portsrc-x86_32-v5.10.91.9.3.tar says to. But everytime I try to insmod wl.ko into the wireless directory I it returns with a permisson denied. 
 
I know a lot of people have issues like mine but all the fixes don't seem to be working. Does anyone have suggestions on what to do at this point?
 
:popcorn:<--mmmm popcorn

---

### Post by bkratz on 2010-02-07
There are  directions in this thread for people with no internet access
Just read the directions carefully!

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by lz1dsb on 2010-02-07
Hi, 
The Broadcom Linux driver worked for me. I've downloaded it from
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
From the problem description I believe that you already know this address. Anyway, the instructions in the Readme are not very detailed but enough. When you executed lsmod command did you append "sudo" in front of the command?

Regards,
Boyan

---

### Post by matt3206 on 2010-02-08
> **lz1dsb said:**
> Hi, 
The Broadcom Linux driver worked for me. I've downloaded it from
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
From the problem description I believe that you already know this address. Anyway, the instructions in the Readme are not very detailed but enough. When you executed lsmod command did you append "sudo" in front of the command?
 
Regards,
Boyan
 
:KSNo actually I did not have sudo in front of the command. It makes alittle bit of sense to me now, with the error message of "permission denied", that sudo commad would require me to authenticate by typing in my passcode correct?
 
I will give it a try and let you know. cheers mate^^

---

### Post by lz1dsb on 2010-02-09
Hi, 
I just saw that I've made a typo in my previous post. I meant "insmod" not "lsmod"... And it could be a bit confusing as both commands are valid one.. Anyway, you should follow the Readme file for the Broadcom driver.

Cheers,
Boyan

---

### Post by matt3206 on 2010-02-09
Ok I tried to insmod into my directory and now I am getting a new error code.
 
```
/lib/modules/2.6.31-14-generich/kernel/net/wireless$ sudo insmod wl.ko
insmod: error inserting 'wl.ko': -1 Unknown symbol in module
```
 
I was able to copy wl.ko into that directory, but I am unable to insmod. eek

---

### Post by matt3206 on 2010-02-09
Thanks for the link bkratz, I think that fixed the problem. The wireless LED light is lit up and I can create wireless networks. I wont know for sure if it worked 100% until I get to a wireless internet connection. Then I can update my comp the way it was designed. Even if this is not the solution thanks everybody for helping this ubuntu noob ^_^

---

