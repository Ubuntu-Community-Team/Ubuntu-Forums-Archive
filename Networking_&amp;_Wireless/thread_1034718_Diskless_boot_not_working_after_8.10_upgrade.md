---
title: "Diskless boot not working after 8.10 upgrade"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by obrienmd on 2009-01-09
Background:

-my entire network is running off a 24-port dell powerconnect 5224 gigE switch

-my DHCP server is a WRT54G running dd-wrt, pointing PXE netboot clients to my netboot server for tftp

-my netboot server is Ubuntu 8.10, serving tftp and nfs for client root once initially booted

-my netboot clients are P1-AH2 computers using the onboard NIC (although I've tried with various others including e1000 nics)

-when the clients were on Ubuntu 7.10 (2.6.22), they net booted just fine

-after upgrading to Ubuntu 8.10 (2.6.27), they give me the following once the kernel is loaded:
--
IP-Config: no response after 60 secs - giving up
/init: line 1: can't open /tmp/net-eth0.conf
kernel panic - not syncing: attempted to kill init!
--
and everything stops.

-strangely enough, when I put a 10/100 switch in between the big GigE switch and my netboot clients, everything comes up just dandy, but the computers are almost useless for my needs (i/o intensive)

-I've replaced the NICs in my clients with multiple different adapters (e1000, other well-supported hardware), no dice @ 1000bT

---

### Post by obrienmd on 2009-01-09
Hrm... new bit of info.  Even when using the 100bt switch work-around, when I restart the computer via software (ie: sudo reboot) it has the problem again.  However, once I hard-reset the computer after the problem, it starts up fine when going through the 100bt switch.

---

