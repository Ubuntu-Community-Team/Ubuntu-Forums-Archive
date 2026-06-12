---
title: "Wired Network Problem"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by jiangshi on 2009-07-25
Greetings!

I just bought an Acer Aspire One mini notebook - 1.6ghz Intel Atom processor N270; 1gb ram; 160gb HD. It came loaded with XP Home, but is now dual-booted with Xubuntu 9.04.

NIC is Atheros AR8132 PCI-E Fast Ethernet Controller

While both wired and wireless work well in XP, only the wireless works in Xubuntu, and it worked out of the box. It would appear that Xubuntu is not recognising the above NIC for my wired network.

Any help on this is greatly appreciated.

~jiangshi

---

### Post by Iowan on 2009-07-25
Post results of **ifconfig** and **lshw -C network**. It *might* be that the wired works, but wireless gets priority.

---

### Post by jiangshi on 2009-07-25
Greetings, Iowan!

Thank you for your reply. Listed below are the results:

Results from ifconfig -

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3064 (3.0 KB)  TX bytes:3064 (3.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:53:ea:5a  
          inet addr:192.168.0.27  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fe53:ea5a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:911137 (911.1 KB)  TX bytes:209732 (209.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2C-53-EA-5A-61-35-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Results from lshw -C network

  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2c:53:ea:5a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.0.27 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4a:50:d3:07:7e:28
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Iowan on 2009-07-26
[Here]("http://ubuntuforums.org/showthread.php?t=1141529") is a (solved) thread with similar problem.

---

