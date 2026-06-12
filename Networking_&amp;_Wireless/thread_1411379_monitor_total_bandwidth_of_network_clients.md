---
title: "monitor total bandwidth of network clients"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by mbarak on 2010-02-19
OK, so here's the situation:

My roomates and I share our internet connection in our house.  This connection has a limit which we frequently pass and get billed for it.

I'd like to set up some way of counting how much bandwidth each of us uses so that at the end of the month each one of us will pay only for what we use (after the base amount)

All clients go through the main ubuntu desktop computer, which gets it's internet through the router.
The ubuntu box is the dns/dhcp server (dnsmasq) and serves static IPs for each laptop.

Currently to count the total bandwidth used by each laptop i  use iptables rules:
-A -s laptop1
-A -d laptop1

the problem with this is that this also counts the bandwidth between laptops (ex: file transfers, games, etc) which is obviously not what I want

I tried:
-A -s laptop1 ! -d 192.168.x.0/24
-A -d laptop1 ! -s 192.168.x.0/24

but, that doesn't seem to work :s it doesn't seem to count downloads from the internet

So, I'm asking for help.  Do you know of any programs that will make my life much easier? or do you know what's wrong with my iptables rules? do you know of a better way? any help would be much appreciated.

---

