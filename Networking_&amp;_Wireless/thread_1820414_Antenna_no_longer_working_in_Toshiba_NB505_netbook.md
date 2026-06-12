---
title: "Antenna no longer working in Toshiba NB505 netbook??"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by nosehat on 2011-08-07
My wife's nebook has Ubuntu 10.04.2 LTS (kernel 2.6.32-33-generic i686), and is using the linux driver for Realtek RTL819x wifi cards.  I installed the driver ages ago with:
```
$ sudo add-apt-repository ppa:lexical/hwe-wireless
$ sudo apt-get update
$ sudo apt-get install rtl8192ce-dkms
```
and it has worked fine until an update 2 days ago.  

Now "This driver is activated but not currently in use", and the wifi antenna LED is orange (I think it should be green to be on?)  There is a hotkey combination ([Fn][F8]) to supposedly turn off and on the wireless antenna, but this has no effect.  Also, the little network applet indicator isn't on her top panel anymore, so I can't right click it and enable wireless that way.

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:85:97:19  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e75:8ff:fe85:9719/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1271272 (1.2 MB)  TX bytes:197554 (197.5 KB)
          Interrupt:27 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

```

Normally that should list wlan0 for the wireless.

```
$ ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

```

```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
```

Grrr!

```
$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: 1c:75:08:85:97:19
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:3000(size=256) memory:f050c000-f050cfff(prefetchable) memory:f0508000-f050bfff(prefetchable)
```

Any ideas?

---

### Post by nosehat on 2011-08-08
I should also note, there is no physical switch anywhere on the netbook to turn the antenna back on.  :P

---

