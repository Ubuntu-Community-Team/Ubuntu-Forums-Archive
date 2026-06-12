---
title: "automatic network profiling / automatic dhcp at boot"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by jb.transfer on 2011-11-30
Hi all,

have special network issue for which I couldn't find a solution.

I want to check at boot time if a network cable is plugged and
if DCHP is running on the subnet.

In brief terms which cases I am thinking of at boot time.

Check if a network cable is plugged:

IFPLUGGED NO: Start a DHCP Server on the booting maschine
IFPLUGGED YES: Check if there is a DHCP Server running.
                                   IFDHCP configure the maschine as dhcp client
                                   IFNODHCP: start DHCP Server on that maschine

I've found IFPLUGD but I am not sure if this is the proper candidate for
this case.

Actually the system should be aware of automatically detecting  if
a cable is plugged or not and should start the dhcp server automatically
if no dhcp server is running and/or no cable is plugged in. 

I hope these thoughts are written comprehensible.

Cheerio jb

---

### Post by jb.transfer on 2011-12-02
Hi again,

after talking to some people I realized that in case of a plugged cable
my linux box shouldnt start a dhcp server automatically cause there
could be a dhcp server which doesn't respond to unknown hosts
due to security policies.

I will rewrite the request a little later or should I close the post and start
a new one?

Thx for opinions

jb

---

### Post by jb.transfer on 2012-03-05
Hi there,

sorry for the long delay.

I found the mii-tool which is telling me if a cable is plugged in.

Cheerio jb

---

