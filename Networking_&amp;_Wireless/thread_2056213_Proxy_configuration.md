---
title: "Proxy configuration"
date: 2012-09-11
forum: Networking &amp; Wireless
---

### Post by geoam on 2012-09-11
Hello,

I'm from Romania, and I'm new to your community.
Normally I do not write into forums because any thing can be found on the internet but I'm a little stuck with a problem.

In the network I work, there is a proxy server (10.1.1.1) used to access the internet. So I use Applications --> System Tools --> System Settings --> Network --> Network Proxy for my configuration.

Cli tools ignore this so I use "set http_proxy=10.1.1.1" and check with env.

But still there are some tools (e.g. telnet) that won't use the proxy.
So is it possible to configure the proxy at a lower level (so that I don't have to configure the proxy at 5 different places) for example with iptables?
I don't really have a clue about iptables put the following was my approach:

sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to-destination 10.1.1.1:3128

This should redirect all traffic with dest port 80 to 10.1.1.1:3128. But it doesn't work.

sudo iptables --list also doesn't show any rules.

Can you help me with this?


Thank's a lot in advance!

---

### Post by geoam on 2012-09-11
Finally did it...

iptables --table nat -A OUTPUT -p tcp --dport 80 --jump DNAT --to-destination 10.1.1.1:3128

The PREROUTING chain did not exist... Why? - I don't know. Maybe someone still can explain it.

---

