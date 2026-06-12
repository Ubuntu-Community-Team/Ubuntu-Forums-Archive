---
title: "Monitor a LAN"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by Kyluke on 2012-11-29
So I was wondering if there is software to monitor an entire subnet from a node.

I did some Google searches and found nothing but something that monitors a PC's Tx & Rx connections which is not what I want.

Does anybody know how to monitor a subnet's quality (ie. ping, packet losses, current load perhaps, traceroute etc).

---

### Post by Sergius14 on 2012-11-29
It is very ambiguous your defition by "entire LAN".

You have to be more specific about what you want to monitor and why.


I can only help with two aproches:

Single node monitoring has to be 1:1, with or without local agents. Software like Zabbix may help. They are not hard to install but takes too many time to get fully configured and you need to know what to monitor and how to interpret. It is Server monitoring each node (could be anything with an IP address). It may have also some autodiscover option, but you have to configure everything.


On Switched network you can't sniff the whole network as many many years ago happened with hubs and/or coaxial Ethernets. Some smart swithches may allow you to configure a Tap or Mirror Port wich forward other ports traffic to a specified. From there you can sniff the traffic on a single device but not much more. You depend fully on the Switch capabilities.



I think that you are looking for the first situation but some kind of software that do "everything" without any configuration at all. Unfortunatelly it doesn't exists.


Take a look to Zabbix, Nagios/Icinga, MRTG, Cacti.


I prefer Zabbix.

---

