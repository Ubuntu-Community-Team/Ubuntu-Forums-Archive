---
title: "webcam issue on asus f9sg"
date: 2008-06-30
forum: Multimedia Software
---

### Post by marconicotera on 2008-06-30
[FONT="Lucida Console"]My embedded webcam isn't reconised by any program (ekyga, skype, amsn ecc.) it switches on but blank screen.[/FONT]
The webcam is a D-MAX (STK-2135)

lsusb
Bus 007 Device 002: ID 0b05:1712 ASUSTek Computer, Inc.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 002: ID 08ff:1600 AuthenTec, Inc.
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 007: ID 0bda:0116 Realtek Semiconductor Corp.
Bus 004 Device 004: ID 174f:8a31
Bus 004 Device 003: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000

erwin@erwin-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 042e (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
erwin@erwin-laptop:~$

Any idea??? Suggestions???

**[FONT="Impact"][FONT="Arial Black"][/FONT][/FONT]**

---

### Post by linuxwizard on 2008-06-30
With Ekiga you may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

---

### Post by marconicotera on 2008-06-30
already tried but it's been of no use.

---

