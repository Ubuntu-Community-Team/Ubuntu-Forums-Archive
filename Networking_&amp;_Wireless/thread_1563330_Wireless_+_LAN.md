---
title: "Wireless + LAN"
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by tail.kinker on 2010-08-28
I'm using wireless, but at the same time, I'm using a LAN to communicate with printers and my file server.  The problem is, when the wired connection is active, Ubuntu insists on using it for Internet, despite the fact that there's no internet on that network.  

On the other hand, I sometimes use the wired connection at my girlfriend's house for internet, as she lacks wireless.

Is there any way to force Ubuntu to *not* search for Internet on the wired connection unless I specifically tell it to?

---

### Post by BkkBonanza on 2010-08-29
You would want to add a routing rule that tells it to use the LAN gateway for local traffic and the other gateway for internet traffic.

If you're using "Network Manager", I'm not sure if it supports adding that distinction and in my experience anything abnormal and it has flaky fits.

From the command line though it's fairly easy to add alternate routes. First, you would want to see what your current route are. Type **route** to see.

eg. on my machine,
```
$ **route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
```

Which tells me that everything goes to gateway 192.168.2.1 - which is my router.

You would want all local traffic routed to the eth0 and everything else to wlan0 (if that's your wifi interface).

route add default gw 192.168.1.1 dev wlan0
route add -net 192.168.2.0 netmask 255.255.255.0 gw 192.168.2.1 dev eth0
(you would have to use correct addresses for your setup)

If this is confusing, show me your **route** output and /etc/network/interfaces file.

You may find this page helpful (though there is likely better ones),
[http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html](http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html)

---

### Post by tail.kinker on 2010-09-05
In fact, it was even easier than I thought it'd be.  I just selected "DCHP (Addresses only)", and it solved the issue.

---

