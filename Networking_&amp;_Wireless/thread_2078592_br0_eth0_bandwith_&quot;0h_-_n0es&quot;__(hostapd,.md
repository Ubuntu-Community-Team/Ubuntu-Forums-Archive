---
title: "br0 eth0 bandwith &quot;0h - n0es&quot;  (hostapd, wifi, briged interfaces)"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by yer on 2012-10-31
So heres the deal.

relivant network nodes:

router                      10.1.1.1
ubuntu pc #1 yerboxII       10.1.1.9
ubuntu pc #2 media-desktop  10.1.1.10

relivant interfaces:

yerboxII: bridged eth0 wlan1 running hostapd
eth0:  n/a
wlan1  n/a
br0    10.1.1.9

media-desktop: connected to yerboxii's hostapd via WPA2 
wlan1  10.1.1.10


networking works fine, all nodes can ping all nodes, internet access, ect.

the problem:
if yerboxII is downloading from the internet at more than 200k/sec on eth0, then media desktop cannont stream video over the wifi.
this doesnt make sense to me because the files are located on yerboxII and media-desktop and yerboxII are directly connected via wifi using nfs mount. so anything i do on yerboxII's eth0 should not affect bandwith between the two computers. unless the bridge br0 is replaying all traffic from and to both computers over the wifi? any way to confirm this?

any help would be greatly apprecheated. because god forbid dora the explorer in 720p cant be played in the living room for two minutes while i download an iso.

thanks in advance guys, any config files you need to look at just let me know.

---

### Post by yer on 2012-10-31
come on people, 63 views and 0 replies.

---

