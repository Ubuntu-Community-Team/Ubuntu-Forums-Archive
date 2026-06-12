---
title: "Networking Issues (DNS?)"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by DoctorZettabyte on 2009-07-27
Hey there, everyone. I'm new to Ubuntu/Linux (Jaunty Jackalope, fresh install as of Saturday evening / Sunday morning), and I'm trying to learn more without switching computers every ten minutes without rebooting/moving from desk to floor.

The story so far:

I'm learning as I go here, and I've been able to get a connection to my network "3LB0W5repeat", which is a repeater network / bridge to the main, aptly named "3LB0W5". I cannot connect directly to 3LB0W5 -- it just bounces me back to the repeater. I think everything checks out, but I can't get a line to anything on the network, or outside of it. The router is 192.168.0.7, I've set myself up on 192.168.0.42 (relatively far away from anything in use :-P ). I'm not much use for networking, so I set it up with "manual" configuration, with the netmask 255.255.255.0, and the two DNS servers, 151.168.0.38, and 199.245.32.43.

My questions now:
Is this a DNS issue as I originally thought? 

Jaunty says I'm connected, but I lose it every few minutes, only to pick it back up again. Vista Home 64 could remain connected through brick and lead, but Ubuntu will say "now", then "two minutes ago", then "five minutes ago", then "now" again -- is this normal?

What is DHCP? My router says it is not enabled -- do I need to worry about it?

"Routes"? If I could get an explanation of where to where they're going (and what address should I put in the first box? [ is it a "if I'm on this address then go this way" deal? ] ), that'd be excellent.

I can't ping anything but myself, despite being connected. Not even the router.

Everything else checks out according to what I've read, which was more or less [this]("https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html"), with the exception of:
[INDENT]lshw -C network will not say anything about wireless, other than that everything else is disabled. I'll take it that this is fine, considering I can connect to the network.

Who's router is "our" router, or is that a typo for "your"? How do I boot with pci=noacpi, should the need arise?

I get a lot of "no such device"s when I try to run dhclient looking for 3LB0W5. Should I be worried? (wmaster0 says that I have an unknown hardware address type 801?)

I can't ping anything, but resolv.conf shows me the two DNS servers I put in earlier.


[/INDENT]Any help (in layman's terms :-P ) would be much appreciated! Thanks so much in advance, I know it's a lot to slog through! :-D

-DocZetta

---

