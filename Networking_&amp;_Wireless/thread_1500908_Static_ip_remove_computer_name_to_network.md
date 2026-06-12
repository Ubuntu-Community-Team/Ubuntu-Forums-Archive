---
title: "Static ip remove computer name to network"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by rt-2 on 2010-06-03
Hi,
I wanted to have a static local IP on my server, so i used : [this Tutorial]("http://codesnippets.joyent.com/posts/show/319")

But on my 192*.168.1.1, there's a place where ic an see all devices, and before, the displayed name was "STASH" and with the update i put, it'S now "--", but i'd like to keep my old one..

Thank you...

---

### Post by Iowan on 2010-06-03
I like to let my DHCP server assign a static lease to my servers, printers, etc. Because I use DNSMasq, the DHCP machines can be reached by their hostnames.

---

### Post by rt-2 on 2010-06-04
yeah but since i applied that code... my hostname is null... :(

---

