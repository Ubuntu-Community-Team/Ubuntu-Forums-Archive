---
title: "Cannot access router admin?"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by xxarthur33xx on 2009-08-20
The other night the internet on my psp stopped working, so I went to see if anything might have changed, but come to find out, I cannot access my Linksys wrt54g admin settings. I tried 192.168.1.1 and it says > Failed to Connect
Firefox can't establish a connection to the server at 192.168.1.1 but I can still access the internet from all the computers in the house...

Ive done ifconfig and everything looks allright.. Any suggestions?

---

### Post by doas777 on 2009-08-20
reboot the router, or unplug it for at least 60 seconds, and make sure your on a wired connection.
try the connection again. if it fails, try pinging the ipaddress of the router. 
also, are you sure that is the correct IP? I change mine, but FF remembers the old IP for 
some time, and kept offering it to me via history.

I've noticed this problem in a series of routers that were dying. eventually they would no longer pass client traffic, and I buy a new one.

---

### Post by xxarthur33xx on 2009-08-20
well I manually entered the info on my psp and now the psp works fine. Im still not sure why i cant access the router. I dont believe I changed the router ip.. How could I tell?

---

### Post by doas777 on 2009-08-20
> **xxarthur33xx said:**
> well I manually entered the info on my psp and now the psp works fine. Im still not sure why i cant access the router. I dont believe I changed the router ip.. How could I tell?


well the easiest way would be to double check the IP on a terminal that can hit the internet. 
if it is in the 192.168.1.x network, then you have the right IP. if not, change your address accordingly.

I assume you tried to connect with the other PCs which can hit the Internet?

also try putting in:
[https://192.168.1.1](https://192.168.1.1)
(note the http**s**) in case it is configured to deny unencrypted connections.

---

### Post by xxarthur33xx on 2009-08-23
Well I can access it on my windows partition.. Why cant I get in whil eon ubuntu?

---

