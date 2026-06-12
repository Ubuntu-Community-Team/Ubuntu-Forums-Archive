---
title: "connection manager with bonding and automatic vpnc?"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by jonaskoelker on 2009-05-13
Hi all.

I'm looking for some network connection management software for my laptop which fits my needs.

At home, I use both wired and wireless (WPA2), and sshfs.  I want to use bonding, such that the ssh connection doesn't drop when I plug and unplug the cable, but still get the faster-than-wireless speed.

At my university, I use wireless (no encryption) and I need to have a vpn daemon running.

All other places (so far) are easy: I use only wireless, or only wired, with no need to run anything on connect or disconnect.

I want some network connection management software that connects me with no interaction on my part; whenever it's disconnected and sees a network it knows about, it should connect straight away.

Is there software which (1) supports bonding; and (2) lets me run hooks whenever I connect to a new network (including "no network")?

NetworkManager, wicd and connman all fail at bonding, AFAICT.  Google has no hits for "lxnm bonding".  My own scripts for detecting when I connect and disconnect to networks fail :(

---

