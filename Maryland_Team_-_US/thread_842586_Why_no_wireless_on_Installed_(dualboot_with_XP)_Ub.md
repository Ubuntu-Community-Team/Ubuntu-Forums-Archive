---
title: "Why no wireless on Installed (dualboot with XP) Ubuntu 7.10."
date: 2008-06-27
forum: Maryland Team - US
---

### Post by Joe Moore on 2008-06-27
I hope someone smarter then me will read this.  I've never used linux before.  All excited to finally get a look at Ubuntu, I incerted the ver 7.10 cd in my new Dell 1525 laptop and rebooted.  Everything seemed to go smoothly with my dual boot install, but when I rebooted, Ubuntu had no internet access through my wireless. Under System >> Administration >> Network, there's not even a wireless option listed.  I rebooted in XP and the wireless worked fine.  I looked up the card and drivers under XP (below) but, I have to admit being a novice, and really don't know what to do with that information or what to do next.  I hate to give up on linux/Ubuntu.  Your assistance in this matter would be appreciated.

Technicals:
Dell Inspiron 1525
Inter Celeron CPU 550@2Ghz
1.99 Gbytes RAM

Dell Wireless 1395 WLAN mini-card revision 2.10
IRQ 17
Memory Range FE7FC000 - FE7FFFFF
Driver: C:\windows\system32\drivers\BCMWL5.sys
Broadband corp.
File ver 4.170.25.12
Driver chipset BCM4315/BCM22062000
MAC address 00:1F:E1:2B:31:87
Location US
Channel 1,2,3,4,5,6,7,8,9,10,11
   and that's all I know about that.

---

### Post by Kevbert on 2008-06-27
Please see this [[COLOR="Red"]thread[/COLOR]]("http://sudan.ubuntuforums.com/showthread.php?t=734221").

---

### Post by stats on 2008-07-10
the driver is in the repo now
if you dint install  ndiswrapper then skip steps 2,3,4 
1.Update & upgrade using update-manager/synaptic/adept etc
2.
```

sudo apt-get remove ndisgtk ndiswrapper-common ndiswrapper-utils-1.9

```
3. Remove the ndiswrapper line from /etc/modules
4. Disable wireless from the network manager applet and then

```
sudo modprobe -r ndiswrapper
```

If it cribs about module being in use, it means you have not disabled wireless
5. Restart, if there were any kernel upgrades
6. System->Administration->Hardware Drivers
I see a wl driver here. Make sure it says enabled and is in use.

worked for me with dell 1395 on inspiron 1525

---

