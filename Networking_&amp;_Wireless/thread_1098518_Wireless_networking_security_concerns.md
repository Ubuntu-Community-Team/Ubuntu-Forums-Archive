---
title: "Wireless networking security concerns"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by aquavitae on 2009-03-17
I've just installed ubuntu 8.10 on a friend's laptop, and he's mildly paranoid about security (the main reason he moved away from windows).  He's worried about the safety of his internet traffic when he's using a wireless hotspot and, in windows, he was using HotSpot Shield, which is a VPN. I'm not really convinced of how secure this is, but I don't know enough about it to be able to comment.

Does anyone else know anything about using a VPN for secirity in this way, and if its a good idea then what should I install on linux?

---

### Post by 3rdalbum on 2009-03-17
A VPN will encrypt internet traffic, so yes it is secure in-between the client and the VPN server. If the makers of HotSpot Shield wanted to though, they could snoop on his traffic as it passes unencrypted through their server.

I'm not familiar with that software, but it should be possible to connect to the same VPN, as long as it is a standard VPN and doesn't use some kind of weird proprietary protocol.

I don't know of any packages that can decrypt internet traffic without an actual VPN or SSH. I'm sure I've heard something being mentioned months ago but I can't find it again. As Australia is going to introduce internet censorship soon I'd be very interested to find out.

---

### Post by aquavitae on 2009-03-17
Thanks for the reply.  I'll try to explain this to him and do a bit of research on Hotspot Shield - I don't know much about it either.  I assume OpenVPN would be the best option in linux?

---

