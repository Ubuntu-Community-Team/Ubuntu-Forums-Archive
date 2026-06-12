---
title: "Wireless disappeared when I accidently booted with insufficient memory"
date: 2013-05-12
forum: Networking &amp; Wireless
---

### Post by aa4bb on 2013-05-12
Not sure whether this is PowerPC specific or a more general problem, so I'm asking it to a general audience rather than Apple group.

I successfully installed 12.04 on a PowerBook G4 512M 1GHz 15", followed by installing firmware-b43-installer to get the wireless going.

I was exploring adding memory. I took out the memory cards to look at them and replaced them in their sockets. One of the 256M cards wasn't seated properly. When I rebooted, the system came up but was very sluggish, and after messing around a while, discovered the problem was having only 256M of working memory.

I reseated the memory card and the system came up fine with 512M of memory. However, wireless is no long active. I can't figure how to activate it. I think the Airport Extreme card may be turned off, but I don't know how to turn it on.

---

### Post by wildmanne39 on 2013-05-12
*Thread moved to **Networking & Wireless**.*

---

### Post by Hadaka on 2013-05-13
Hi,please open a terminal..ctrl/alt/t
then COPY and paste the following...

```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list all
cat /etc/modules
```
post the output..
thanks.

---

### Post by aa4bb on 2013-05-16
Thank you for your help.

The problems now seem to be more widespread than just networking. I think the best solution is to reinstall from scratch.

---

