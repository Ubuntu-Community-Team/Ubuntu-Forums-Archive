---
title: "Dial Up Madness!"
date: 2006-02-19
forum: Networking &amp; Wireless
---

### Post by elpollodiablo on 2006-02-19
Hello, 

I subscribed today. I'm a Gentoo user, but I like to spread the penguin OS around. Ubuntu works flawlessy, but dial up is driving me nuts. 

I've been googling for a long time now, and I feel like I need to come up with a solution any time soon. 

Here is my setup: I've installed ubuntu via LAN (I've got a router and blah blah). I need to set up dial up internet becouse the pc's owner uses old school dial up at home. I have plain serial modems all over (from dlink to usr), so the modem detection is not my problem.

Well. The eth0 card is configured statically (IP 192.168.0.20, MASK 255.255.255.0, GW 192.168.0.253). 
This is what I did just before writing here.

1. Unplugged the LAN cable
2. Disabled eth0
3. reboot
4. executed
    route del default gw 192.168.0.253
5. tried connecting with the gnome dialer thing, wvdial and ppp (via pon, poff). 

The results are all the same:
1. The modem talks with my ISP.
2. closest node ip and DNS get detected
3. no way I can ping my DNS and my WAN access node
4. if I issue the route command, it takes AGES to get my prompt back (looks like route is waiting for something before printing the routing table on the screen).

I've also tried with "defaultroute" in /etc/ppp/options. Nothing really changes. 
Would you mind to help me? I'm using ubuntu 5.10.

Thank you for now, 
Michele

---

