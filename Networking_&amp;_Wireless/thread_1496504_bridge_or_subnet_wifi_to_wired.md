---
title: "bridge or subnet wifi to wired"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by skullmunky on 2010-05-29
I have an ubuntu desktop (A) with wifi, configured using wicd.  I have another machine with only ethernet (B).  I'd like to connect B to A over ethernet and from there to the internet; after forum searching it sounds like I need to use bridge-utils or iptables, but I'm not clear on what the easiest method is.  I see posts referring to problems with trying to do this using wifi, and other problems with trying to do it with wicd as well.  Anyone have a nice clean set of instructions on how to do this?

Diagram:
==== wired
---- wireless

[cablemodem]==[router]----[A]==[B]

---

### Post by mickeyWD on 2010-05-29
Hi skullmunky,
I want to realize the same topology connecting the wifi laptop to a switch and other pc.

I've found this example: [https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing#simple%20iptables%20example](https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing#simple%20iptables%20example)

It's a really simple solution because all you need is to change some address in this script:```
#!/bin/sh
#
# internet connection sharing wlan0 is the gate way
# eth0 is the lan port this might use a straight ethernet cable to a router wan port or a switch or a single PC
# 192.168.2.2 is the port that is being used by the lan for access I changed it to 192.168.2.254 and set fixed addresses for the wan and router
#
# change wlan0 to ppp0 and you can use this for mobile broadband connection sharing
#
ifconfig eth0 up"
ifconfig eth0 192.168.2.1
echo “1” > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.2.0/24 -j MASQUERADE
iptables -t nat -A PREROUTING -i wlan0 -p tcp --dport 3074 -j DNAT --to-destination 192.168.2.2
iptables -t nat -A PREROUTING -i wlan0 -p udp -m multiport --dports 88,3074 -j DNAT --to-destination 192.168.2.2
iptables -A FORWARD -i wlan0 -d 192.168.2.2 -p tcp --dport 3074 -j ACCEPT
iptables -A FORWARD -i wlan0 -d 192.168.2.2 -p udp -m multiport --dports 88,3074 -j ACCEPT
```

and lunch it with something like
~> sudo ./wlan_gateway.sh

I can ping pc over ethX connection

but it's not going to work because when eth0 is switched on I can't go through the internet anymore.

It look like the requests don't go to wlan0 any-more. I've also set the eth0 connection in networkmanager to manual so that it's not activated, and then labelled to default, when cable is pluged-in.

---

