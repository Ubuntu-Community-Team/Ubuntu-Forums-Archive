---
title: "ati proprietary fglrx 8.19.10 installed but no 3d"
date: 2005-11-13
forum: Multimedia &amp; Video
---

### Post by basfrank on 2005-11-13
Hi Forum,

I got the proprietary ati fglrx driver 8.18.08 to work. 3d also.
Yesterday I tried the new 8.19.10.
The installation via installer worked fine but there's no 3d support.
Fglrxinfo says the mesa module has been taken for 3d not the ati one.
I have no idea what's wrong with it.

Can you help me?

---

### Post by Zeroedout on 2005-11-13
you're not alone. I get the exact same error. When I do sudo modprobe fglrx i get this error, Operation not permitted. However, I am using a custom kernel, are you using the kernel from the repos, or did you compile it yourself?

---

