---
title: "ubuntu 11.04 Dell XPS M1330 wireless (N) stops randomly."
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by pi3ch on 2011-05-09
I am using Ubuntu **11.04** on **DELL XPS M1330**. My home router is **Billion BiPAC 7800N** that support **wireless N** technology. My network connection **stops randomly** as I rebooted the laptop after installation. it works like for 5 min then freezes for some seconds and works again.

I check the Internet connection on router and there is not disconnect issue with that. The problem also happens with LAN connections (e.g. connecting to home ftp server).

Thank for any comments/suggestion on this issue :confused:

Output of **lspci**: 
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
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
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```P.S.: my wireless card worked flawlessly with Ubuntu 10.04.

---

### Post by pi3ch on 2011-05-10
no comments? :(

---

### Post by pi3ch on 2011-05-17
I tried to update my drive (Iwlagn) to newer one using [compat-wireless-2.6]("http://wireless.kernel.org/download/compat-wireless-2.6/") (./scripts/driver-select iwlagn) after following procedure and reboot, guess what? I even lost my wireless connection! Ubuntu even did not detect my wireless card! ... boy it is so bad! Never install this drive! it just mess up everything! It took me 1 day to get my old drive to work.
I tried to restore but doesnt work. so what I did at the end:
1. sudo make uninstall the compat wireless package
2. reinstall linux-headers and linux-image
3. reboot

and I got my wireless working. but anyway still it freezes sometimes on Wireless N. (and for some reason my bluetooth is off after this reinstallation!)

anyway I still have the wireless issue

---

### Post by muxical on 2011-08-13
I've the exact same system (with a Linksys router). However, my system freezes randomly.
As per this post[1], the culprit are 802.11n drivers. May be that's case with you as well.

I'm going to try to disable it and see if it solves my problem.

[1]. [http://www.megalinux.net/solution-dell-xps-m1530-ubuntu-810-system-freeze-issue/](http://www.megalinux.net/solution-dell-xps-m1530-ubuntu-810-system-freeze-issue/)

---

