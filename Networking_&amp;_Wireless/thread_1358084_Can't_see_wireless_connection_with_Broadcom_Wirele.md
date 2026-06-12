---
title: "Can't see wireless connection with Broadcom Wireless BCM4312"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by pensador82 on 2009-12-17
Hi,

I just installed Ubuntu 9.10 on my HP laptop, but I can't see the wireless connection that I have at home. I do see it from Windows 7, though. Here is the result of a few commands:

```
lspci -nn

07:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

lshw -C network

  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f4300000-f4303fff

```

It seems Ubuntu recognizes my wireless card but for some reason the button that I have in front of my laptop is always red no matter what position it is--as if the card was turned off. Any ideas?

---

### Post by Bucky Ball on 2009-12-20
Plug in an ethernet cable if you haven't already and get your updates. This should pick up that card and offer you the drivers (they cannot be included in Ubuntu ISO as they are third-party). Most Broadcom cards work out of the box now (yours definitely).

If you have plugged an ethernet cable and still nothing you might try System->Administration->Hardware Drivers and see if the driver is already there but disabled (Broadcom B43).

---

### Post by howcanireachthesekids on 2009-12-22
> **Bucky Ball said:**
> Plug in an ethernet cable if you haven't already and get your updates. This should pick up that card and offer you the drivers (they cannot be included in Ubuntu ISO as they are third-party). Most Broadcom cards work out of the box now (yours definitely).

If you have plugged an ethernet cable and still nothing you might try System->Administration->Hardware Drivers and see if the driver is already there but disabled (Broadcom B43).
Can you please tell me what are the commands to get the updates needed to get the BCM4312 driver to work if i get internet via cable. :)

thank you in advance

---

### Post by Avidanis on 2009-12-22
> **howcanireachthesekids said:**
> Can you please tell me what are the commands to get the updates needed to get the BCM4312 driver to work if i get internet via cable. :)

thank you in advance


For hardware updates go to :

System/Administration/Hardware Drivers

Activate the B43 driver

---

### Post by Bucky Ball on 2009-12-22
Solved? Could you please explain how for other users. :)

---

### Post by IceDragonkin on 2009-12-24
I'm having a similar issue with my hp mini i just put a clean install of 9.10 on. Here's what i get when i try to do all that.


```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]

lshw -C network

*-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:22:64:81:f9:6a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.0.5 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:26 memory:febfc000-febfffff ioport:ec00(size=256)
```

and when i run updates and go to System/Administration/Hardware drivers and try to activate the drivers it says error check log /var/log/jockey.log where it says this

```
2009-12-24 15:32:19,658 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2009-12-24 15:32:19,701 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2009-12-24 15:32:19,776 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2009-12-24 15:32:23,297 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2009-12-24 15:32:27,825 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2009-12-24 15:32:27,826 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2009-12-24 15:32:27,870 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```
any ideas on what to do?

---

### Post by Avidanis on 2009-12-24
> **IceDragonkin said:**
> I'm having a similar issue with my hp mini i just put a clean install of 9.10 on. Here's what i get when i try to do all that.


```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]

lshw -C network

*-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:22:64:81:f9:6a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.0.5 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:26 memory:febfc000-febfffff ioport:ec00(size=256)
```and when i run updates and go to System/Administration/Hardware drivers and try to activate the drivers it says error check log /var/log/jockey.log where it says this

```
2009-12-24 15:32:19,658 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2009-12-24 15:32:19,701 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2009-12-24 15:32:19,776 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2009-12-24 15:32:23,297 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2009-12-24 15:32:27,825 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2009-12-24 15:32:27,826 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2009-12-24 15:32:27,870 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```any ideas on what to do?



I think you need to go into the blacklist file at  /etc/modprobe.d/blacklist.conf and put a # in front of the "blacklist B43" command.

It appears your driver is being prevented from being initialized at startup due to being blacklisted. You should probably wait though until someone else who is more qualified can verify this.

---

### Post by Avidanis on 2009-12-24
Can you copy and paste your blacklist.conf file to a post ?

Also since the original poster had his issue solved and this thread is marked as solved, you would probably get more help if you reposted your question in a seperate and new thread.

---

### Post by IceDragonkin on 2009-12-24
good try but nope. didn't really help. :( had to set it back because it broke my Ethernet connection.

---

### Post by Avidanis on 2009-12-24
I think by default Ubuntu will use the ethernet connection. If you are trying to connect wirelessly ,disconnect your ethernet and reboot .

Also I found that before I turn on the pc, I need to have my wifi switch turned off. And then I turn it on right after I enter password and hit enter . The wifi light comes on , and I get connected. If I leave the wifi switch on the side of laptop turned on before I boot , It does'nt see my wireless.

---

### Post by IceDragonkin on 2009-12-24
That's no good either. i downloaded some wireless managers and they tell me that they can't find a wireless interface. I have a feeling it's the drivers are wrong, missing or corrupt but i'm not sure what to do about it.

---

### Post by Avidanis on 2009-12-24
Start a new thread , this one is solved.

---

### Post by focwiz on 2009-12-24
> **IceDragonkin said:**
> That's no good either. i downloaded some wireless managers and they tell me that they can't find a wireless interface. I have a feeling it's the drivers are wrong, missing or corrupt but i'm not sure what to do about it.

After installing UNR on my netbook, I had to connect with a cable and download the Broadcom STA wireless driver.  It was installed by the system and now shows in the System/Hardware Drivers menu item.  Ireless light then went to solid blue and the rest was easy configuration.

---

### Post by Bucky Ball on 2009-12-24
> **Avidanis said:**
> ... since the original poster had his issue solved and this thread is marked as solved, you would probably get more help if you reposted your question in a seperate and new thread.

Quite correct. +1

Use thread title describing your problem.

---

