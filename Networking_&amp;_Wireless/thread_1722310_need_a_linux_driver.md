---
title: "need a linux driver"
date: 2011-04-05
forum: Networking &amp; Wireless
---

### Post by bbish55 on 2011-04-05
Hello!

I recently loaded ubuntu 10.10 onto my wife's HP DV6409WM laptop. The wireless does not work! This unit has an nvidia mcp51 controller. I have downloaded a host of drivers from hp support, etc. using "Windows Wireless Drivers" feature to no avail. Some drivers come up valid, some do not, makes no difference. No wireless action to be had. Thoughts? Anyone? 

I like the basic layout and function of ubuntu and would like to give it a go, but the wireless must work. Otherwise. . .

Thanks!

---

### Post by chili555 on 2011-04-05
Welcome to the party! First, let's verify what wireless card you have. Please open Applications > Accessories > Terminal and run and post:```
lspci -nn
ndiswrapper -l
```Thanks.

---

### Post by bbish55 on 2011-04-06
I think my wireless card is dead! The computer doesn't recognize it with either the lspci -nn, through the device manager, nothing. I have a broadcom bcm94311mcg and I installed the bcmwl6.inf and it states "Hardware Present: no"

---

