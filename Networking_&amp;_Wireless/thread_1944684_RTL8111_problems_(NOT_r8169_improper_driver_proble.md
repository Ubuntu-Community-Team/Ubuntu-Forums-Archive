---
title: "RTL8111 problems (NOT r8169 improper driver problem)"
date: 2012-03-21
forum: Networking &amp; Wireless
---

### Post by bitter_mike on 2012-03-21
I'm running 10.10 on a 64-bit PC.

I have the Realtek RTL8111 NIC and it is giving me problems. I'm aware of the well-known problem where, by default, the r8169 driver is loaded and does not work with the card. I have already gone through the process to replace that driver with the correct r8168 driver from Realtek. Initially, that worked. Every time I updated the kernel, I would recompile the driver and replace the r8169 driver.

However, after this most recent kernel update, this did not work. I can detect a wired connection, but when I try to connect, it constantly disconnects, reconnects, disconnects, reconnects, every few seconds. Here is the dmesg output of relevance:


```
[ 1951.672534] r8168: eth0: link down
[ 1952.671902] r8168: eth0: link up
[ 1953.672536] r8168: eth0: link down
[ 1957.672546] r8168: eth0: link up
[ 1958.672554] r8168: eth0: link down
[ 1959.672550] r8168: eth0: link up
[ 1960.672561] r8168: eth0: link down
```

This repeats for as long as the wired connection remains enabled. I have updated to the latest driver available from Realtek as of March 21, 2012 with no luck. 

Any help would be appreciated. Thanks.

---

