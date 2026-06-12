---
title: "WLAN Adapter WG311v3 WORKING w/ 64-bit Kernel"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by kenm_uk on 2010-01-13
Hi. I am trying to get my WG311v3 wireless networking card to work on a new installation of Ubuntu 9.10 (karmic).

I followed many of the instructions on:
[http://ubuntuforums.org/showthread.php?t=612458](http://ubuntuforums.org/showthread.php?t=612458)
and:
[http://ubuntuforums.org/showthread.php?t=1136959](http://ubuntuforums.org/showthread.php?t=1136959)

I later found the post:
[http://ubuntuforums.org/showthread.php?t=1193831](http://ubuntuforums.org/showthread.php?t=1193831)
which links to:
[http://sites.google.com/site/subtlegems/netgear-wg311v3-ndis-driver-for-linux-amd64](http://sites.google.com/site/subtlegems/netgear-wg311v3-ndis-driver-for-linux-amd64)
containing some 64-bit drivers.

However, I am still not able to get my wireless card to work.  
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

Does anyone know where to begin in fixing this problem?

One suspicion is that I originally installed the incorrect drivers and I am not sure how to uninstall the driver and reinstall a different/correct one (as found in ([http://sites.google.com/site/subtlegems/netgear-wg311v3-ndis-driver-for-linux-amd64](http://sites.google.com/site/subtlegems/netgear-wg311v3-ndis-driver-for-linux-amd64)).

Thanks,
Ken


P.S. 
```
$ sudo lshw -C network
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:fded0000-fdedffff memory:fdee0000-fdeeffff
  *-network
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:22:15:98:2c:13
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.100 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:29 memory:fe02b000-fe02bfff ioport:f600(size=8) memory:fe02a000-fe02a0ff memory:fe029000-fe02900f

```

```
$ sudo ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wg311v3 : driver installed
        device (11AB:1FAA) present

```

```
$ lsmod | grep ndi

```
Should this be empty?

---

### Post by kenm_uk on 2010-01-13
After running
```
$ sudo modprobe ndiswrapper
```

I found this:
```
$ tail /var/log/messages
Jan 13 22:22:07 htpc kernel: [  166.812487] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Jan 13 22:22:07 htpc kernel: [  166.812496] ndiswrapper 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
Jan 13 22:22:07 htpc kernel: [  166.813072] ndiswrapper: using IRQ 16
Jan 13 22:22:10 htpc kernel: [  169.100164] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
Jan 13 22:22:10 htpc kernel: [  169.100170] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
Jan 13 22:22:10 htpc kernel: [  169.100178] ndiswrapper (mp_halt:262): device ffff8800b702e580 is not initialized - not halting
Jan 13 22:22:10 htpc kernel: [  169.100180] ndiswrapper: device eth%d removed
Jan 13 22:22:10 htpc kernel: [  169.100192] ndiswrapper 0000:01:08.0: PCI INT A disabled
Jan 13 22:22:10 htpc kernel: [  169.100214] ndiswrapper: probe of 0000:01:08.0 failed with error -22
Jan 13 22:22:10 htpc kernel: [  169.100259] usbcore: registered new interface driver ndiswrapper

```

The driver does not seem to be loading correctly.  I think I need advice on how to remove the driver from ndiswrapper completely and to reinstall it.  I may also need advice on the correct 64-bit driver to use.

Thanks,
Ken

---

### Post by shearn89 on 2010-06-06
Late to the party, but I'm going to bump this, since I have the exact same problem...

Just started my thread here: [http://ubuntu-utah.ubuntuforums.org/showthread.php?p=9419462#post9419462](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=9419462#post9419462)

---

### Post by kenm_uk on 2010-06-06
I abandoned all attempts to get the wifi card to work. The machine is using a wired LAN cable to cennect to the network. If you have any luck, I would be interested in what you learn.

---

### Post by shearn89 on 2010-06-06
Yeah, from my googling I think it's not going to happen. I'll keep you posted.

---

