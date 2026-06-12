---
title: "Dell Inspiron 6000 - Wireless Problem"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by jdiehl on 2009-06-26
Hello,

I am new to Ubuntu, but so far am loving it!  I have my Dell desktop set and ready to go after getting a new wireless card.  My problem is with my Dell Inspiron 6000 with a Dell Wireless 1370 WLAN Mini PCI Card.  I think the issue is with it not being on.  I have seen a number of threads mentioning turning it on.  I have hit FN F2 and tried to adjust it during the BIOS by hitting F2 and I went in to the Dell setup before booting to Ubuntu and adjusted to be sure it was on and it was.  I have read countless archives to no avail.  I do not have the WIFI indicator on when I am in Ubuntu, but works fine when I am in Windows XP.  I have been able to get online thorough a LAN line, but nothing with wireless.  

Anyone have any idea of what I need to do?

---

### Post by Ayuthia on 2009-06-27
Have you checked System->Administration->Hardware Drivers to see if there are any options there for your wireless card?  If so, can you go into the Terminal and post the results of lspci -nn?

---

### Post by jdiehl on 2009-06-27
I did and it lists "No proprietary drivers are in use on this system."  When I run lspci it responds with:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by Ayuthia on 2009-06-27
You can try the following if you have a working internet connection:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```
This will install the firmware needed to help make your wireless card work.

Hope that helps.

---

### Post by superprash2003 on 2009-06-27
also take alook at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by jdiehl on 2009-06-27
AWESOME!  That worked!  Thank you so much for your help with this!

---

### Post by Ayuthia on 2009-06-27
Out of curiosity, which one worked?  It appears that the 4318 card is not being recognized by Hardware Drivers, but I have not been able to verify if it is working with b43-fwcutter or ndiswrapper.

---

### Post by jdiehl on 2009-06-29
I believe it was the b43-fwcutterthat helped.  Everything has been working great!

---

### Post by nightmicu on 2009-08-26
Sorry, problem solved after I posted

---

