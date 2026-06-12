---
title: "Multiple internet connexions at the same time..."
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by TOXIC0 on 2010-04-11
I explain my problem : I got 2 internet connexions, and I connext to each one through a dedicated networkCard :

[LIST]
[*]eth0  : connected to a HighSpeed internet, all OUTGOING ports except 80 are blocked from the router
[*]wlan0 : connected to a slow internet, all OUTGOING ports are open.
[/LIST]

So, my problem is : I want to use irc, ssh and much more, so I need to use wlan0 for that since it's blocked on the other connexion.

The idea would be that all traffic on every ports except 80 uses the wlan0 interface, while the traffic to port 80 uses the eth0 interface.

Each interface is actually connected to a router/modem wich is a gateway, the 2 interfaces are using different subnetworks :
[LIST][*]eth0 uses 192.168.0.X / 255.255.255.0[*]wlan0 uses 192.168.178.X / 255.255.255.0
[/LIST]

So, since the filtering should be on the targeted port of each IP-packet, I figured I had to uses iptables (static routing is not an option here...)

The idea is to catch every packet whose destination port is 80, and either output it on the eth0 interface, or just change the gateway it's going to use.

I configured my system so that it can access the 2 networks at the same time : I can access LAN ressource on eth0 (192.168.0.xxx) and I have access to the internet and the all 192.168.178.xxx using wlan0, all at the same time... (I used networkManager for that, connected to both networks and checked the "Use this network only for it's local ressources" checkbox in the Ipv4/Route panel for the eth0 profile in nm-applet.)

So the question is : how do I do that ? I'm struggeling with iptables for over 3 hours, found some interresting --oif or --gw options on some internet documentation that are not recognized by my iptable on ubuntu...

Summary : 
One interface used for internet services using port 80.
The other interface for all traffic to the internet using other ports.
=> how ?

---

