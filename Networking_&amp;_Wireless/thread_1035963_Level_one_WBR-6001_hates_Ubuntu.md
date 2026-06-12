---
title: "Level one WBR-6001 hates Ubuntu"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by qewrtyuiop on 2009-01-10
I have used a WGT624 for a while and finally gave up and bought WBR-6001 by Level One when I got tired of it relentlessly dropping wireless connections.  Now when I try to connect to it, the Level One router refuses to accept any wireless connections from my laptop (Acer Aspire One running Ubuntu 32 8.10).  I have disabled all forms of wireless security and even went back to factory defaults and it refuses to accept the connection with the following log entries:
> Associated: xx-xx-xx-xx-xx-xx st=0
Disassociated: xx-xx-xx-xx-xx-xx because RX deauth req
All the reviews I could find on it said it was great but I'm starting to regret buying it due to the crappy-Japanese-to-English documentation.
Thanks

---

### Post by qewrtyuiop on 2009-01-10
Update:
I forgot to mention that every few connections attempts, Ubuntu will continuously cycle and become locked to the point that physical restart is required to correct it.
Now when it tries to connect, it associates and then becomes inactive to the point that the router closes the connection:
Disassociated: xx-xx-xx-xx-xx-xx because idle 300 seconds

---

### Post by gryzzly on 2009-09-24
Oh, I happened to receive this router as a birthday gift from my colleagues. Did anyone else use Level one WBR-6001 with ubuntu? Or maybe any other linux distro? 
In my case I am able to connect to it, but after a while I'm getting disconnected, with the following in the log:
```
Disassociated: XX-XX-XX-XX-XX-XX because RX deauth req
```
(where XX-XX..XX is my mac address)
I have lenovo 3000 n200 laptop, with intel 3945 wi-fi.

Any advice would be much appreciated.

---

### Post by shemtovo on 2009-11-29
have any of you been able to solve it?
i just bought one, thinking "it wont be a problem, all routers are the same" only to find this bug.

DAMM

---

