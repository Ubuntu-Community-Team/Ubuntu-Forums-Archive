---
title: "Almost an internet connection sharing issue"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by malcmail on 2011-09-02
The set up is this. Pfsense box acting as router / firewall (usually works well). It feeds a wireless AP  and that feeds all my machines. All on 192.168.1.x. I've recently added another cast off box which I was going to use for file backups. Since the main box it will get back ups from is next to it (and because there's no wireless cards kicking about) I've decided to plug it into one of the 192 boxes. I've set up the ethernet port OK and the box attached (which is now on 10.42.43.x along with the interface of the ubuntu box hosting it) can ping into the 192 etc and also the world at large. But it won't take pings the other way round. I'm presuming its the masquerading / firewall but being a bit simple I can't work out what the problem is.  

The iptables for the box sharing the connection - 

```
-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-A INPUT -i eth1 -p udp -m udp --dport 67 -j ACCEPT 
-A INPUT -i eth1 -p tcp -m tcp --dport 67 -j ACCEPT 
-A INPUT -i eth1 -p udp -m udp --dport 53 -j ACCEPT 
-A INPUT -i eth1 -p tcp -m tcp --dport 53 -j ACCEPT 
-A FORWARD -d 10.42.43.0/24 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A FORWARD -s 10.42.43.0/24 -i eth1 -j ACCEPT 
-A FORWARD -i eth1 -o eth1 -j ACCEPT

```The result of route on the same box is-
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      *               255.255.255.0   U     1      0        0 eth1
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan2
link-local      *               255.255.0.0     U     1000   0        0 wlan2
default         router.mydomain 0.0.0.0         UG    0      0        0 wlan2


```I'm sure its ridiculously obvious to someone thats knows about these things - that someone isnt me!!

Any help gratefully received.

---

### Post by malcmail on 2011-09-04
Looking at thi sagain is a bridge the best way to do it? If so can I bridge a wireless connection as when I tried to add wlan2 to the bridge it said it wasnt supported.

---

