---
title: "Wireless interface disabled in Ubuntu; fine in Win XP"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by dnels on 2010-08-08
Greetings from southwest VA!

I have an HP mini laptop (Intel Atom, N270, 1.60GhZ, 1Gb RAM, Win XP ver 2002 SP3) that I upgraded to Ubuntu 10.04 netbook version last nite.

I can dual boot, and so far everything under Ubuntu works great - except for the wireless interface.  Rebooting back to WinXP, it works fine.  The 'sudo lshw -C network' command shows "disabled". Ubuntu sees it, its just disabled.  The help file says to make sure its on.  It is - there is no physical switch..

I am VERY new to this, with no programming experience to speak of.  Any help would be appreciated!

Regards...

D

---

### Post by jpl888 on 2010-08-08
Post output of ```
lspci
``` and ```
lsusb
``` and we'll see if we can get to the bottom of this for you.

---

### Post by tcopeland on 2010-08-08
Make sure you have the wireless proprietary driver installed. I find that HP products usually need proprietary drivers. System -> Admin -> Hardware Drivers -> ~Something like Broadcom Wireless Driver. Hope this helps!

---

### Post by jpl888 on 2010-08-08
It should tell you if there's a restricted driver available but I agree with the previous poster also. There is a reasonable chance it's a Broadcom 4312.

---

### Post by dnels on 2010-08-08
Here is the output of the lscpi & lsusb commands:

d@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
d@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 13d3:3249 IMC Networks 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4d2b Primax Electronics, Ltd Wireless Laser Mini Mouse (HID)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 10f1:1a08  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
d@ubuntu:~$ 


As it is a Broadcom interface, I went to the Broadcom site and downloaded the driver for the 4312, but after reading the README.txt, I was a little baffled... Do I have to build my own driver?

thanx guys..

D

---

### Post by jpl888 on 2010-08-09
There is a driver included with Ubuntu that will work with that card.

I have the same card on 2 laptops and it works perfectly with the Broadcom STA driver.

Go into System -> Administration -> Hardware Drivers. After searching for a few seconds you should get a list of available drivers one of which being Broadcom STA wireless driver.

Click on it, then click Activate and reboot. That should be it.

She attached screenshot:-

---

### Post by dnels on 2010-08-09
Thank you for the reply and the information.. I went to the Hardware Drivers folder and opened it, received a message saying "Downloading package indexes failed, please check your network status. Most drivers will not be available".  I hit "close", a 'searching' pop-up comes up, then the hardware Drivers box pops up blank withe the message "No proprietary drivers are in use on this system".

Did I get a bad load when installing Ubuntu? The system seems fine in all other regards, much faster than XP!

Cheers!

Doug

---

### Post by bkratz on 2010-08-09
> **dnels said:**
> Thank you for the reply and the information.. I went to the Hardware Drivers folder and opened it, received a message saying "Downloading package indexes failed, please check your network status. Most drivers will not be available".  I hit "close", a 'searching' pop-up comes up, then the hardware Drivers box pops up blank withe the message "No proprietary drivers are in use on this system".

Did I get a bad load when installing Ubuntu? The system seems fine in all other regards, much faster than XP!

Cheers!

Doug




You do need to have it plugged in to a wired connection for the update to occur or it is available on the live CD too.

---

### Post by dnels on 2010-08-10
I guess I'll need to order the CD.. I don't have an Ethernet adapter plug-in...

I appreciate the assistance!  I be back once I get a CD and let you know how it goes.

regards, 

Doug

---

### Post by jpl888 on 2010-08-10
Thats odd for a machine not to have a network card these days and I have not seen a wireless router without ethernet ports. Is it just the cable you're missing?

---

### Post by dnels on 2010-08-10
Good Tuesday morning!

Amazing what a good nites sleep does for one's eyesite... After seeing your post, I turned on teh lights and turned my laptop over and double checked everything..  There IS an ethernet plug - it had a rubber cover over it that I had not noticed, as the other ports are all exposed.. When I get home this evening, I'll hook it to the modem/router...  I'll update later and let you know.

Thanks for keeping up with me...

Peace

Doug

---

### Post by jpl888 on 2010-08-10
Looks like you're on the home straight!

---

