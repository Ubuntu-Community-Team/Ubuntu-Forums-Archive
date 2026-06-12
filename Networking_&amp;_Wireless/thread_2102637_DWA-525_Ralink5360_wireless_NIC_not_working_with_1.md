---
title: "DWA-525 Ralink5360 wireless NIC not working with 12.04LTS"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by CGeek on 2013-01-07
Ok, so I have a DWA-525 Ralink5360 wireless NIC and I've been searching  and trying methods all through the ubuntuforums and otherwise, namely:

[http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/](http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/)
[http://ubuntuforums.org/showthread.php?t=1559576](http://ubuntuforums.org/showthread.php?t=1559576)
[http://ubuntuforums.org/showpost.php?p=10055176&postcount=4](http://ubuntuforums.org/showpost.php?p=10055176&postcount=4)
etc...

The final thing I tried was this: [http://ubuntuforums.org/showpost.php?p=12343622](http://ubuntuforums.org/showpost.php?p=12343622)
There  was even a post telling to edit some lines to include rt5360 and I  checked the latest versions and they were already there...

The  final result is that ubuntu 12.04 is not even displaying the wireless  card be it in the notification area nor through the iwconfig
lshw -C network: 
*-network UNCLAIMED
           description: Network controller
           product: Ralink corp.
           vendor: Ralink corp.
           physical id: 3
           bus info: pci@0000:05:03.0
           version: 00
           width: 32 bits
           clock: 33MHz
           capabiities: cap_list
           configuration: latency=32 maxlatency=4 mingnt=2
           resources: memory:e3000000-e300ffff

I also noticed some error messages during booting and when I modprobe rt2x00pci in dmesg: 
[   26.588543] rt2800pci 0000:05:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.598629] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.608682] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.618762] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.620009] psmouse serio1: Failed to enable mouse on isa0060/serio1
[   26.628805] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.638862] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.648917] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.658960] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.669015] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.679060] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.689154] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.699194] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.709300] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.719389] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.729439] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.739614] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.749664] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.759910] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.759949] phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset 0xffff detected.
[   26.759977] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   26.760043] rt2800pci 0000:05:03.0: PCI INT A disabled

That  seems to me like some sort of error in the driver itself...do I use one  of the older ones in [http://www.orbit-lab.org/kernel/compat-wireless/](http://www.orbit-lab.org/kernel/compat-wireless/) ?

Please advise.

---

### Post by CGeek on 2013-02-01
I made a fresh install (the first since a few years now) but I still needed an internet connection to be able to update it properly and install the required packages

I connected it to my other box using a USB Hub-to-Hub connection, made all the upgrades and ran these two lines

sudo apt-get install linux-backports-modules-cw-3.6-precise-generic-pae linux-backports-modules-net-3.6-precise-generic-pae

rebooted and that did the trick

---

### Post by vezolmi on 2013-04-11
I installed the 5360 model D-Link adaptor in Lubuntu with [http://ubuntuforums.org/showthread.php?t=2008849&p=12302336#post12302336](http://ubuntuforums.org/showthread.php?t=2008849&p=12302336#post12302336)

---

