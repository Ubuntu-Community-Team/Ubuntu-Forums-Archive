---
title: "internet sharing"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by johnh10000 on 2009-05-24
Hi gang,

Iam running ubuntu (intrepid) and dnsmasq, to my little lan. for dns of hosts, and dhcp, all fine.

I am using a 3 dongle at the mo, and opendns for internet dns (3's are not quick at busy times)

I am tring to share the net accross the network, as a precursor to when cable arrives in the next week or two.

I have told dnsmasq about opendns, in a new version dnsmasq.resolv.conf for dnsmasq. what else do I need to do?

ok I now know dnsmasq doesn't share, so whats the recomends here pls

---

### Post by xpod on 2009-05-24
Prior to using dedicated Routers i used to use Firestarter to do my ICS.
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

Or you could cut out the need for any GUI(Firestarter) and configure Iptables directly...
[http://lindesk.com/2007/04/internet-connection-sharing-using-iptables/](http://lindesk.com/2007/04/internet-connection-sharing-using-iptables/)

---

### Post by sahabcse on 2009-05-24
Try firestarter for more info click [here]("http://sahabm.blogspot.com/2008/12/firewall-and-internet-saring.html")

---

### Post by johnh10000 on 2009-05-24
> **sahabcse said:**
> Try firestarter for more info click [here]("http://sahabm.blogspot.com/2008/12/firewall-and-internet-saring.html")

Thanks gang just got firestarter, will fiddle, and report soon.

---

### Post by xpod on 2009-05-24
> Thanks gang just got firestarter, will fiddle, and report soon.

You generally need a second NIC plus a Crossover Cable if theres no switch of some sort available so unless you already have those items you may be just as well buying yourself a cheap router.

---

### Post by johnh10000 on 2009-05-24
> **xpod said:**
> You generally need a second NIC plus a Crossover Cable if theres no switch of some sort available so unless you already have those items you may be just as well buying yourself a cheap router.

hmm funny that, I already have a lan with 3 boxes on it, and an occasional laptop (dhcp) vistor.  This is run offa hub in the living room.  I guess run an extra ubuntu box in the living room with 2 nics in it and feed the net work like that?

Or could I just plug virgin media's wireless router in to my hub ?

next week hen that arrives (hopefully)

---

### Post by xpod on 2009-05-24
> Or could I just plug virgin media's wireless router in to my hub ?


Cant you just use the router for all your networking needs?
Saves using ICS at all.
Although i cant talk.:p
Although our whole network is behind the main Virgin Router i also have a linksys router(connected to me via ICS,when required) that i use as a wireless access point on this side of the house.

---

### Post by johnh10000 on 2009-05-24
> **xpod said:**
> Cant you just use the router for all your networking needs?
Saves using ICS at all.
Although i cant talk.:p
Although our whole network is behind the main Virgin Router i also have a linksys router(connected to me via ICS,when required) that i use as a wireless access point on this side of the house.

Well I haven't seen it yet, if it has 4 eth connecors err 5 unless it's the cbl modem too, then I will.  As you seem to have access to one does it do dhcp and firewall stuff?

---

### Post by johnh10000 on 2009-05-24
> **johnh10000 said:**
> Well I haven't seen it yet, if it has 4 eth connecors err 5 unless it's the cbl modem too, then I will.  As you seem to have access to one does it do dhcp and firewall stuff?

Skip the question!!  I just had a brain wave, went to virgin's site foound out about the router, got the manual.

As u said just you that!! cool four ports everything, and an arial to boot.

---

### Post by xpod on 2009-05-24
> Well I haven't seen it yet, if it has 4 eth connecors err 5 unless it's the cbl modem too, then I will. As you seem to have access to one does it do dhcp and firewall stuff?

You`ll get both a cable modem and a router with Virgin and unless you`ve went for the 50Mb connection the router will be a bog standard Netgear WGR614.It has the 4 lan ports and one wan port.
You cant do much with their custom firmware but it does have the basics you`ll need.

EDIT:Reminds himself to refresh page when distracted by demon children.

---

### Post by MartyBuntu on 2009-05-24
If you have an extra router lying around *(or buy a cheap refurbished one - I got a Netgear for $8 after mail in rebate)* you can chain one router off the other one, providing you disable DHCP in the "slaved" routers setup page. This is how my network is set up.

---

### Post by update_manager on 2009-05-24
> **xpod said:**
> Prior to using dedicated Routers i used to use Firestarter to do my ICS.
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

Or you could cut out the need for any GUI(Firestarter) and configure Iptables directly...
[http://lindesk.com/2007/04/internet-connection-sharing-using-iptables/](http://lindesk.com/2007/04/internet-connection-sharing-using-iptables/)

Some other iptables configuration tools:
Webmin
Shorewall



In general, the iptables configuration can be shortened to something like the below. Its not secure and is for demo purposes of nat + stateful iptables rules.


#!/bin/sh

IPT="/sbin/iptables"

WAN="eth2"
LAN="eth1"
# IP on LAN is 192.168.0.1 

iptables -F
iptables -F INPUT
iptables -F OUTPUT
iptables -F FORWARD
iptables -F -t mangle
iptables -F -t nat

iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP

echo 1 > /proc/sys/net/ipv4/ip_forward

iptables -A INPUT -s 127.0.0.1 -d 127.0.0.1 -j ACCEPT
iptables -A INPUT -i $LAN -j ACCEPT

iptables -A INPUT -p udp --sport 67 --dport 68 -j ACCEPT

iptables -t nat -A POSTROUTING -s 192.168.0.0/24 \
--out-interface eth2 -j MASQUERADE

iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -m state --state RELATED,ESTABLISHED \ 
-j ACCEPT
iptables -A FORWARD -i $LAN -o $WAN -j ACCEPT

---

### Post by johnh10000 on 2009-05-24
only the 10m connetcion , so i'm thinking join my hub to it and ubuntu for my lan and it for wi-fi, no need for dhcp.

not at home at the min yak ltr

---

### Post by johnh10000 on 2009-06-05
> **xpod said:**
> You`ll get both a cable modem and a router with Virgin and unless you`ve went for the 50Mb connection the router will be a bog standard Netgear WGR614.It has the 4 lan ports and one wan port.
You cant do much with their custom firmware but it does have the basics you`ll need.

EDIT:Reminds himself to refresh page when distracted by demon children.

it's arrived!!! 

as you seem to running a V 10m connetion, on their router, you may be able to help.

We "chatted", the other day.  Well it's arrived!

ok it works. now i know the routers gway 192.162.1.1
my lan boxes are 
192.168.52.10  ->tux
           20  ->lounge (xp)
           30  ->bedroom (xp)
local dns 192.168.52.10 via dnsmasq

can't see the inernet when anywhere when i set up boxes to:
ip 192.168.5220
nm 255.255.0.0

dns 192.168.52.10
      0   0  0  0

gwy 192.162. 1. 1

what have I done wrong ?

---

