---
title: "No wireless on HP mini 110"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by jordbrill on 2009-11-03
Hey Everyone,

I am new to Ubuntu, but i just had to put it onto my netbook due to my ridiculous hate towards windows.

I have managed to install the Ubuntu Netbook remix to my HP Mini110. Everything is working perfectly except for the wireless (ethernet is working fine).

Int he top task/menu bar I can see the wireless icon, but it is faded out and does does not find any available networks. Do i have to to activate/install any additional drivers in order to get my wireless working? 

Someone please help, I've been struggling with this for far to long! I am very new to Ubuntu but so far i love it.


Many thanks in advance.

---

### Post by anthony47 on 2009-11-03
I am having the same problem as you. I installed 9.10 on my mini110 and everything works(so far) except for the wireless. I have ubuntu on one partition and XP on the other partition. I wiped my entire drive clean and did a fresh install of XP and 9.10. I have no internet at all in XP and only wired internet in 9.10
Any help appreciated!!
Anthony...

---

### Post by jordbrill on 2009-11-03
yea, same here! its like i have completely locked my wireless card! 

Does your wireless light on the front of your hp mini always stay blue? mine does

---

### Post by anthony47 on 2009-11-04
Yep, the light is always blue. In XP there is no internet at all. In Koala I can use a wire connection to the internet but no wifi, in XP no wire or wireless.

---

### Post by jordbrill on 2009-11-04
ok, glad its not only my computer. I have internet through a wired connection, but like you are experiencing, i also have no wifi.

I have uninstalled xp so i couldn't tel you if it still works there...im assuming not!

---

### Post by bopomofo on 2009-11-04
> **jordbrill said:**
> Hey Everyone,
Do i have to to activate/install any additional drivers in order to get my wireless working?

Try to activate the Broadcom STA driver through Restricted Hardware. Possible solution in [this thread]("http://ubuntuforums.org/showthread.php?t=1308521&highlight=hp+mini+110")

---

### Post by david.m.bailey on 2009-11-04
I am also in the same boat.  My wireless worked fine with Ubuntu 9.04.  When I went to 9.10, I lost the wireless.  I am almost clueless as to working in terminal etc.  If you guys get a fix to this PLEASE let me know.
 
My Win XP wireless is still working, but my Ubuntu is out.

---

### Post by jordbrill on 2009-11-05
The following link solved everything for wireless issues on the hp mini 110

[http://ubuntuforums.org/showthread.php?p=8246179&posted=1#post8246179](http://ubuntuforums.org/showthread.php?p=8246179&posted=1#post8246179)

---

### Post by h1kz0r on 2009-11-26
Unfortunately I tried all the different methods online including this one and still the wireless doesn't work on my hp mini.
The wl is loaded fine, the STA Driver says active and in use and the wireless led is on.
iwlist gives me an error... failed to read scan data, invalid argument when i do scan or scanning.
I see this issue resolved in many places, but this is complete bs imo and all those ppl have it working on 9.04 not 9.10 and the rest of us just downgraded.
this issue is still unresolved, just like all the other "solved" threads about this.

---

### Post by winthant on 2010-12-29
Solved!!

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

> 

Ubuntu Netbook Remix 10.04 Lucid:
Everything works out of the box but the recommended Broadcom STA driver does not appear to activate in live mode. Furthermore, on booting after installation a blank screen appears with a flashing cursor due to this issue. The workaround for this is to press Shift on reboot until the GRUB menu appears and select the recovery mode, followed by the fail safe graphics mode. Once booted into this low resolution mode, a standard restart should allow the computer to boot normally, but it many not boot properly on further attempts which is why it's imperative to immediately plug in an ethernet cable and enter the following two terminal commands to install the STA driver:

sudo apt-get update

sudo apt-get --reinstall install bcmwl-kernel-source

Following this the user should reboot their computer to check that they can boot normally, and that the wireless driver is now active.

There are no problems with the microphone here (though it is advised to turn the input all the way up in the Sound application) and Bluetooth does not break.

* Ubuntu 10.04 Lucid:

110c: Everything, except hibernate, works as soon as the wireless device is installed. Same problems as with the netbook remix: After install, you once need to start recovery mode. Then you need to connect wired internet and install wireless driver.

---

