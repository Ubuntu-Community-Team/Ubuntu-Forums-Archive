---
title: "Wireless does not reconnect after suspend/standby rtl8185"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by jermsie on 2009-01-23
The wireless card has been working great, my only problem is that I suspend my PC often when I'm doing something else. On resume, wireless does not auto-reconnect and I always need to run "sudo /etc/init.d/networking restart" in terminal.

Chipset is RTL8185.

How can the wireless automatically reconnect after system standby?

Thanks for the help :)

---

### Post by jamessnell on 2009-02-13
I've been having this problem too.

For me what happens is everything seems normal before I suspend. Then I suspend and upon resume when connecting to my personal WPA protected wireless, it'll connect for a little while (10seconds to 5mins) and then lose the connection. If I disable then re-enable networking & wireless through the ubuntu network widget, the avg. time between it losing a connection seems to go down slightly - but I suppose the issue remains.

Seems to me that if I'm connecting to some other wireless networks I use that don't have encryption on them, then I don't notice a problem.

I'm using the following network card:

```

02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
	Subsystem: Apple Computer Inc. Device 0088
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
	Memory at d0000000 (64-bit, prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb

```

---

### Post by danmarycap on 2009-03-13
In case you're still having this problem, I've posted a solution here: [http://ubuntuforums.org/showthread.php?p=6883391](http://ubuntuforums.org/showthread.php?p=6883391)
-Dan

---

