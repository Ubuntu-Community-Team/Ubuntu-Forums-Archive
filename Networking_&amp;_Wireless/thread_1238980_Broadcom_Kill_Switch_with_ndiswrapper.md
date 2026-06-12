---
title: "Broadcom Kill Switch with ndiswrapper"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by JSHarrison on 2009-08-13
I have set up my wireless to use ndiswrapper because it is much faster for me than the b43 driver. I have it set up and working but there's one bug I've yet to work out. When I boot up, I have to open a terminal and type: sudo rmmod ndiswrapper, then I have to press the wifi button on the front of my computer to turn the wireless on, then I have to type: sudo modprobe ndiswrapper. After doing this, the wireless will work.

Is there any way to either disable the use of this wifi button/kill switch or use a command line in /etc/rc.local to turn on the wireless before starting up ndiswrapper?

Currently my /etc/rc.local looks like this:

```
rmmod b43
rmmod ssb
modprobe ndiswrapper
exit 0
```

---

### Post by JSHarrison on 2009-08-14
Additional info:
I'm using a Broadcom BCM4318 on an Acer Aspire 5002WLMi

output of sudo lshw -C network:
```

  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 02
       serial: 00:14:a4:2a:93:5f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5a driverversion=1.53+Broadcom,12/22/2004, 3.100. ip=192.168.1.9 latency=64 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

---

