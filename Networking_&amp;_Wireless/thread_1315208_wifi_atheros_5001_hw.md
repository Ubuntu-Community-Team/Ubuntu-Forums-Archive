---
title: "wifi atheros 5001 hw?"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by ottosykora on 2009-11-05
I have problems to make my wifi in Toshiba Satellite MX40 to run.
I have installed the madwifi and wifi radar from the repositiry, but wifi-radar continues to crash, and in the networking I cannot make any contact with anything.
next step?


```
06:02.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.



iwconfig wlan0
wlan0     No such device



lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:6b:57:b8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.50 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:21 ioport:3000(size=256) memory:b0116000-b01160ff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=80 maxlatency=28 mingnt=10
       resources: memory:b0100000-b010ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
 
uname -mr
2.6.31-14-generic i686

lsb_release -d
Description:	Ubuntu 9.10

sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.

```

---

### Post by Iowan on 2009-11-05
Check [this]("http://ubuntuforums.org/showthread.php?t=1312160") one - dunno if it's the same model.

---

### Post by aauvero on 2009-11-21
Hi, I had a similar problem with Ubuntu 9.10 UNR on a JumperPC netbook.  I found this link [http://clayeweb.org/blog/2009/11/11/acer-aspire-one-a0531h-and-opensuse-11-1-ubuntu-netbook-remix/](http://clayeweb.org/blog/2009/11/11/acer-aspire-one-a0531h-and-opensuse-11-1-ubuntu-netbook-remix/) .   The simple solution was to append one line “blacklist acer_wmi” to the /etc/modprobe.d/blacklist-ath_pci.conf file.  Hope this also solves your problem.  Thanks to the genius that posted the solution on CLAYEWEB.ORG!!!

---

