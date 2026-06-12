---
title: "Wifi can access LAN but not internet"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by Chili.willy on 2009-02-25
I installed Ubuntu 8.10 on an old Dell laptop. It has a pcmcia wireless card, an RTL-8180. It is set up and can access other computers on my local network, but it can't get out to the internet.  On my LAN, I can ping other hosts, I can move files with sftp, and I can use Firefox to view my router's Web status and control pages.  But I can't ping sites out on the other side of the router, and Firefox can't load websites.  If I try to ping Canonical.com like this
```
ping -c 4 91.189.84.12
```
I get "Network is unreachable". If I try to visit Google or anything else in Firefox, I get "Firefox can't establish a connection to the server at www.google.com." There are suggestions about a firewall or proxy, but my other laptop works fine (that's how I'm typing this), and the settings are the same. (I'm pretty sure there is no proxy or firewall.)

I tried disabling ipv6 in Firefox by going to the address "about:config" and setting _network.dns.disableIPv6_ to True, but that didn't help. 

Any ideas?  Thanks.
Will

---

### Post by invincibletoviruses on 2009-02-26
this may be of little use to you, but in wireless networking there is something called the hidden node problem it is when computers are networked and a router is in the middle and both people are on ether side of the router they can connect to Internet but cant see each other.you seem to have the opposite.This may something related, google it!
visit link:[http://www.wildpackets.com/images/compendium/topo-1b_2.gif](http://www.wildpackets.com/images/compendium/topo-1b_2.gif) ,to see image

---

### Post by gilby7887 on 2009-02-26
sounds like we have the same problem.

---

### Post by Chili.willy on 2009-02-26
It's fixed.  I think this is how:

I edited /etc/network/interfaces.  Before I started, the file only contained 2 lines:```
auto lo
iface lo inet loopback
```I added the following, based on the same file in my Debian machine:```
allow-hotplug eth0
iface eth0 inet dhcp

iface wlan0 inet static
address 192.168.0.102
gateway 192.168.0.1
wireless-key s:xxxxxxxxxx  #Note, xxxxxxxx isn't my real wireless key!
wireless-essid MonstorMash #Note, that's not my real essid, either.

auto wlan0
```Note that my setup uses a static IP address for wireless clients--that's for a little extra security.  If you are using DHCP, you wouldn't want that "static" in there (I guess you'd want "dhcp", same as for the hardwired eth0 interface), and I suppose you wouldn't want the line that starts with "address".

Good luck!  I hope this helps at least the person with the 7s and 8s in their screen name.

---

