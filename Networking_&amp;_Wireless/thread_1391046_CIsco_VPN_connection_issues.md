---
title: "CIsco VPN connection issues"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by jongudm on 2010-01-26
I'm trying to get some VPN profiles working on Ubuntu 9.10 that I had been using on a Windows XP system (all of which worked well there).  There are five profiles in all and only two work the way I need them to (with the TSM command line client connecting).  One connects and I can use RDP but the TSM client doesn't connect.  The remaining two don't connect at all, the message that appears is just "Connection failed" (using the client from the network menu that is).

I've tried using the vpnc-connect for the last two and one does connect (enough for SSH but not for TSM) but nothing works with the last one.

Apart from the encryption method and the NAT traversal are there any options that could be changed?

---

### Post by jongudm on 2010-01-27
I forgot the other problem, which is that when connected on the ones that work I have no internet connection on the local machine.  Is that configurable or am I stuck with that?

---

### Post by jongudm on 2010-02-04
I suppose I should mark this as "solved" but in a very dirty way.  I installed the old (2008 version I think) official Cisco client and as annoying as that one is (requiring a recompile after kernel updates) I can now get connected.  So I use the built in GUI for three VPN profiles, vpnc for one and the Cisco client for two...

---

