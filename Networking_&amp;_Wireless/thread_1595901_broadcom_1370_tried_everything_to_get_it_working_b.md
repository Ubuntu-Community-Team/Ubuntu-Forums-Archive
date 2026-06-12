---
title: "broadcom 1370 tried everything to get it working but still no cigar:( any help?"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by breadbin on 2010-10-13
i know there is alot of posts about this driver but i have read and read and tried everything that was said but no cigar. specs

i have a dell inspiron with a broadcom 1370 wifi card and ubuntu 10.10 installed. as it is the wifi icon has a red ! and t says missing firmware.

here are outputs of various things hoping it might help

[B][SIZE="1"]sudo lshw -class network
*-network:0
description: Ethernet interface
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 02
serial: 00:14:22:91:0e:23
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
resources: irq:18 memory:dfbfc000-dfbfdfff
*-network:1
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 3
bus info: pci@0000:02:03.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64
resources: irq:17 memory:dfbfe000-dfbfffff
*-network DISABLED
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:14:a5:56:14:d0
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg


lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


modprobe -l | grep b43
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko

Contents of /etc/modprobe.d/blacklist
blacklist bcm43xx
blacklist bcm4318
blacklist BCM4318
blacklist b43
blacklist b43legacy


[/SIZE][/B]i added the lines to the blacklist file and then installed ndiswrapper and the windows driver and ndiswrapper worked fine and didn't give me any errors but i see the kernel drivers are still loaded and still the red ! is there. please can soemone help cos its crucial really, i wont be using linux if i cant get it working and i really want to. thanks in advance

oh and if anyone needs to see any other outputs of commands i'll get them no worries:)

---

### Post by chili555 on 2010-10-13
I believe that the kernel driver is loading because your ethernet card uses b44 which depends on ssb which drags in b43, even though it's blacklisted. You might try:```
sudo rmmod -f ndiswrapper
sudo rmmod -f b43 ssb
sudo modprobe ndiswrapper
```Does your wireless work now?

As you might see, it's very difficult to get ethernet with b44 and ssb to work correctly and ndiswrapper *without* ssb to work correctly!

If you are certain you will never, ever need ethernet, you can blacklist b44 and ssb.

If it were me, I'd get the firmware and use the native driver and not ndiswrapper.```
$ modinfo b43
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/b43/b43.ko
--- snip ---
depends:        [COLOR="Red"]ssb[/COLOR],mac80211,led-class,cfg80211

``````
$ modinfo b44
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/net/b44.ko
version:        2.0
license:        GPL
--- snip ---
depends:        [COLOR="Red"]ssb[/COLOR],mii
```

---

### Post by breadbin on 2010-10-14
thanks for that but it still not working in fact i think i might have to reinstall cos the wifi is gone from the menu now and i can't see it anywhere. i tried them commands and got 2 errors along the line of not existing or something but might try the firmware. is it the firmware from dell that you suggesting? or broadcom i might have a look:)

ok just had a look at the page 

[http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation]("http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation")

here and need to get fwcutter and stuff installed. thanks for putting me on the right track though;)

---

### Post by breadbin on 2010-10-14
thanks chilli, i managed to get it working with the firmware and fw-cutter. was really so easy to do:) thanks

---

### Post by chili555 on 2010-10-14
Great work! Glad it's working.

---

