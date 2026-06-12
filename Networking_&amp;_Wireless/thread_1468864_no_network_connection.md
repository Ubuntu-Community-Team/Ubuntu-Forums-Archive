---
title: "no network connection"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by Joe Soap on 2010-05-01
I bought a pc with ubuntu 9.10 pre-installed today.  Unfortunately there's a problem with the network connection, i.e. I don't have any.

The mb is a Foxconn A74ML series with onboard LAN.  

I've switched cables with another PC and it didn't have any effect.  The other PC is still connected to the internet and the new one is still not connected.

Can anybody suggest anything that I can/should do to get a connection?  Naturally I'd be happy to post whatever info is needed to help diagnose the problem.

Thanks
Joe

---

### Post by gnik1 on 2010-05-01
Is this connecting directly to the modem or is there a router in-between?

---

### Post by Joe Soap on 2010-05-01
There's a router (hub/switch?) in-between.  I have two other PCs connected to it and they're working fine.

---

### Post by gnik1 on 2010-05-01
I would give the router and modem a power cycle. While it's off reconnect the linux machine to the router and disconnect or shut down the other pc's. 
Turn the modem on, then the router, then the new pc. Give about 30 seconds between each device turned on.

After that try > Applications > Accessories > Terminal 

and enter ping -c 4 google.com

then enter ifconfig

and post both results.

---

### Post by Joe Soap on 2010-05-01
will have to wait until tomorrow to try that, but thanks.  i'll give it a shot.

---

### Post by Iowan on 2010-05-01
A couple of other things to check (all from a terminal):
**ifconfig -a** to see if your interface has an IP address
If the machine has an IP address, can it ping the router (or the other machine)?
If it can ping the router, but not google.com, can it ping by IP address (74.125.95.104)?

---

