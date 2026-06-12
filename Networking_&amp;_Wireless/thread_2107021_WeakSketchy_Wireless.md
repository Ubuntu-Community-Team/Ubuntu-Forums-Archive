---
title: "Weak/Sketchy Wireless"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by colmeweb on 2013-01-20
Hey all,
  I got a new Toshiba Satellite C850D for Christmas and I am running 12.10 on it now. I had a few issues getting my wireless working, but i got that worked out here [http://ubuntuforums.org/showthread.php?t=2098755](http://ubuntuforums.org/showthread.php?t=2098755) 

Now the only remaining issue I am having is that my wireless keeps dropping out. The indicator shows that I am still connected, but there is no data moving. A new twist is that when I went to disconnect this morning I got the message that the disconnection failed because the device was not active. I was still getting the signal that I was connected, but apparently my router wasn't even active. 

Here is the router readout from lspci -v. if you want anything ells just ask. 

```

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723
	Subsystem: Realtek Semiconductor Co., Ltd. Device 0723
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at 3000 [size=256]
	Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: rtl8723ae
	Kernel modules: rtl8723ae


```

-Thanks

---

### Post by colmeweb on 2013-01-26
Half update half bump,

Over the last 40 minutes I have done this about 9 times with the same result every time. My internet is working fine and then I try to load a youtube, hulu, or streetfilms video and my signal drops to nothing. If I close the page my signal comes back after about 30 seconds or so. If I don't close the window my signal never comes back.

This might explain why it works sometimes and not others if the excessive flash ads on a page are kicking my signal. 

Has anyone out there ever heard of flash disrupting a wireless signal?

---

