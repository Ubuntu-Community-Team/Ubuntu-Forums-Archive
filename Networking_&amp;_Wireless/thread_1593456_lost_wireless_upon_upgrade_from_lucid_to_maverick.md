---
title: "lost wireless upon upgrade from lucid to maverick"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by jethroman125 on 2010-10-11
hi i have a sony vaio VGN-NW150J laptop that was running lucid and had wireless no problem but when i upgraded to maverick i lost all functionality of my intel 5100 agn wireless card. when i run iwconfig this is what i get

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

and on bootup it flashes something about no suitable unicode found i can't get a good look at it maverick boot up too fast. any help will be appreciated.

---

### Post by jethroman125 on 2010-10-11
lspci  shows this 

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller (rev 10)
02:00.0 Network controller: Intel Corporation WiFi Link 5100
0b:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0b:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0b:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

```

lsusb shows this

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b14e Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by mpnordland on 2010-10-12
Hi, I have a similar problem, I have a Dell studio 1747 wireless working great before upgrade, the driver was gone upon reboot after upgrade, I got the driver installed, but now network manager shows no networks to connect to my chipset is bcm43224
Thanks!

---

### Post by guvnr on 2010-10-12
bump :(

The funny thing is, I had wireless, turned it off and it just won't come back on. I've pressed/clicked all the regular stuff.

Am using an HP Pavillion DV2 .. never one of Ubuntu's favorite models I think. 

I just upgraded to 2.6.35-22-generic.

lspci |grep Broadcom
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

Would it help if I install the B43 driver, I wonder? Currently using the STA BCM4312.

Otherwise, Maverick's rather demure so thanks to all and sundry for the new toy.

---

### Post by jethroman125 on 2010-10-23
i fixed it by putting the ucode back in the firmware directory in lib and getting rid of conman

---

### Post by jethroman125 on 2010-11-04
when you update your kernel you have to use the backport driver part of the software updating and sometimes you have to put ucode back in the firmware directory i spent hours trying to figure that out it would be nice if there was a way to do it with out that but i guess it's not feasible or a priority.  you could probably write a script that could automate that but i agree it gets confusing. also if that does not work try manually installing drivers i remember seeing a tutorial on that here somewhere and there are always windows driver wrappers but they are buggy in my experience. if none of that works someone else might think of something or you can Google it to see if someone else with your hardware and situation has a fix.

---

### Post by jmullagh on 2010-11-13
I was able to solve this issue on my mini by simply employing the Synaptic Package Manager as follows:
 In  Synaptic, remove the bcm43 driver which is, in Synaptic,  '**firmware-b43-installer**' the same time you install  'f**irmware-b43-lpphy-installer**'. If you don't the system seems to get  confused and reverts to the original driver driving you up the wall....  again.  Good Luck  !!!  Hope this works....  :smile:

---

