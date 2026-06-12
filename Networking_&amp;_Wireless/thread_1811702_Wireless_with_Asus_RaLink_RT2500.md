---
title: "Wireless with Asus RaLink RT2500"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by Snakes on 2011-07-25
Hi

For a while now I'm trying to establish a wireless connection to a unprotected wifi network with a internet connection.   On windows/mac computers this worked out of the box. Despite many google-queries and forum threads, I didn't get it done on my ubuntu 10.04 machine.

The computer is a P4 2.8ghz with plenty of ram.    The wifi-card is a Asus RaLink RT2500 .   There is also a wired NIC card: a Broadcom NetXtreme BCM5782, but since the lack of cabled infrastructure I'm not using that.

The loopback interface (lo) has 127.0.0.1 as ip-address and 255.0.0.0 as subnetmask.  For ip it gives me ::1 and netmask 128 and scope host (found this in formation via System > administration > network tools ).

The network (coming from a D-link DWL-G510) is open/unprotected but it's not displayed in the list of available networks in the networkManager applet 0.8.  In fact there is no wireless network in that list, while on the windows/mac's there are plenty of available (protected) networks of the neighbors.

I have tried to make different configuration.   
With auto DHCP ( and DHCP addresses only) I was not able to connect to (or discover) the wifi.
With a manual dhcp configuration based on the info from the established connection on my mac (auto dhcp ip 192.168.0.136 snm 255.255.255.0 ) I was able to connect to the wifi, but didn't succeed to ping the router…
I also noticed some other available wifi networks but they were displayed with strange characters in their names ( see the attached screenshot).


So, I'm missing something?   Can somebody help?

Thanx in advance!

---

### Post by ratcheer on 2011-07-25
Please run "sudo lspci -v" to determine which, if any, kernel driver is being used for the card. Post the output to a reply.

Tim

---

### Post by Snakes on 2011-07-27
Here ya go:

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Hewlett-Packard Company Device 12bc
	Flags: bus master, fast devsel, latency 0
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [e4] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 12bc
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at fc400000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 14e0 [size=8]
	Capabilities: [d0] Power Management version 1
	Kernel driver in use: i915
	Kernel modules: i915

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
	Flags: fast devsel
	Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
	Subsystem: Hewlett-Packard Company Device 12bc
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1440 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
	Subsystem: Hewlett-Packard Company Device 12bc
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1460 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
	Subsystem: Hewlett-Packard Company Device 12bc
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 12bc
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fc480000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=64
	Memory behind bridge: fc500000-fc7fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 12bc
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 14c0 [size=16]
	Memory at 50000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Hewlett-Packard Company Device 12bc
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at 14f8 [size=8]
	I/O ports at 1810 [size=4]
	I/O ports at 1800 [size=8]
	I/O ports at 1814 [size=4]
	I/O ports at 14d0 [size=16]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 12bc
	Flags: medium devsel, IRQ 11
	I/O ports at fc00 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 12bc
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1000 [size=256]
	I/O ports at 1400 [size=64]
	Memory at fc480400 (32-bit, non-prefetchable) [size=512]
	Memory at fc480600 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)
	Subsystem: Hewlett-Packard Company Device 12bc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
	Memory at fc500000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
	Kernel driver in use: tg3
	Kernel modules: tg3

05:04.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 130f
	Flags: bus master, slow devsel, latency 66, IRQ 16
	Memory at fc510000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: rt2500pci
	Kernel modules: rt2500pci


```

---

### Post by ratcheer on 2011-07-27
Ok, your wireless card is a RaLink RT2500 and the kernel has loaded driver rt2500pci for it. I am not familiar with that particular card and driver, but my system has a RaLink 3060 and when the kernel defaulted to loading driver rt2800pci, I could not connect, either.

So, I went to the RaLink website and found out that they listed a different driver for my card. When I downloaded and installed their driver, my wireless started working perfectly. My suggestion would be to check what driver RaLink lists for your card and, if it is different, install RaLink's. This will be a build from source code, so you will also learn more about Linux in doing it.

Other people may have simpler ways of fixing it but, IMHO, the wrong driver is the wrong driver.

Good luck.

Tim

---

### Post by chili555 on 2011-07-27
I wonder if there is a driver conflict. Please post:```
lsmod | grep rt2
lspci -nn | grep 0280
```Thanks.

---

### Post by Snakes on 2011-07-27
```
bankster2@bankster2:~$ lsmod | grep rt2
rt2500pci              13719  0 
rt2x00pci               5995  1 rt2500pci
rt2x00lib              27573  2 rt2500pci,rt2x00pci
led_class               2864  1 rt2x00lib
mac80211              205402  2 rt2x00pci,rt2x00lib
cfg80211              126144  2 rt2x00lib,mac80211
eeprom_93cx6            1333  1 rt2500pci
bankster2@bankster2:~$ lspci -nn | grep 0280
05:04.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
```

---

### Post by chili555 on 2011-07-27
It doesn't appear that you have a driver conflict. rt2500pci and its pals are correct for your device. I saw this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456977](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456977)

This bug suggests that the problem is power saving mode. Please try:```
sudo iwconfig wlan0 power off
```If the card connects, we can write one file to make this persistent. Please post back and let us know.

---

