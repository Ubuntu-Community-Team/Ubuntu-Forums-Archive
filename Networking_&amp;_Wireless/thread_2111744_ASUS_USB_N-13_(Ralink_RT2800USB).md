---
title: "ASUS USB N-13 (Ralink RT2800USB)"
date: 2013-02-02
forum: Networking &amp; Wireless
---

### Post by n96 on 2013-02-02
This adapter at first worked plug and play. After some time it started randomly dropping the connection and refusing to reconnect for ten minutes or so. Now it's refusing to connect at all. I see the wireless networks, it does actually connect to my wireless network, but almost all packets sent were dropped. When I try to ping my router, usually about 1 in 100 packets yields a response and 1 in 10 yield "Destination Host Unreachable" (those are usually all clumped together. I tried installing the driver which came with it, nothing happened. I may have not installed it properly and I wouldn't know because apparently at Asus they still believe user friendliness and linux can not be in the same sentence. I uninstalled the driver as it seemed to be doing nothing. 

Help is much appreciated. 

I looked for threads, but no one seemed to have this problem. 

Using Ubuntu 12.04

---

### Post by ahallubuntu on 2013-02-02
~

---

### Post by n96 on 2013-02-02
I followed the instructions in that thread, but nothing has changed. :(

---

### Post by ahallubuntu on 2013-02-02
~

---

### Post by ahallubuntu on 2013-02-02
~

---

### Post by n96 on 2013-02-02
Results: 
[IMG]http://i46.tinypic.com/2ai3udz.png[/IMG]

---

### Post by ahallubuntu on 2013-02-02
~

---

### Post by n96 on 2013-02-02
Thank you for trying anyways. If it helps anyone, I found out that the adapter has a Railink RT3072 chipset by running lsusb. I'll do more googling to see ifI can find a solution with this new information.

---

### Post by ahallubuntu on 2013-02-02
~

---

### Post by n96 on 2013-02-04
> **ahallubuntu said:**
> One tip: if you can find a way to get online more reliably (temporary wired connection?), try installing all suggested updates especially the latest kernel.  You're seem to be using 3.2.0.25 which is quite old - in 12.04 now I was automatically updated to 3.2.0.36 when installing updates.  Newer kernels can definitely fix hardware issues.  I'd probably do that first if possible to rule that out, then work on tweaking.

You can verify that you're really on 3.2.0.25 (as I suspect from your screenshot) by typing

```
uname -r
```

in a terminal.
Ah yes, indeed. After updating to 3.2.0.37, the problem is now solved. Thank you very much.

---

