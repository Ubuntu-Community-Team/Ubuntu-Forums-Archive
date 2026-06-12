---
title: "wireless problems"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by danielb2 on 2008-12-19
okay so like many other im very new to ubuntu. i just installed it and i cant connect to the internet. i cant even connect through my kat! okay so iv been reading and a lot of people have the same problem that i am haveing. i have Atheros 802.11 wireless LAn card. it says it finds it but i have no idea what the prob is. any ideas?


just in case i ran 

lshw -c network



*-network
description: Rthernet interface
product: mcp67 ethernet
physical id: a
bus info: pci@0000:00:0a.0
local name: etho
version:a2
serial: 00:1b:24:ef:13:c4
width:32 bits
clock:66 mHz
capabilities: bus_master cap_list ethernet physical
configuration: brocast=yes drver= forcedeth driverversion=0.61 latency=0 maxlatency=20
mingnt=1 module=forcedeth multicast=yes
*network UNCLAIMED
descrption: ethernet controler
product: AR242x 802.11abg Wireless PCI Express Adapter
Vender: Atheros Communications Inc
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33 mhz
capabilities: cap-list
configuration; latency=0
*network Disabled
description: ethernet interface
physical id: 1
local name: pan0
serial: b2:57:12:c7:02:09
capabilities: ethernet physical
configuration: broadcast=yes driver= bridge driverversion=2.3 firmware= N/A multicast=yes



sudo iwconfig

lo no wireless extensions
eth0 no wireless extensions
pan0 no wireless extensions

---

### Post by iponeverything on 2008-12-19
Is the network applet showing on the upper panel?
post the output from:

```

sudo lshw -c network
sudo iwconfig
sudo ps uaxw|grep applet

```

---

### Post by danielb2 on 2008-12-19
yah the 2 computer thing? it has an x on it

---

### Post by superprash2003 on 2008-12-19
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

