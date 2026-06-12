---
title: "Iptables port forwarding"
date: 2012-03-02
forum: Networking &amp; Wireless
---

### Post by NamelessHero on 2012-03-02
Hello, could someone please share knowledge?
I set up internet sharing, using old PC with ubuntu 10.04 system.
eth0 is used for internet access, and eth1 for sharing internet, i set up eth1 as gateway 192.168.0.1 and pc connected to ubuntu system has 192.168.0.2.

But now i can't figure out how to port forward, first i want to forward port 16000 udp to 192.168.0.2.

Here are the commands that i would use:

```
-A INPUT -i eth0 -p udp -m udp --dport 16000 -j ACCEPT
-A PREROUTING -t nat -i eth0 -p udp --dport 16000 -j DNAT --to 192.168.0.2:16000
```

But the problem is, i don't know where to place it, i tried placing it in /etc/rc.local with no success, so could someone tell me all important iptable files and description of each (with /etc/... directories please).

And one more thing, what would be commands to first block all traffic and then add seperate IPTABLE rules to unblock necessary ports, and where to add it.

Please, help.. i see that i can't learn this all by myself, this would be beneficial for others too.

---

### Post by Phoenixxl on 2012-03-02
Maybe not a straight answer , but I've always used shorewall in these situations. It's a great step between iptables and the admin , it has easy maintenance and makes configuration easy.

port forwarding rules can be set up in /etc/shorewall/rules

and would look like this:
#UDP and TCP port 49000 to a bridge called mysub to address 192.168.1.211

DNAT             net             mysub:192.168.1.211:49000  tcp       49000
DNAT             net             mysub:192.168.1.211:49000  udp       49000

to install:
sudo aptitude shorewall install


A configuration for a 2 nic system can be found in

/usr/share/doc/shorewall/examples

once installed.

Setup info:
[http://www.shorewall.net/two-interface.htm](http://www.shorewall.net/two-interface.htm)

Good luck.

---

### Post by NamelessHero on 2012-03-02
Thanks for info, i see that shorewall is pretty good tool, i will defilinely try it. However i really want to learn configure iptables in native way, so i'm still waiting for more information on this subject.

---

### Post by NamelessHero on 2012-03-02
Please, someone share some knowledge.

---

