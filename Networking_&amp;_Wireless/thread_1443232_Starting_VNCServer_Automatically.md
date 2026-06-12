---
title: "Starting VNCServer Automatically"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by Muhnamana on 2010-03-30
So I just installed VNCServer on my Ubuntu box. I've tested the connection on my Windows box and connect fine.

If I were to restart Ubuntu, would the VNCServer start automatically? If not, how would I do this?

---

### Post by Iowan on 2010-03-31
I haven't (yet) used VNCServer (but I'll provide a BUMP, at least). Is the machine a server - or (more directly) controlled by Network Manager? (Yes, it could be both if the server has a desktop.) Network Manager doesn't initialize interfaces until login, whereas */etc/network/interfaces* does. The next thing would be to check some of the */etc/rcX.d* directories to see if they start VNC. I'm not sure how to check "services" on newer releases (or if servers use it).

---

