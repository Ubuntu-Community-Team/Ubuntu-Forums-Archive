---
title: "Plymouth slowing down my boot?"
date: 2011-01-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mc4man on 2011-01-20
Anyway before you deleted your boot chart it showed irqbalance running. Happened to notice that the latest update to irqbalance has disabled it and not offere to configure.
(not sure what the intention there is for either. Being curious reconfigured and enabled oneshot on my p4

---

### Post by MacUntu on 2011-01-20
It might be a misconfiguration on my end, I'll wait for mainline kernels (which will need some time as -rc1 doesn't play nice with some systems/configs). Will have a look into the irqbalance thingy, thanks!

---

### Post by mc4man on 2011-01-20
It took my post a bit of time to register  so I filed a bug on just in case it should be enabled or a configure dialog should pop up
[https://bugs.launchpad.net/ubuntu/+source/irqbalance/+bug/705429](https://bugs.launchpad.net/ubuntu/+source/irqbalance/+bug/705429)

---

### Post by mc4man on 2011-01-27
Interesting that this became my thread somehow, anyway - 
the irqbalance package was broken, has been fixed and should now default configure as
irqbalance enabled  w/ oneshot disabled

Don't quite understand the oneshot option, whether there is a value to be being enabled on some hardware or not. Have left oneshot enabled on p4 anyway..

---

