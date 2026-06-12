---
title: "Still trouble with Atheros wireless on HP DV9702EA."
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by Zombie13UK on 2008-12-11
OK, I thought I'd start a new thread instead of adding to my last one, as I'm now using Ubuntu 8.10, and heard how "easily" it picks up wireless NICs. Hmmmm...

I'm still having the same problems. Under "System -> Administration -> Hardware Drivers", it says "Support for Atheros 802.11 wireless LAN cards." and is set as "activated". However, under "System -> Preferences -> Network Configuration" there is nothing listed under "Wireless".

How can I got about getting working? I've tried adding an entry with all the appropriate details such as SSID and WEP key, but there's no option to activate the connection.

Doing an "ifconfig" at the command line gives...

```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:2c:32:0b  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe2c:320b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44624 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66641585 (66.6 MB)  TX bytes:1915603 (1.9 MB)
          Interrupt:20 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)
```

So where's wlan0? I thought this was supposed to be simple these days...


EDIT: Doing "lspci -v" gives the following, if it's any help...

```
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137b
	Flags: fast devsel, IRQ 16
	Memory at f2000000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath_pci
```

Cheers. :)

---

### Post by ibutho on 2008-12-11
You need to let us know which chipset is used on your laptop. What is the output of running
```
sudo lspci | grep -i net
```
and
```
sudo lshw -C network
```

---

### Post by Zombie13UK on 2008-12-11
Cheers!

```
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

and

```
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1e:68:2c:32:0b
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.3 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:72:c8:fc:26:e1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by |{urse on 2008-12-11
This howto fixed this very problem for someone a few days ago

[http://ubuntuforums.org/showpost.php?p=6316502&postcount=5]("http://ubuntuforums.org/showpost.php?p=6316502&postcount=5")

---

### Post by Zombie13UK on 2008-12-19
Many thanks for that! I've installed madwifi, and now have a "wifi0" listed when doing "ifconfig". However, the post says to blacklist ath5k, which I've done, but the post then linked to says to do the complete opposite. Also, am I supposed to disable the Atheros option under Hardware Drivers?

I'm now confused what to do. I've added the wireless network details under the Network Configuration, but can't see any way to start the connection, or even where to attach those wireless settings to "wifi0".

Cheers. :)

---

