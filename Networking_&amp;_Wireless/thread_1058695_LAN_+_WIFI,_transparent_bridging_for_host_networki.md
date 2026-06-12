---
title: "LAN + WIFI, transparent bridging for host networking?"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by Ng Oon-Ee on 2009-02-03
Hi all, I have a pretty complicated use-case here (I think), so would like to ask for help.

I've got a laptop with functioning WIFI (no need for ndiswrapper, thankfully), the card shows up on lspci as:-
```
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```

Also the typical run-of-the-mill LAN connection shows up as:-
```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
```

When I'm at home, or on the road, my internet connection comes through my wireless connection, the LAN connection is idle. When I'm in my office, my internet connection comes through my Ethernet port, the WIFI is idle.

However, now I'm trying to setup VirtualBox with RDP, which requires host networking so that I can access the headless VM through the internal network. Unfortunately all the guides I've seen refer to the use-case where either internet is always through WIFI (in which case eth0 is bridged) or bridging through a tap interface when the computer only has one LAN connection.

Would it be possible to create a tap interface to either eth0 or wlan0, depending on which has connectivity? Or perhaps bridge eth0 AND wlan0 so that both behave as one interface, which could then presumably be bridged through a tap for internal host networking? I'm looking for something similar to Windows bridging of two network connections to look like one to all programs.

Help much appreciated.

---

### Post by Ng Oon-Ee on 2009-02-03
Ah, I think I got something working. Here's my /etc/network/interfaces...

```
auto lo br0

iface lo inet loopback

iface br0 inet dhcp
bridge_ports wlan0 eth0
bridge_maxwait 0
```

It works with the LAN, my VM has its own IP on my office's local network, different from my host machine's (due to DHCP). Am waiting to try it out at home on my own WIFI. I disabled Network Manager, am unsure whether this would work with it on (some reports suggest no) and I really have to get to REAL work so won't be testing that just yet.

---

