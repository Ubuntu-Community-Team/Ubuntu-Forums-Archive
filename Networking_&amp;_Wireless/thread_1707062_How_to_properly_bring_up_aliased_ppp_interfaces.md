---
title: "How to properly bring up aliased ppp interfaces?"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by dbv on 2011-03-14
Hi,

I have configured ppp0 (DSL connection) and it comes up properly with the machine and with 'pon'. I also configured 2 aliased ppp0 interfaces in /etc/network/interfaces like this (I'm listing just one as an example):

auto ppp0:0
iface ppp0:0 inet static
address 206.x.y.z
netmask 255.255.255.252
broadcast 206.x.y.z
network 206.x.y.z

After ppp0 comes up, if I do 'ifup ppp0:0', ppp0:0 comes up just fine. How do I make it come up automatically with ppp0? I suppose I could just put in a script in /etc/network/if-up.d/ that'll execute 'ifup ppp0:0' and 'ifup ppp0:1' but is this the preferred way of doing this?

Thanks.

---

### Post by dbv on 2011-03-18
It's solved, kind of. I'll leave a note here in case someone else has the same problem. I found this document very helpful:

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

After configuring ppp0, add scripts in /etc/ppp/ip-up.d and /etc/ppp/ip-down.d to bring ppp0:0 up or down. Make sure you take ppp0:0 down before trying to bring it up (so do ifdown ppp0:0 before doing ifup ppp0:0 in ip-up.d). The section in /etc/network/interfaces I wrote above is needed as well.

---

