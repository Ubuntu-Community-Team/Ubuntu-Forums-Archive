---
title: "Won't log-on to Secured Wireless"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by ThinkBaz on 2009-06-23
Why would wireless work with XP and not Ubuntu (8.04)?  I just moved and haven't set-up a wired connection yet, so need to rely on Wi-Fi.  The connection is secured, and Ubuntu simply won't log-on, even when next to the antennae.  However, it will log-on to a stray unsecured signal.  I'd like some troubleshooting advice please. Thanks.  Forgive me if I haven't provided sufficient information.  My mind is mush for using Windows the last month.

---

### Post by Metaljaz on 2009-06-23
When you left click on the network connections icon on the top right corner of the screen do you see the connection that you wish to connect to?
If you see it what happens when you click on it? Are you given a box to enter the key/password?

---

### Post by lavinog on 2009-06-23
It would be helpful to know what kind of wireless device you are using.
try posting the output of lspci
in the terminal:
```
lspci>~/pci.txt
```
This will save it to a text file in your home folder

---

### Post by ThinkBaz on 2009-06-23
Yea, I'm provided the box.  I enter the pass-key, and about thirty seconds later, I'm prompted for it (pass-key) again.

lspci:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
13:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
14:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
14:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
14:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)

---

### Post by Metaljaz on 2009-06-24
If I am not mistaken you have a choice of several different types of secured wireless. Like a drop down menu with the choices, something like WEP, WEP Shared, WPA, etc. Make sure you have the right choice selected for your secured wireless set-up. Make sure you are using the password for your wireless and not your Ubuntu login password.

---

