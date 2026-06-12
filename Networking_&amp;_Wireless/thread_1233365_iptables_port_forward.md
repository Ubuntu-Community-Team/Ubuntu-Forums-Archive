---
title: "iptables port forward?"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by Rogmatic on 2009-08-06
After many hours of research and trial and error, I finally found a way to forward the incoming wireless signal (from my router) on my Ubuntu laptop (I'll call it Polaris) to a wired connection to my Vista desktop (Betelgeuse) using this guide:
[http://ubuntuforums.org/showthread.php?p=6060607](http://ubuntuforums.org/showthread.php?p=6060607)
I have working Internet access.

Now, I need to properly configure my BitTorrent software on Betelgeuse and have no idea how to get the port forwarded properly.  On my router config page, it shows both Polaris and Betelgeuse as attached devices  (although Betelgeuse might just be showing because it has wireless capability, even though I disabled it) [EDIT: Yeah, turns out Betelgeuse is not an attached device, according to my router.  When I saw it there it was leftover info from a previous wireless connection.]  I tried forwarding a port to Polaris, and to Betelgeuse with no luck.  I'm wondering if I have to do some kinda port forwarding setup on Polaris using iptables.

My iptabls rules are:
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth1 -j MASQUERADE

I have --no-- idea how iptables works, so a detailed description of what needs to be done would be greatly appreciated.
EDIT: Solved. Set up a static route to Betelgeuse in my router config.

---

