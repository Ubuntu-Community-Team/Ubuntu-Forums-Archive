---
title: "Need help with socat"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by jammer10000 on 2009-11-21
Not sure if this is the right place, but running 9.10 64bit and attempting to use socat. Not finding a forum for it, I'd thought I'd try here... Here is what I'm trying to do:

socat pty,link=/dev/vttyS0,raw,echo=0,waitslave tcp:192.168.255.106:54321

Seems to work great, but it always creates the virtual serial port vttyS0 with root.root... Now, my apps cant open the port... Tried to chgrp, chown etc, with no luck... Even tried to set user and group within the socat command and no dice... I'd just like to have the virtual serial port opened as root.dialup and I think all will be ok, but am stumped... If I run everything as root, works great... Don't want to do that though... Any help or pointers would be greatly appreciated....


Thanks!

---

