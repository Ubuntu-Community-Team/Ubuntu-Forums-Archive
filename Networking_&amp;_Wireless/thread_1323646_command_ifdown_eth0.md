---
title: "command ifdown eth0"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by mxmike51 on 2009-11-11
Hi all;

When I script:root@mike-desktop:/home/mike# ifdown eth0

I get: ifdown: interface eth0 not configured

I don't understand what "interface eth0 not configured" is refering to exactly. I have eth0 configured for static IP and it is currently in use. How can it not be configured?

[LEFT]BTW I am using 9.10 all updates installed.

I am writing a script to reset my network connection every 24 hours. When my IP lease expires I lose phone service. All I have to do is reset my network connection and my tele service gets my new IP and my phone works again. So I need a command to reset eth0. So I don't have to do it manually everyday because I am too forgetful lol.

I wish I could set a static IP but I am on a public network and don't have admin privileges. 

Thanks in advance and best regards,

Mike
[/LEFT]

---

### Post by dread22 on 2009-11-11
can you just use
ifconfig eth0 down
instead?

---

### Post by mxmike51 on 2009-11-11
Bingo

That is just what the Doctor ordered!

Thanks a million!

Miike

---

