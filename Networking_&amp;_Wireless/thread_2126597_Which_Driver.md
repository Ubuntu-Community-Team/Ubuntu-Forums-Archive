---
title: "Which Driver"
date: 2013-03-17
forum: Networking &amp; Wireless
---

### Post by Victor99 on 2013-03-17
Hi! I recently purchased a wifi card:
       Apple [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue ! important][FONT=inherit ! important]Airport[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://www.techsupportforum.com/forums/#") Extreme PCI Wireless Card For PowerMac G3 G4 G5 New

Condition: Brand new.

Description:

This 802.11g [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]Wireless [/FONT][/FONT][/COLOR][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]LAN[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.techsupportforum.com/forums/#") PCI Card works with both IEEE 802.11b and IEEE 802.11g products.
CD/Driver included.
Work fo PC MS [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]Windows [/FONT][/FONT][/COLOR][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]98SE[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.techsupportforum.com/forums/#")/Me/2000/XP ista /Windows 7.

This card uses the [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]Broadcom[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://www.techsupportforum.com/forums/#") chipset (the best brand for wireless cards)

Broadcom BCM94318MPG (BCM4318EKFBG) : AirForce One  Single-Chip 802.11g Transceiver with BroadRange  Technology

I'm using XP in a dual boot with Ubuntu 12.04. The [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]driver [/FONT][/FONT][/COLOR][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]CD[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.techsupportforum.com/forums/#") has a plethora of drivers on it.The list:
     4311 folder which has broadcom_43xx_drv410401 and hp4311driver
Since it has hp in this folder, I assume these drivers are for laptop
     4318driver folder which has: 
            bcm43xx64.cat 
            bcm43xx.cat
            bcmwl5.[[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]inf[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://www.techsupportforum.com/forums/#")
            bcmwl5.sys
            bcmwl564.sys  
     5350 folder
            ICS_Dx64.exe
I know this is an [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]Intel [/FONT][/FONT][/COLOR][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]driver[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.techsupportforum.com/forums/#"), and I'm using AMD
     6200 6300 folder
I know these are Intel drivers
        atheros_v7.6.0.260
           atwh.sys
           athwx.sys
           netathw.cat
           netathw.inf
           netathwx.cat
2 more Intel follders and a PCMCIA folder.

     Which drivers do I use for XP and which drivers do I use for  Ubuntu? Any and all resonses will be greatly appreciated. Thanks.

---

### Post by wildmanne39 on 2013-03-17
Hi, in ubuntu just do:CTRL+ALT+T
```
sudo apt-get install linux-firmware-nonfree
```
with a wired connection then reboot.
Copy and paste for accuracy.
You do not need the drivers for windows with ubuntu.

I have not used windows in a long time but the driver should be bcmwl5.sys and bcmwl5.inf I think.
Windows might find the driver for you if you inset the disk and go to device manager and tell it to install driver.

---

