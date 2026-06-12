---
title: "How to change the network card priority with multiple cards?"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by TheAlien on 2010-09-26
I've got two network card interfaces on my computer, one wireless and one wired. The wireless card is connected to the Internet and the wired is connected to the LAN. When only the wireless card is active, Internet works. As soon as i enable the second wired card, Internet stops working. And it seems like Ubuntu chooses the wired card for Internet as soon as it's enabled.

Are there any ways to solve this? So my Ubuntu box always chooses the wireless card for Internet traffic and let me use the wired device for LAN only?

---

### Post by Iowan on 2010-09-26
In Network Manager, check the options under **Routes**. You might be able to limit the wired network to local traffic. Otherwise, you can see if **route -n** changes the default route when wired is plugged in.

---

