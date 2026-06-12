---
title: "Frequent network interruptions (no wicd or network manager)"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by El_Belgicano on 2012-01-12
Hello all, my ubuntu (10.04) laptop is behaving quite annoyingly over the network:

_Connected are:_ a windows pc (wired) and the laptop (either wired or wireless WPA).

_Management of the network interfaces:_ pure ifup/ifdown based on /etc/network/interfaces. (Nothing like wicd/NM on the laptop)

_Symptoms:_ two different situations may (one of them will, it's only a matter of time) happen:
**a)** windows pc is getting a fine connection (browsing and everything: ok), when enabling the connected interface on the laptop (wlan0 or eth2) i can load a few pages in firefox or connect to skype or something small, after this (quite fast...), both the windows pc and the ubuntu laptop lose connection.
**b)** it does not happen right away and happens only on the laptop, i lose connection (windows pc is fine)
**both)** with "losing connection" i mean "nothing can be loaded in FF or whatever else, but i did not notice any changes in the 'ifconfig' results and i'm still able to ping the outside world".

_Current "remedies":_ depends on the situation:
**a)** swear internally, reset modem... wait and start browsing again.
**b)** issuing a "sudo /etc/init.d/networking restart" is sufficient to give me back a working connection...

Voila, if you need anything else i'll be more than happy to provide the information you need.

Thanks in advance...

---

### Post by El_Belgicano on 2012-01-13
A few things that might help:

**/etc/network/interfaces**
```
auto lo

iface lo inet loopback
iface wlan0 inet dhcp
iface eth2 inet dhcp

iface default inet dhcp

iface bonheiden inet dhcp
	wpa-ssid belkin54g
	wpa-psk XXXXXX
```

**/etc/resolv.conf**
```
nameserver 192.168.2.1
domain Belkin
search Belkin
```

**sudo lshw -c network**
```
  *-network DISABLED      
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: c1
       serial: 00:26:6c:88:24:a6
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=yes multicast=yes port=twisted pair
       resources: irq:16 memory:d5000000-d503ffff ioport:3000(size=128)
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: 4c:ed:de:11:d1:0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 ip=192.168.2.4 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:17 ioport:2000(size=256) memory:d4000000-d4003fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

Thanks for your time...

---

