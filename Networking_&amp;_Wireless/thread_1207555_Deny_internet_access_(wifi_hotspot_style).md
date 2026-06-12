---
title: "Deny internet access (wifi hotspot style)"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by burcyril10 on 2009-07-08
Hi there,
Is there a way to deny some users internet access and not others? I have thought of one way - give permitted users an ip address with one subnet and banned users an address another subnet then use iptables to deny everything coming from the banned subnet.

This could work however there are a few flaws; most notably if a person assigns their ip address staticly to the permitted range then they get internet...

My goal here is to have a wifi hotspot thing... connect to the wifi and 'try' to access the internet then get redirected to a web page telling them to register and THEN they get access...I believe a transparent proxy will allow me to redirect, but how can I be sure all the people in the permitted ip range are in fact permitted? I know I can use my DHCP to map MAC addresses to permitted IP ranges but this doesn't solve the problem of staticly assigned ips within the permitted range...

Can you get somthing to check dhcp leases and outgoing ip address when a packet tries to leave? I'm pretty sure ip tables can't do that...

I'm running a very standard ubuntu router/gateway setup (with dhcp, transparent squid, httpd and the lot) net on eth1 and lan on eth2...

Any help would be greatly apreciated!
 - Cyril

---

