---
title: "&quot;Create new network&quot; not functioning as directed"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by Zwerdlds on 2010-09-20
I've gotten the Ubuntu Broadcom STA driver working on my AppleTV by (not blacklisting) adding the appropriate rmmod statements to my rc.local script.  The system now recognizes the card;  lswh -C network:
```
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 05
       serial: 00:23:12:1e:53:de
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:22100000-22103fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth0
       version: 10
       serial: 00:23:32:34:7a:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.200.55 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:20 ioport:1000(size=256) memory:22000000-220000ff
```

I can now successfully join wifi networks on the device.  My ultimate goal is to create a wifi AP using the card via Ubuntu.  The card is a bcm4328.  

I have attempted to create a wifi hotspot using the "Create new network" menu item from the network menu applet.  When I try to join the network on my MacBook, it apparently can join successfully, but then gets a "Self Assigned IP" which is outside the LAN's subnet (which is 192.168.200.X, while the IP on the MBP is 169.254.161.193 and the network control panel indicates that it is self-assigned).

 It would appear that the AP on the AppleTV is not bridged with the wifi.  I have attempted to follow the CLI-based tutorials but chickened out when I saw I had to set the card to master mode as I do not believe the bcm4328 is capable of this.

What are my options?

---

### Post by Zwerdlds on 2010-09-20
[bump] I have already tried Firestarter.

---

### Post by Zwerdlds on 2010-09-20
Does anyone have any idea about this?

---

### Post by Zwerdlds on 2010-09-22
I have since tried the [shared ethernet connection through wireless tutorial]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") with poor results.  The device no longer accepts VNC screen control requests and SSH connection requests are refused over port 22.

Furthermore, the network I set up does not appear.  When I specify to join a hidden network, the connection times out.

Does anyone have any idea!?

---

