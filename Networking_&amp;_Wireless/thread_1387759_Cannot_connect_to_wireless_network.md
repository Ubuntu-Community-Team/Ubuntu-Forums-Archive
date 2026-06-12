---
title: "Cannot connect to wireless network"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by Elaina on 2010-01-22
I have just installed Ubuntu. It's a dual-boot, with Windows Vista. Anyway, it's installed and working perfectly... the only problem is that it detects no wireless networks. I got no prompts or anything. When I click the Network Manager I get nothing.

My router is a WRT54G Linksys. It works fine with Vista, I've tried resetting it, but to no avail. Can anyone help? I've tried searching Google but I get nothing of much use.

---

### Post by myth1914 on 2010-01-22
If you run ifconfig, does it show wlan0 and the mac address for the Wifi card?

---

### Post by bkratz on 2010-01-22
> **Elaina said:**
> I have just installed Ubuntu. It's a dual-boot, with Windows Vista. Anyway, it's installed and working perfectly... the only problem is that it detects no wireless networks. I got no prompts or anything. When I click the Network Manager I get nothing.

My router is a WRT54G Linksys. It works fine with Vista, I've tried resetting it, but to no avail. Can anyone help? I've tried searching Google but I get nothing of much use.

Go to the terminal  (Applications>>Accessories>>Terminal) and type in

lspci  (that is LSPCI in lowercase) and copy/paste the output back here so we can see what your wireless card is.

---

### Post by Elaina on 2010-01-22
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

```

---

### Post by leclerc65 on 2010-01-22
Google using 'ubuntu broadcom bcm4322' , I got this:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by bkratz on 2010-01-22
The BCM4321 and 22 are similar to the BCM4311 and 12. Here is an easy page to look at yours is in the first half page.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Elaina on 2010-01-22
Whoo, it worked! You rock, thanks so much for your help!

---

### Post by bkratz on 2010-01-22
> **Elaina said:**
> Whoo, it worked! You rock, thanks so much for your help!

Well now all you have to do is go to the thread tools and mark is [solved] in case it happens to help someone else (easier to search for solved)

---

