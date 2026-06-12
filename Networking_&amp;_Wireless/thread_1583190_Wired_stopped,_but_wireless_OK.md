---
title: "Wired stopped, but wireless OK"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by Dankroad on 2010-09-27
I'm experiencing the [same issues]("http://ubuntuforums.org/showthread.php?t=1579047").  I'm running Lucid 10.04 on a Dell Studio 15. I first noticed it today, but it could have been happening for a couple of days.  I get no IP address for my wired connection when running ifconfig.  Wireless is connecting perfectly.  Normally when I start up both wired and wireless connect and get a local IP address like 192.168.1.11*.  Additionally, the router has a slowly blinking light corresponding to this connection, which is different from other good connections like my printer which has a solid light on.   
Here is output from running route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```Thanks for any help!

---

### Post by mickwombat on 2010-09-27
Try setting a static address and gateway for the wired connection.

Sometimes it just works for reasons unknown.  Pinging 8.8.8.8 (Google DNS) is a good test of connection to outside world....and easy to remember.

---

### Post by Iowan on 2010-09-27
Moved to separate thread.

---

