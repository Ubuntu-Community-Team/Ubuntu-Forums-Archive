---
title: "wireless switch"
date: 2012-08-04
forum: Networking &amp; Wireless
---

### Post by antobbo on 2012-08-04
HI there, I have another problem with the wireless. Basically I have network manager installed and my wireless connection enabled. If I disable it from network manager, I cannot enable it anymore no matter what I do, unless I log out from ubuntu, boot in windows 7 and toggle a few times the wireless there and log back in ubuntu 12.04
Is there a solution to that? I was told that it could be due to power, any idea?
thanks

---

### Post by praseodym on 2012-08-04
Hi,

what kind of computer is it? Please show also the outputs of

```
lsmod
rfkill list
```
Tried a

```
sudo rfkill unblock all
```

when it is disabled?

---

