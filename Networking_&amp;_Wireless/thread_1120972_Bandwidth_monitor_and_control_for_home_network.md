---
title: "Bandwidth monitor and control for home network"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by Sastopher on 2009-04-09
I use an Ubuntu machine as a router for a home network shared by a bunch of gamers who are constantly struggling to find a happy medium between download/torrents and gaming.  What we want is gaming (and peripherals, such as ventrilo, etc.) to have a streamlined path, low-bandwidth tasks like web browsing and IM-ing allowed to function as normal, and any kind of obtrusive high-bandwidth downloads or torrents silenced for the duration of the playing.

I'm currently using Shoreline Firewall through webmin to configure my router's settings, but I have enough knowledge of iptables that I can understand and make changes directly if I need to.

First off, ideally someone could point me to some QoS settings that deal with this sort of network (putting any kind of large bandwidth hogs at the bottom of the list, and/or prioritizing connections by port i.e. the gaming ports used).  I got my feet wet with this a while back but wasn't able to find anything that really did the trick.  What I have now is ToS set up through webmin/shorewall that denote torrent ports that get forwarded as minimize-cost, and all gaming ports we use set as minimize-delay.  I couldn't say if this has helped, as torrenting on the network while playing a game such as Warcraft 3 is certainly not a transparent process.

My main machine is a Windows box, PuTTY-ed into the router via SSH.  I often have iftop running to keep my thumb on the pulse of our connection so I can debug what's happening to our network when people start dropping out of my game for whatever reason. At this point, I'd throw out something like the following to surgically cut out the local, offending computer:

```
iptables -I loc2net 1 -s <offenders_ip> -j DROP
```
(loc2net i.e. local to network is one of the chains webmin has set up through its configuration, and merely adding this rule through webmin or through -A just puts it behind ACCEPT/established,related and doesn't immediately change anything)

I guess I could improve the surgery, making so it allows basic functions under a restricted rate, and composing all this in a script but... There has GOT to be a better utility for all of this.  Is there any sort of console/TTY app that measures and controls bandwidth movement on a LAN?  In an ideal world, it might even have a little real-time ASCII graph and some numbers.

I know this is asking a lot, but I can't imagine this is that esoteric of a setup amongst linux users.  Does anyone have some personal recommendations that might help me out?

Ideal: low-maintenance system that gives bandwidth to torrents/DLs when that's all that's running, but makes them transparent or cuts them off completely when anyone on the zone is playing a game.

Acceptable: a better method of actively watching bandwidth flow on my network and then I would manually control the flow to adjust to our current needs.

Thanks a ton guys, if you could help me out with this it would solve a problem I've been slowly toiling over for months.

---

