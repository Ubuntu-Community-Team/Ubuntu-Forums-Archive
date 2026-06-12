---
title: "n00b acer 3680 wifi setup"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by zmame on 2010-01-30
Hey all.. Been with Microshaft since 1991 made the plunge yesterday after getting super pissed windows. So i'm totaly brain dead to Linux. 

I would appreciate idiot proof instructions to get drivers and install wireless card on Acer 3680 laptop. I've herd people using **AR5007EG **driver to get it to work according to my google searches. 


would very happy if i could get it working thanks in advance :D



~Nick .S


p.s. have ubuntu 9.10 installed

---

### Post by bkratz on 2010-01-30
> **zmame said:**
> Hey all.. Been with Microshaft since 1991 made the plunge yesterday after getting super pissed windows. So i'm totaly brain dead to Linux. 

I would appreciate idiot proof instructions to get drivers and install wireless card on Acer 3680 laptop. I've herd people using **AR5007EG **driver to get it to work according to my google searches. 


would very happy if i could get it working thanks in advance :D


~Nick .S


p.s. have ubuntu 9.10 installed




Found another thread where the user says that the BCM4311 is the wireless card in his/her Acer 3680. You might want to go to the terminal ( Applications>>Accessories>>Terminal) and type in 

lspci  (that is LSPCI in lowercase) and copy paste the output back here.  This will say what wireless card you have.

---

### Post by zmame on 2010-01-31
lspci  (that is LSPCI in lowercase) and copy paste the output back here.  This will say what wireless card you have.[/QUOTE]

sorry for late reply just got back home here is the results 

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by zmame on 2010-01-31
Managed to get it working 

For anyone having same issues with card mentioned above just open Terminal and enter

sudo apt-get install b43-fwcutter
that will get it working

Thanks,
    Nick S

---

