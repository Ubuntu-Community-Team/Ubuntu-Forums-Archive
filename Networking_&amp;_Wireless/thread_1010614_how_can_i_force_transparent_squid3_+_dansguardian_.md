---
title: "how can i force transparent squid3 + dansguardian + firestarter"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by Dibhala on 2008-12-13
Firstly hello everyone.
Secondly I need a hand with squid3 + dansguardian on ubuntu 8.10
I've been searching for solution, but I just suck with iptables.

I got dansguardian running (default config: listening on incoming 8080, working on 3128 , squid3 (same 3128 listening on 80). I used firestarter to route traffic between LAN<->internet.
Eth0 gets IP from router by dhcp, eth1 is configured to 172.16.0.0/24

Afair when I manually configured firefox on all hosts, to use ubuntu's IP and port 8080, mature content was filtered (at least dansguardian worked, don't know if squid did anything).

The problem is, that I would like to filter transparently all content going from LAN hosts -> through dansguardian -> squid.
I tried with couple iptables entries which I found, looking for DG configuration, but those didn't work for me.

Could anyone give me a solution how to configure squid3 + DG +firestarter to work transparently ? I ran out of ideas.
Maybe there's a program with GUI for this ?
I just don't know how to create working iptables entry to route all the ongoing traffic to/from inet through dansguardian.


ps. If I forgot to add any information, although I think I put all needed info, just mention what info should I add.

This is the last place I can search for help :/

---

