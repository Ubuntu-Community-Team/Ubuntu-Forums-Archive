---
title: "selective routing"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by davidmaxwaterman on 2011-02-24
Hi,

I want to have my computer connected to both eth0 and wlan0 and to have one as default and route selective hosts/nets through the other.

I have previously done this by having eth0 as default route and adding routes to selected other hosts through wlan0. I was using gnome then, but have since moved to kubuntu and unlike gnome's, the GUI network manager doesn't seem to have this feature.

So, I'm trying to use the command line 'route' command, which I had successfully used in the past. However, now I come to try this method again, I can't seem to get it working.

I tried :

sudo route add -host imap.host.com dev wlan0

and then tried pinging it, but I get 'Destination Host Unreachable'. If I try to traceroute, I get a response from something on the correct network, but the line has '!H' in it, which is clearly not correct.

Any hints?

Max.

SOLUTION: grep -i gateway /var/log/*; and then do 'sudo route add -host imap.host.com gw <gateway> dev wlan0'

---

