---
title: "WiFi issues after installing Ubuntu 9.10"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by AndyWhite87 on 2010-02-18
Hello!

I have been using a test client of windows 7 32-bit recently and it's coming to the end of it's time. I downloaded Ubuntu 9.10 and installed it. The WiFi still works fine when i boot Windows 7, but not on Ubuntu. I googled it and found it to be drivers. I got my ethernet and connected up this way. My lspci is:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Additional info is that I saw dell wireless 1395 WLAN mini-card in the wireless card properties in windows 7.

Hope you can help!

Andy

---

### Post by chili555 on 2010-02-18
> 0b:00.0 Network controller: Broadcom Corporation [COLOR="Red"]BCM4312[/COLOR] 802.11b/g (rev 01)Please see: [http://wireless.kernel.org/en/users/Drivers/b43#device_firmware_installation](http://wireless.kernel.org/en/users/Drivers/b43#device_firmware_installation)

Especially see: > Ubuntu/Debian

In recent versions of Ubuntu and Debian, installing the b43-fwcutter package will handle everything for you:
```
sudo apt-get install b43-fwcutter
```
You will be asked to automatically fetch and install the firmware into the right location. You will need to be hooked up to the internet by wired ethernet to proceed. Also, open System -> Admin -> Software Sources and be sure that universe, restricted and multiverse are enabled. Select a proper download location if you are not in the USA.

---

### Post by jpl888 on 2010-02-18
Hi Andy,

That chipset isn't compatible with the open source Broadcom driver.

You need to enable the closed Broadcom driver in System -> Administration -> Hardware Drivers.

See attached screen shot.

---

### Post by AndyWhite87 on 2010-02-18
Excellent!

I'm typing this wirelessly!

Thanks

---

### Post by jpl888 on 2010-02-18
You're welcome!

---

