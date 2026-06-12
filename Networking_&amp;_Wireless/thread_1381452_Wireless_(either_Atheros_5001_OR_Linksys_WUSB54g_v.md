---
title: "Wireless (either Atheros 5001 OR Linksys WUSB54g v4): Ubuntu Studio 9.10 PLEASE HELP!"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by sciomind on 2010-01-14
Hi all!

About a week ago I installed Ubuntu Studio 9.10 (Karmic Koala) and must say that I am impressed by both its appearance and performance.  I was particularly delighted when it detected my nvidia graphics card and installed it with minimal input from me, just minutes after my first boot-up!

My problem, however, is getting wireless connectivity with this machine.  It's an Acer Aspire 5520 with a built-in Atheros wireless card (lspci lists it as:
   05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

I have been trying for days to get wireless to work, hour after hour.  It can see networks, but can't connect (can't obtain ip address).

At one point I even swapped out the internal Atheros Card for an Intel card (3945 I believe) but at that point it wouldn't even recognize that a card was installed at all (Even in Windows -- this is a dual boot machine) so I ended up putting the Atheros card back in.

I also obtained a Linksys WUSB54g usb wireless adapter, and no matter what I do I can't get it to connect either.

I really have been working on getting wireless access on this machine for MORE than full time for just about a week now, so I would really appreciate any knowledgeable help at all.

Thanks in advance!

---

### Post by changingstate on 2010-01-14
Okay, if you could make sure the usb device is plugged in and post the output of 

```
sudo lshw -C network
``````
lsusb
```please?

---

### Post by sciomind on 2010-01-14
Thanks for the quick reply!
Here's the output:
---------------------------------------------------------
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:56:a3:db
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.101 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:27 memory:f2688000-f2688fff ioport:30f8(size=8) memory:f2689c00-f2689cff memory:f2689800-f268980f
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1c:26:b0:a7:e9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f2200000-f220ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:23:69:6b:74:b4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
--------------------------------------------------------------
$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 13b1:000d Linksys WUSB54G Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
--------------------------------------------------------
Hope that helps.

---

### Post by changingstate on 2010-01-15
Ok, take a look at this for the atheros card : [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

Please ask if you have any questions or need further assistance.

---

