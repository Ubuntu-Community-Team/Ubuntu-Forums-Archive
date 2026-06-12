---
title: "Ethernet on emachines (e625)"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by cpa on 2010-02-21
Hi,

I have a weird issue with my ethernet on an emachine (e625). It connects perfectly and I can access the internet for a while (from 10sec to 5 min) but after nothing.

When I look to ifconfig, it shows that after a given period, all packets are dropped !

I'm using the default driver (atl1c), as lsmod shows.

I tried wicd instead, but same issue.

Any idea ?

Thanks,
Cp

ps: wireless works perfectly.

---

### Post by cpa on 2010-02-22
I installed a newer version of the driver but I still have the same issue...
Ideas anyone ?

---

### Post by axldavis2012 on 2011-06-07
which version of ubuntu are you using cause some people use older versions

---

### Post by cpa on 2011-06-07
I was using the current version at the time, ie 09.10. The problem was related to the kernel version, in the end.

I don't have access to this machine anymore but hopefully it's fixed in the new versions.

---

