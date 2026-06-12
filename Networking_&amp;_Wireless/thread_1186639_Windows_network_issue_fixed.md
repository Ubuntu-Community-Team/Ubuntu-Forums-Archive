---
title: "Windows network issue fixed"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by jmstern on 2009-06-13
I am not sure how I did this, but after loading some program, I lost the ability to browse Windows network.  I could see the network, but if clicked the icon, got response, 'Unable to browse network'.  frustrating! 

Today I was roaming through the screens in GADMIN-SAMBA -and I noticed the interface address was wrong - 

made the change to 'interfaces = 127.0.0.1/8 192.168.1.1/24' and SHAZAM.
the line had read interfaces = 127.0.0.1/8 192.168.0.0/24

Hopes this helps!

---

### Post by Iowan on 2009-06-14
192.168.1.1 is your router address? (or the Samba server... or both?)
I don't have **gadmin-samba** installed, but I'm curious what file it is uses/modifies.

---

