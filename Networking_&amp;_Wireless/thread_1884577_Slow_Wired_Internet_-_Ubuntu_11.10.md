---
title: "Slow Wired Internet - Ubuntu 11.10"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by dramos on 2011-11-21
Hi,

I have dual boot set up and internet is slower in Ubuntu. When I test the speed in Windows I get around 12mb/s. When I test in Ubuntu I get around 3mb/s, somethings as low as 1mb/s.

I looked around and saw some similar posts but did not help me. Here is some info that others with similar problems were asked to provide.

lspci -nnk | grep -iA2 net
 
```

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169


```


Any help, will is appreciated.

Thanks in advance.

---

### Post by dramos on 2011-11-21
I found what seems to be a solution. Some other users with the same LAN adapter had similar problem. They fixed it by turning off the computer and unplugging from the power supply for a few minutes.

It worked for me.

---

### Post by BornOle on 2011-11-23
Of all the ridiculous things ... this solution worked for me, too. Thanks to the OP!

---

### Post by Filiberke on 2011-12-31
thanks!! it solved the same problem for me too!! I'm feeling lucky to have clicked this thread, who knows what time i would've wasted searching for a more complicated solution...

thx again!

---

