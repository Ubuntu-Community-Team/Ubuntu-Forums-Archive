---
title: "X11 forwarding borked"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by Arthemys on 2011-07-20
I'm trying to set up X11 forwarding from my home server running Ubuntu Server 10.10 with OpenSSH_5.5p1 Debian-4ubuntu6

When I try to run anything that needs X I get:
```
cparker@leopard:~$ xeyes 
Error: Can't open display: 
```

In /var/log/auth.log is this:
```
error: Failed to allocate internet-domain X11 display socket.
```

I saw a bug about this but it seemed fairly outdated. [Bug #434799]("https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/434799")

---

