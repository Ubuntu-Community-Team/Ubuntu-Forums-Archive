---
title: "I thought I was getting the hang of IPTables...."
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by DragonDon on 2010-09-22
Just when I thought I was getting it, iptbles throws me a curveball.

Ok, so I've been working with iptables to get the right ports open to use a voip softphone but wasn't getting any audio.  I took my router out of the equation and plugged my system into my cable-modem directly.  I checked iptables and whamo, there are soo many settings/rules/chains that I am completely overwhelmed and no idea where they are coming from.

I had PeerGuardian Linux installed so I thought maybe that was mucking with the chains.  I removed it but still they are there.

I could use some help from all you wonderful iptables-gurus to understand what is happening.

Here is what is listed for iptables -L

[http://paste.ubuntu.com/498906/](http://paste.ubuntu.com/498906/)

This is my iptables file that I created:

[http://paste.ubuntu.com/498615/](http://paste.ubuntu.com/498615/)

Here is what iptables -L looked like earlier today when I was going through my router:

[http://paste.ubuntu.com/498617/](http://paste.ubuntu.com/498617/)

TIA.

Don

---

