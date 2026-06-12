---
title: "[CentOS] Networking woes... &quot;network is unreachable&quot;"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by joeashcraft on 2013-02-27
[SIZE="3"]**[COLOR="DarkOrange"]Problem[/COLOR]**[/SIZE]
Whenever I try to add the default route (with or without the iface specified), I get an error:
```
# route add default gw 192.168.1.254 dev eth1
SIOCADDRT: Network is unreachable
```
I'm able to bring up eth1 via ```
# ifup eth1
``` or ```
# ifconfig eth1 up
``` but [FONT="Courier New"]ifup[/FONT] throws the error above since it tries to add a route; [FONT="Courier New"]ifconfig[/FONT] doesn't give an error since it just brings up the iface. I've done everything short of a reboot. I've restarted the networking service (# service network restart), unplugged and plugged in the cable, unloaded and loaded the driver. I'm stuck.

I can't really upload/paste the contents of files, but I can transcribe from one machine to another. Please don't ask for really long files :-)

[SIZE="3"]**[COLOR="DarkOrange"]System Info[/COLOR]**[/SIZE]
[LIST]
[*]Two wired NICs on two WANs
[*]eth1:
[LIST]
[*]Static IP set via "/etc/sysconfig/network-scripts/ifcfg-eth1": 192.168.1.90
[*]GW is a 2Wire RG (for AT&T Uverse): 192.168.1.254
[*]mask: 255.255.255.0
[/LIST]
[*]eth0:
[LIST]
[*]Static IP set via "/etc/sysconfig/network-scripts/ifcfg-eth0": 192.168.10.100
[*]GW is a DD-WRT router: 192.168.10.1
[*]mask: 255.255.255.0[/LIST][/LIST]


[SIZE="3"]**[COLOR="DarkOrange"]How I Got Here...[/COLOR]**[/SIZE]
A few days ago, I was trying to figure out why my server couldn't get out to the internet. My last effort was to remove all the routes and re-add them with the script that I wrote that runs at startup. So I did ```
# ip route flush table all
``` like a moron and now it's even more broken!

---

