---
title: "[Karmic] Empathy and Pidgin have the same issue...Network Error."
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by HuoMaKe on 2009-12-24
I'm using AIM, but I've seen posts about MSN, Google Talk....everyone has this error, but none of their solutions work for me.

Debug output from pidgin -d:

```
(04:21:41) util: parsed 360
(04:21:44) dns: Got response for 'login.messaging.aol.com'
(04:21:44) dnsquery: IP resolved for login.messaging.aol.com
(04:21:44) proxy: Attempting connection to 205.188.251.43
(04:21:44) proxy: Connecting to login.messaging.aol.com:5190 with no proxy
(04:21:44) proxy: Connection in progress
(04:21:45) proxy: Connecting to login.messaging.aol.com:5190.
(04:21:45) proxy: Error connecting to login.messaging.aol.com:5190 (No route to host).
(04:21:45) proxy: Connection attempt failed: No route to host
(04:21:45) oscar: unable to connect to FLAP server of type 0x0017
(04:21:45) connection: Connection error on 0x8fd8330 (reason: 0 description: Unable to connect to authentication server: No route to host)
(04:21:45) account: Disconnecting account MarkTraceur (0x890d100)
(04:21:45) connection: Disconnecting connection 0x8fd8330
(04:21:45) oscar: Destroying oscar connection of type 0x0017.  Disconnect reason is 0
(04:21:45) oscar: Disconnected.  Code is 0x0000 and msg is 
(04:21:45) oscar: Signed off.

```

I have nothing special going on, really. I switched connections recently (came home for the holidays) but apart from that, everything is normal.

Output of ping login.messaging.aol.com:

```

PING login.messaging.aol.com (64.12.202.116) 56(84) bytes of data.
64 bytes from bucp-m1-vip.blue.aol.com (64.12.202.116): icmp_seq=1 ttl=51 time=643 ms
64 bytes from bucp-m1-vip.blue.aol.com (64.12.202.116): icmp_seq=2 ttl=51 time=675 ms

```

(I don't remember how to check a specific port, but I don't know if that matters?)

If anyone can figure this out I would sure appreciate it, it is bugging the hell out of me.

Thanks,
MarkTraceur

P.S., I checked on my laptop...also running Karmic. It can't do AIM on Empathy, either. I can use naim and Meebo, though. What could it be&#8253;

---

### Post by HuoMaKe on 2009-12-25
Bump--I could really use a solution!

---

### Post by eugenevdm on 2010-01-07
Same problem would like a solution.

---

### Post by Rasheeke on 2010-01-15
For me I have disconnects from msn but not gmail once in a while at random or when I change my status at all.

---

### Post by SyphonX67 on 2010-04-05
same problem here. It was working fine up until a couple of days ago...

---

### Post by tacticalbread on 2010-04-07
Same problem. AIM network error with AIM.

---

