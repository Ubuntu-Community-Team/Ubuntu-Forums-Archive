---
title: "Wireless disconnecting randomly"
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by swinghein on 2011-04-21
Running 10.10 on Hp dv2000. Approx once a day wireless asks for password authentication but cannot re-connect to wireless network. I verified connection,correct password and modem & router functionality but still will not re-connect. After re-boot problem is resolved for another day or two.

---

### Post by josephmills on 2011-04-21
hi there first press **ctrl+alt+T **than  could we please see a ```
sudo lshw -c network 
``` it takes a little while too load

---

### Post by swinghein on 2011-04-22
*-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:5c:ed:a2
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f4200000-f4203fff ioport:3000(size=256)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:93:0b:51
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-28-generic firmware=228.61.2.24 ip=192.168.1.105 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:f4300000-f4301fff

---

### Post by josephmills on 2011-04-22
please go to **system-->pref-->password and encryption keys ** please delete any pass words that might be getting in the way.

---

### Post by swinghein on 2011-04-22
I deleted the password as instructed and then re-connected. Thanks for the advise, will post in a couple days to update.

For education's sake, is there a name for what I just did? I'm a new user and still building a vocabulary for Linux

---

### Post by josephmills on 2011-04-22
> **swinghein said:**
> I deleted the password as instructed and then re-connected. Thanks for the advise, will post in a couple days to update.

For education's sake, is there a name for what I just did? I'm a new user and still building a vocabulary for Linux

playing with rainbow tables ?

---

