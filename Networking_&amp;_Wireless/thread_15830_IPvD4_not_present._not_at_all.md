---
title: "IPvD4 not present. not at all"
date: 2005-02-17
forum: Networking &amp; Wireless
---

### Post by ganatronic on 2005-02-17
edit: I've been trying to change the title of this post, since it originally wasn't accurate (and overly dramatic, what with the repetition and all). I think I'm just going to give Hoary a try, and actually plug in the lan card to get whatever updates/send whatever information to my router. My computer, so far, has been completely wireless. And for whatever reason it's not getting everything done. If I could delete this post I would, since I don't think anyone can help me with it. Right now I'm thinking my /etc/network/interfaces file doesn't have all the info it needs. but, whatever. Gonna check out Hoary, gonna have me some fun.  


Simply put (because it's late ;p):

My network manager is not at all recognizing an Inet4 address. IPvD6 is there all right.  But under network settings everything is part of an ip6 type. Same thing under ifconfig (obviously). I can assign an inet address under ifconfig with "ifconfig ra0 192.168.11.9 netmask 255.255.255.0", but that only puts them under a plain inet (without a number after it -- especially not a 4, the number I'm really hunting for.

So here's an ifconfig log:
ra0 Link encap:Ethernet HWaddr 00:11:09:0B:E4:9B  
inet6 addr: fe80::211:9ff:fe0b:e49b/64 Scope:Link  
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1  
RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
TX packets:3454 errors:0 dropped:0 overruns:0 carrier:0  
collisions:0 txqueuelen:1000  
RX bytes:0 (0.0 b) TX bytes:139557 (136.2 KiB)  
Interrupt:11 Base address:0x5000

this one is from before I attempted to assign ip's through ifconfig (sorry, I don't have one from after. I have to copy it onto my usb drive and then move it over to this computer - since I c'not get on the 'net from my ubuntu comp. But it's not that much more exciting). It will ping my own ip after I enter it with ifconfig, so I know the card is at least working.

wlan card is a ralink rt2500. I built the drivers for it, and everything on that part seems to be right (although there's a chance, of course, that they aren't).

When I use a dhcp client it will not find any networks. Although I know there are two in range.



Anybody know what gives? Am I missing an application? I've been trying to figure this out for a few days, and have tried a lot of things. This seems to be at the base of it.

---

