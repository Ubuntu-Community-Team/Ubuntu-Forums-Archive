---
title: "wireless doesn't work"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by Sdados on 2010-01-19
hello

I installed ubuntu 9.10 on a dell vostro 1500 and everything worked fine with the wireless. I didn't have to configure anything and i could connect on the internet. 

Later i installed the same version of ubuntu (64bit) on a dell xps 1330, but this time it looks like the wireless adapter is not recognized at all. If i click on the icon in the top right part of the screen there are not wireless network. 

I am quite a newbie of linux, could someone please tell me what to do to make it work?

thank you very much!

---

### Post by bkratz on 2010-01-19
Well we need to determine what the wireless card is.

Go to the terminal
Applications>>Accessories>>Terminal
and copy/paste the output of
lspci (that is LSPCI in lowercase)
back to this thread.

---

### Post by plorabell on 2010-01-19
Hi,  I am a newbie as well and downloaded ubuntu  last week on to an old pc.  I have the same problem, my wireless network card is not recognised.
At one point I got a message saying my version of ubuntu was not genine. 
Any help, in very simple terms would be appreciated.
 
Colin

---

### Post by bkratz on 2010-01-19
> **plorabell said:**
> Hi,  I am a newbie as well and downloaded ubuntu  last week on to an old pc.  I have the same problem, my wireless network card is not recognised.
At one point I got a message saying my version of ubuntu was not genine. 
Any help, in very simple terms would be appreciated.
 
Colin

That is a new one on me. You probably should start a new thread with the results of the same command.

---

### Post by Sdados on 2010-01-19
ok now the laptop where i have the problem is busy, but in a short time i should be able to tell you what wirelees card it mounts.

thanks for now!!

---

### Post by Sdados on 2010-01-19
it is a dell wireless 1490 dual band WLAN mini-card

hope it helps!

---

### Post by bkratz on 2010-01-19
> **Sdados said:**
> it is a dell wireless 1490 dual band WLAN mini-card

hope it helps!

Not really, Dell usually rebrands a Belkin card with their own number. When you did the lspci did you see anything that said something like BCM43xx? If you can copy/paste the output here more help would be available.

---

### Post by Sdados on 2010-01-19
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c) 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) 
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) 
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02) 
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12) 
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02) 
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01) 



here it is.

it looks there is some BCM4312...

---

### Post by bkratz on 2010-01-19
> **Sdados said:**
> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c) 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) 
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) 
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02) 
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12) 
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02) 
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01) 



here it is.

it looks there is some BCM4312...



OK, this should do it

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Sdados on 2010-01-19
i followed the instructions in the links, but i got an error trying to install the file from the cd. when i mark for installation the b43-fwcutter and then click apply, it says that can't find the karmic_koala cd. Im using the same cd i used to install ubuntu on the computer... ubuntu 9.10 amd64.

So i downloaded from another computer the file and transferred on the not working one. I instlled the package and restarted the laptop. Still not working. 

There is one thing that i don't understand in the instructions. The last point says: repeat steps 1.3 thru 1.4.2... can't figure out what does it means...

sorry im a little bit hard understanding... :D i hope im not bothering you too much!

---

