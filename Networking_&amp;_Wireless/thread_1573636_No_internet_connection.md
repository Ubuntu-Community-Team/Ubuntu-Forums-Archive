---
title: "No internet connection"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by johnwright on 2010-09-13
I decided to try Ubuntu on my Win7 machine.  I have a Gigabyte EP45-UD3P motherboard with a realtek Ethernet adapter.  My /etc/network/interfaces has :

auto lo
iface lo inet loopback

ifconfig shows lo and wlan0 interfaces.

Any help on getting it to work?

---

### Post by MaindotC on 2010-09-13
Sure - here'a a [Basic Troubleshooting Guide](http://ubuntuforums.org/showthread.php?t=25557) for your wired adapter, or here's the  [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  You can refer to those but if you want I'll help you through this now.

Let's see if your hardware is detected.  Post the output of:```
lshw -C network
```

---

### Post by Iowan on 2010-09-13
Your */etc/network/interfaces* looks normal for a Network Manager-controlled machine. **ifconfig -a** will show all configured interfaces - active or not...
**sudo lshw -C network** will provide more information about your interfaces - including drivers, aliases, and (maybe) IP address.

---

