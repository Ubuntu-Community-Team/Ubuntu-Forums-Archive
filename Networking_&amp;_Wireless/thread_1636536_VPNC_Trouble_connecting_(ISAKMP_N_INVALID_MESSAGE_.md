---
title: "VPNC Trouble connecting: (ISAKMP_N_INVALID_MESSAGE_ID)(9)"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by clrg on 2010-12-03
Hi there!

When I try to connect to my company's VPN using the Cisco VPN client, I get a kernel panic. Please don't suggest I should Cisco's client, it only works with Kernels older than 2.6.24 (I have 2.6.35).

So I use vpnc. The error message is:

> 
$ sudo vpnc
[sudo] password for phirt: 
Enter password for [email]user@group@fubar.net[/email]: 
received notice of type  (ISAKMP_N_NO_PROPOSAL_CHOSEN)(14), giving up
vpnc: quick mode response rejected:  (ISAKMP_N_INVALID_MESSAGE_ID)(9)
this means the concentrator did not like what we had to offer.
Possible reasons are:
  * concentrator configured to require a firewall
     this locks out even Cisco clients on any platform except windows
     which is an obvious security improvement. There is no workaround (yet).
  * concentrator configured to require IP compression
     this is not yet supported by vpnc.
     Note: the Cisco Concentrator Documentation recommends against using
     compression, except on low-bandwith (read: ISDN) links, because it
     uses much CPU-resources on the concentrator



I already asked my company's IT support about it, but they told me they only support M$ XP. How convenient.

Concentrator compression is not force-enabled, I checked that with another laptop running 8.04 (the cisco vpn client works just fine there).

I'd greatly appreciate your help, since I have no idea what to do here.

Thanks for reading & answering
clrg

---

### Post by clrg on 2010-12-19
Boing.

---

### Post by clrg on 2010-12-23
Bump.

---

### Post by clrg on 2010-12-27
Ding. (Am I allowed to push it three times in a row?)

---

