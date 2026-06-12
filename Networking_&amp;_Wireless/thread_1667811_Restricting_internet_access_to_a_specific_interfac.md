---
title: "Restricting internet access to a specific interface"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by BionicSniper on 2011-01-15
Ok I am trying to get my file/web server up and running but I need some help getting the interfaces configured.

I have 2 NICs, one of which connects to an internet facing facing switch [eth0] and the second connects to my router [eth1]. This is so I can talk to the server from the internet without having to deal with port forwards and I can also have the server in my network.

When I have both plugged in I am able to see my server on my network and go to it's webpage on the internet but the server itself is unable to get on the internet. This sounds like a dns problem but I am unsure of how to fix it.

I have eth1 as the only interface for samba (in smb.conf) but is there a way to do that globally across the system as smb shares is all I want that interface to be able to do.

---

