---
title: "ATI Radeon HD 2600 on Ubuntu 12.04 LTS not working"
date: 2014-03-09
forum: Multimedia Software
---

### Post by dennis16 on 2014-03-09
Hello,
i just installed an Ubuntu 12.04 LTS on the Notebook of my Girlfriend. I wondered why the animations are feeling so laggy so i looked at the systeminformation tab insite of the control center. At Graphic there is: unknown (Unbekannt at German). 
I searched at google and found this one: [http://www.ubuntugeek.com/how-to-install-ati-radeon-hd-2600-drivers-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-ati-radeon-hd-2600-drivers-in-ubuntu.html) but this one is outdated because you can download any longer drivers for this graphic card. any idea what i can do?

LSPCI:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV630/M76 [Mobility Radeon HD 2600 XT/2700]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV630 HDMI Audio [Radeon HD 2600 Series]
04:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 01)
06:00.0 Mass storage controller: Silicon Image, Inc. SiI 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
07:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
07:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
08:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)

```

---

### Post by Bashing-om on 2014-03-09
dennis16; Hi !

Here is the deal:
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)


Blame ATI ...

If you require to run the proprietary graphics driver, the recommended option is to install version 12.04.[color=red]1[/color]

Else use the provided open source drivers:

"Graphics: Unknown" is a false report and a known bug. Install the package mesa-utils and the graphics card/driver will be shown. <-https://bugs.launchpad.net/ubuntu/+source/mesa-demos/+bug/914631
&&
[https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)


Just me little bit
[INDENT][INDENT]to try and help
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2014-03-09
Make sure 3D is working. An HD2600 should be able to slice through Unity animations regardless of open-source or proprietary driver.
```
sudo apt-get install mesa-utils
glxinfo
```

---

