---
title: "Wireless USB Stick not working"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by Teeba on 2011-09-03
Hi there,

I've just installed Ubuntu today so be patient with me..

My usb wireless adapter recognises my SSID and asks me for the WPA pass but can't connect. It just continually tries and tries, then gives me the 'wireless disconnected' message afterwards.

I've done a lsusb which tells me that my USB stick is an RT2870/RT3070 Wireless Adapter.

I've also done a lshw -C network which gives me:

```
 *-network               
       description: Ethernet interface
       product: Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 11
       serial: bc:ae:c5:34:c4:ab
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 multicast=yes port=twisted pair
       resources: irq:78 memory:fbdfc000-fbdfffff ioport:b800(size=256) memory:fbdc0000-fbddffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@2:4
       logical name: wlan0
       serial: 7c:dd:90:06:34:ef
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-8-generic firmware=0.12 multicast=yes wireless=IEEE 802.11bgn


```

What's wrong and how can I solve it? Keep in mind I have no internet access at all on the ubuntu system (can't plug it into the router) so I can't install any extra tools or anything.. pain I know. I'm almost completely clueless with the command line so a step by step would really help :)

Thanks

---

### Post by nm_geo on 2011-09-03
By the welcome to the Forum..

In the terminal

```

lsmod
```That will tell us drivers and modules that are loaded.
```

lsusb
```Those numbers can be important on that dongle.

---

