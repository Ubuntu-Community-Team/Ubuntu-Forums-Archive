---
title: "iptables - route issues"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by Pedlar on 2009-05-13
Ok, so to be most thorough as possible, my network internet runs off a Verizon EVDO, the USB727, I have 2 Linux computers running Ubuntu, the one I'm on, and my Server, my Server is running Ubuntu 8.04 the way my network is setup is like:

[COLOR="White"].........[/COLOR]Verizon EVDO(connected using WvDial)
[COLOR="White"]...................[/COLOR](ppp0)
[COLOR="White"].....................[/COLOR]|
[COLOR="White"]...............[/COLOR]Ubuntu 8.04 Server
[COLOR="White"].............[/COLOR](Connected Via eth0)
[COLOR="White"].....................[/COLOR]|
[COLOR="White"]..[/COLOR]D-LINK Router, DHCP Disabled, Connected to LAN Port, not WAN, so turned into wireless HUB 
[COLOR="White"].........[/COLOR]/[COLOR="White"]......................[/COLOR]\[COLOR="White"]........................[/COLOR]\
[COLOR="White"].........[/COLOR]/[COLOR="White"]......................[/COLOR]\[COLOR="White"].........................[/COLOR]\
  Ubuntu 8.04(Me)[COLOR="White"].....[/COLOR]Windows XP[COLOR="White"].....[/COLOR]Windows Vista

So, all of it works, to an extint, I have no problems with the Windows machines, but my Linux machine keeps pushing its interal IP over the ppp0 device, causing Verizon to shut me off.

My iptables script looks like:
```
iptables -t nat -A POSTROUTING -o ppp0 -s 192.168.10.0/24 -j MASQUERADE
iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 3074 -j DNAT --to-destination 192.168.10.2
iptables -t nat -A PREROUTING -i ppp0 -p udp -m multiport --dports 88,3074 -j DNAT --to-destination 192.168.10.2
iptables -A FORWARD -i ppp0 -d 192.168.10.2 -p tcp --dport 3074 -j ACCEPT
iptables -A FORWARD -i ppp0 -d 192.168.10.2 -p udp -m multiport --dports 88,3074 -j ACCEPT

```

my eth0 IP is Static set to 192.168.10.2

but, Sometimes it does this, sometimes not, like right now, my internal hasn't shown up at all, and then sometimes itll show up in succession, and shut me down. the tcpdump output for when it happens looks like:
```

09:56:07.634677 IP pedlar-desktop.local.35656 > gw-in-f100.google.com.www: S 2228317669:2228317669(0) win 5840 <mss 1460,sackOK,timestamp 51916693 0,nop,wscale 5>
```

and like I said, sometimes it dosn't do it, sometimes it does, its strange, and has me stumped.

---

### Post by Pedlar on 2009-05-13
Also, I'm not sure if this will be irrelevant to this issue, both computers are running Samba Server. Though like I said, prolly isn't messing anything up, but just another peice of the entire setup

---

### Post by Pedlar on 2009-05-21
Noone ever have this problem before?

---

