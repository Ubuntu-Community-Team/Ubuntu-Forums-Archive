---
title: "routing with one physical interface"
date: 2012-12-11
forum: Networking &amp; Wireless
---

### Post by KisteBecks on 2012-12-11
Hi,

i would like todo some traffic shaping experiments, for this i need a "real" linux instead of my openwrt router.

do keep things simple i was thinking about letting openwrt handle dhcp/dns and just tell the "new linux" todo routing.
openwrt's dnsmasq tells the clients via dhcp option 3 that "new linux" is the router. 

but so far my client only sends data to "new linux" but does not get packages back?

to enable routing i enabled forwarding on "new linux".
"new linux" is on 192.168.11.171, openwrt is on 192.168.11.1

is it possible todo routing with only one real interface on the new linux box?



someone from #openwrt@freenode told me that i need to disable icmp redirects for this. 
(or the hosts would figure out that the new router is not the shortest way to the internet and route traffic differently)

found these command that probably worked:

```

sysctl -w net.ipv4.conf.all.accept_redirects=0
 sysctl -w net.ipv4.conf.all.send_redirects=0
sysctl -w net.ipv4.conf.eth0.send_redirects=0

```after entering the above command on the "new linux" ping from clients to hosts on the internet did no longer show a icmp redirect message.

---

### Post by KisteBecks on 2012-12-11
afrer reading some more i come to the conclusion that you really do need two subnets for routing.
hopefully my unmanaged switch can handle two subnets

---

### Post by iponeverything on 2012-12-11
Create a sub-interface on a separate subnet. 

I have done firewall'ing though a single interface box this way..

---

### Post by KisteBecks on 2012-12-22
ah, thats interresting. thx

---

