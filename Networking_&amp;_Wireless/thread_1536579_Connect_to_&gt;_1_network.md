---
title: "Connect to &gt; 1 network"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by fred2028 on 2010-07-22
I have a wireless Internet modem (USB) and a LAN Ethernet connection. I can only pick 1 of them to connect to (by disconnecting the other). How can I connect to both at the same time?

---

### Post by pricetech on 2010-07-22
A little clarification would be helpful.  You say you have a wireless modem that connects USB ??  Not sure what you mean there.

---

### Post by fred2028 on 2010-07-22
> **pricetech said:**
> A little clarification would be helpful. You say you have a wireless modem that connects USB ?? Not sure what you mean there.
 It's a Rogers mobile Internet stick. I put a SIM card into the stick, connect it (USB) to the server, and I can get 3G Internet.
 
The server is hooked to a LAN, but if I wanna use the 3G Internet, I need to disconnect LAN.

---

### Post by pricetech on 2010-07-22
Got it.

Manually configure your LAN connection and leave the Default Gateway blank.  That way your computer won't be trying to use both connections to access the Internet.

Should work.

---

### Post by fred2028 on 2010-07-22
> **pricetech said:**
> Got it.
 
Manually configure your LAN connection and leave the Default Gateway blank. That way your computer won't be trying to use both connections to access the Internet.
 
Should work.
 Would that interfere with the server's ability to serve pages to other computers on the network?

---

### Post by Iowan on 2010-07-22
Check **route -n** - there should be a route for "local" traffic, and a gateway for "everything else". The local should still work. Having two gateways confuses the machine.  For that matter, having both interfaces set for "local" traffic may not work,either...

---

### Post by pricetech on 2010-07-22
> **fred2028 said:**
> Would that interfere with the server's ability to serve pages to other computers on the network?

It shouldn't.  As long as they are all on the same subnet, no routing is necessary.

---

