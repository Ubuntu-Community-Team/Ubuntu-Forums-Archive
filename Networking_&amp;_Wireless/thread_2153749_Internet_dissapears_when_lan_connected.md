---
title: "Internet dissapears when lan connected"
date: 2013-06-12
forum: Networking &amp; Wireless
---

### Post by decrepit on 2013-06-12
Just purchased a new desktop, installed 12.04, copied ufw and samba from the old machine running 10.04. I had this connected via a cross over cable to a laptop with 10.04.
Desktop has 2 nics, eth0 to adsl modem, eth1 to laptop, the old set up allowed transfer of files between both computers, and allowed the laptop to connect to the internet via the desktop.

Something is very strange with the new one, with eth1 disconnected the desktop has normal internet with this route.
(New Percy)
```
michael@Percy:~$ route
Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

default         nexthop.wa.iine 0.0.0.0         UG    0      0        0 eth0

124.169.236.0   *               255.255.255.0   U     1      0        0 eth0

link-local      *               255.255.0.0     U     1000   0        0 eth0

nexthop.wa.iine *               255.255.255.255 UH    0      0        0 eth0

michael@Percy:~$ 
```

Very similar to the old set up

```
(Old Percy)
michael@Percy:~$ route

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

nexthop.wa.iine *               255.255.255.255 UH    0      0        0 eth0

10.0.1.0        *               255.255.255.252 U     1      0        0 eth1

124.150.52.0    *               255.255.255.0   U     1      0        0 eth0

link-local      *               255.255.0.0     U     1000   0        0 eth1

default         nexthop.wa.iine 0.0.0.0         UG    0      0        0 eth0
```

Then when I activate eth1 this happens.

(new Percy laptop connected)
```

michael@Percy:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         Percy.local     0.0.0.0         UG    0      0        0 eth1
10.0.1.0        *               255.255.255.252 U     1      0        0 eth1
124.169.236.0   *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0



```

I've obviously done something wrong, been scratching my head trying different things for the last couple of days, can anybody help please?


edit, I've just had a thought, before I bought the 2nd nic, I had 2 network connections on eth0, samba and internet, and switched between as I swapped cat5 cables.

Is there a file somewhere that thinks this is still the case?
Maybe I'll try deleting both connections and starting again.

Yippee that worked!

Samba's not quite right, but I'll call this thread closed, play around for a bit and start another thread if I can't sort it.

---

### Post by newbie-user on 2013-06-13
Looks like eth1 is set as the default connection. Check your /etc/network/interfaces file for the "gateway" line. Whichever interface has that line will be used as the default route.

---

### Post by decrepit on 2013-06-13
Thanks newbie, that's probably it. At one stage I had a gateway set for eth1. 
I assume my deleting the 2 interfaces has removed it, cause there's no "gateway" line in /etc/network/interfaces now

---

