---
title: "Enthernet won't connect"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by ryan.megatron on 2009-11-15
Hi everyone,

I recently installed Ubuntu 8.10 to dual boot on my Windows XP laptop. It's very different from Windows and I'm still figuring out how some stuff works, however everything seems to do it's job. But when I plug in my ethernet cable, I see this swirl appear where the network thing was, but after waiting a while, it says something like "Network not Connected". Everything works fine in Windows.

Can someone tell me what I'm doing wrong?
Thanks!

---

### Post by sanderj on 2009-11-15
Why Ubuntu 8.10? Why not Ubuntu 9.10, which is more up to date?


What's on the other side of the ethernet cable? A cable modem? A DSL modem? Something else?

---

### Post by Iowan on 2009-11-15
I presume you're trying to get DHCP address?
**lshw -C network** (from a terminal) should show if hardware has a driver associated.
**ifconfig -a** will show IP address (or lack thereof).

---

