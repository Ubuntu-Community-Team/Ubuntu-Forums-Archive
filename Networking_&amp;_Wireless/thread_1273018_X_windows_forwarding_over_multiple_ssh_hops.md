---
title: "X windows forwarding over multiple ssh hops"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by Zxaos on 2009-09-22
Hi folks, I'm having a some trouble performing X forwarding over multiple ssh hops.

The setup that I'm trying to accomplish is:
local machine(A) -> gateway machine(B) -> target machine(C)

B and C are on the same network but C doesn't have WAN access. I've successfully used X forwarding from A to B, and (while I was on the LAN with C) from A to C.

When I'm trying to do A->B->C from the WAN, though, I can't get X forwarding to work. Does anyone know how to get it to go?

---

### Post by sunjith on 2009-10-06
Try this:

On A:
```
**ssh** -f -l user_on_B -N -L 9999:C:22 B
ssh -p 9999 -X -Y -l user_on_C localhost
```You must be able to ssh from A to B and then to C successfully in order for this to work. For example, if C is not on known_host list of B, this would give error: "administratively prohibited: open failed".

---

