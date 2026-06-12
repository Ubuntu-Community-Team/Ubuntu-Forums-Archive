---
title: "Wired internet not working REALTEK"
date: 2011-12-25
forum: Networking &amp; Wireless
---

### Post by krelverehan on 2011-12-25
Hey guys, I've got a problem with my new laptop running ubuntu 11.04. My wireless works flawlessly but my wired connection is not working. In the networking toolbar the wired network button is greyed out. There is nothing wrong with the connection itself, as I have tested it on devices known to work.

Here is a few things that might help...

**$ sudo lshw -C network**
```

       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 04
       serial: 00:21:cc:51:eb:cd
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:50004000-50004fff memory:50000000-50003fff
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:f0:6d:57:54:3d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.145 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:52000000-5200ffff

```

**$ lspci**
```

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
[COLOR="Red"]01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 04)
01:00.1 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5288 (rev 01)[/COLOR]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

Running PPPoeConfg tells me this:
```

I found 2 ethernet devices:
eth0
wlan0

Are all your ethernet interfaces listed above?
(If No, modconf will be started so you can load the card
drivers manually).  

```
```

NOT CONNECTED
Sorry, I scanned 2 interfaces, but the Access
Concentrator of your provider did not respond. Please 
and modem cables. Another reason for
the scan failure may also be another running pppoe
process which controls the modem.  

```

I connect to a linksys router running Tomato firmware before connecting to the net. I gave my laptop a static IP (192.168.1.145).

I looked through the forums trying to find something relevant to REALTEK, but no luck. I have been using linux for quite some time now, but I am very new to networking. I've tried messing with **/etc/network/interfaces** but it makes no sense to me, so I've reverted it back to normal.

Also are there any good intro to networking guides you can point me at?

Thanks!
-KV

---

### Post by &#3670;&#1763;&#1756;Storm &#3670;&#1763;&#1756;Shadow on 2011-12-26
Check if your NIC got a valid MAC address. I faced that problem about 5mins ago.
Sometimes this may help:
[**Wired Connection is not detecting.**]("http://ubuntuforums.org/member.php?u=1411497")

Hope your problem get solved.

Take Care

---

### Post by krelverehan on 2011-12-26
> **&#3670 said:**
> Check if your NIC got a valid MAC address. I faced that problem about 5mins ago.

How do I check that? Am I checking if my NIC has a valid MAC address? or if it is reading a valid MAC address from my router or some other device?

Here is the readout from **$ ifconfig -a**
```

eth0      Link encap:Ethernet  HWaddr 00:21:cc:51:eb:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:744 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55480 (55.4 KB)  TX bytes:55480 (55.4 KB)

wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:57:54:3d  
          inet addr:192.168.1.145  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76f0:6dff:fe57:543d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34249443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18959032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3778123088 (3.7 GB)  TX bytes:1665202869 (1.6 GB)

```

I have setup my router to give a static IP for both wlan0 and eth0 using the MAC addresses found here.

---

