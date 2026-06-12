---
title: "Network WAN access problem (Inten 82567)"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by bepe on 2011-09-27
I have a problem getting 11.04 desktop connect to WAN. This is the configuration:

- latest Ubuntu 11.04.3
- installed on a Lenovo desktop
- Intel 82567LM-3 Gigabit Network

The machine runs in a LAN behind a Netgear FVX538 router setup as NAT.

This is the problem in detail:
- LAN connections do work, I can ping and reach other machines within the LAN, as well as the router
- **The Problem: there is no response to pings to outside (WAN) adresses (and of course other apps like Firefox can't connect to outside adresses either)**
- it is not a DNS problem, adresses are correctly resolved, ping would not even work with hardcoded WAN IPs 

The integrity of the hardware and the router setup has just been verified by installing Windows 7 on this very machine and testing WAN access successfully. (The machine is behind a Netgear FVX538 router, which works fine with other Ubuntu clients in our network.)

BTW, same problem when going back to 10.04.

Ifconig results look "clean" (at least compared to what I get on other machines in network).

Other Ubuntu machines (different hardware thou) work well with the system default settings.

Can I exclude a configuration issue at this point? Or is this an e1000e driver problem? If so, what to do? Any other idea?

---

### Post by bepe on 2011-09-29
I should add that I deactivated IPv6 to make sure its not related to the IPv6 issues reported in the forum. Still same problem.

No one around who has a clue or a similar problem? (I have edited my orginal post - hopefully it has become clearer.)

Please - any help or hint appreciated!

---

