---
title: "Driver 8139cp, 8139too"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by ICEB3AR on 2010-11-19
Hey there

I found some posts on the Problem, but the solutions I have tried did not succeed and I'm not sure, if I have made something wrong!
The Problem is that I get the following:

```

#: dmesg | grep 8139
[   23.322063] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   23.526403] 8139cp 0000:01:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   23.526470] 8139cp 0000:01:08.0: Try the "8139too" driver instead.
[   23.526534] 8139cp 0000:01:0a.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   23.526592] 8139cp 0000:01:0a.0: Try the "8139too" driver instead.
[   23.528700] 8139too Fast Ethernet driver 0.9.28
[   24.924789] eth1: RealTek RTL8139 at 0xe800, 00:50:bf:55:5e:b5, IRQ 20
[   24.924791] eth1:  Identified 8139 chip type 'RTL-8139C'
[   24.925530] eth2: RealTek RTL8139 at 0xe400, 00:50:bf:55:5e:bc, IRQ 21
[   24.925532] eth2:  Identified 8139 chip type 'RTL-8139C'

```The error above with Try the 8139too driver instead also appears on startup. I have tried to set 8139cp on blacklist:
```
/etc/modprobe.d/blacklist
...
blacklist 8139cp

```But as you see above the driver is still loaded and the error appears. So what can I do to fix this problem?

Best regards

---

### Post by ICEB3AR on 2010-11-23
Bump

---

### Post by ICEB3AR on 2010-11-26
```
modprobe -r 8139cp
```

doesn't work either.

Anyone has an idea?

---

### Post by chili555 on 2010-11-26
I have this issue on one of my desktops. I tried the blacklist method with no change. However, is it really a problem? Do you have a problem connecting? Are speeds slow?

---

### Post by ICEB3AR on 2010-11-26
It seem to work fine, but It shouldn't display that error especially because the problem is known for a long time. And I personly don't like errors which came up on a working setup.

But okay thanks for your answer =)

---

