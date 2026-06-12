---
title: "tftp, put"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by valros on 2009-11-23
With tftp, I need to 'put' a file to 192.168.1.1, but there's nothing on how to specify the destination. How do I specify the target machine.

Right now I have the following lined up:

tftp
mode binary
rexmt 1
timeout 60
put <file>

---

### Post by valros on 2009-11-23
Ok I think tftp 192.168.1.1 is correct, however it keeps telling me that there is no such file, what directory is it working from?

---

