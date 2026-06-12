---
title: "ports not visible from outside"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by kehon on 2009-07-04
i dont think my ports are forwarded because i cant access my ftp or webserver from outside the local network i can access it from another computer on the network but not from one outside of it and port scan websites say its not open can someone help me with this i've been trying for the longest to get it working also i'm using a dynex DX-WGRTR v1000 router

---

### Post by mamut0o1 on 2009-07-04
> **kehon said:**
> i dont think my ports are forwarded because i cant access my ftp or webserver from outside the local network i can access it from another computer on the network but not from one outside of it and port scan websites say its not open can someone help me with this i've been trying for the longest to get it working also i'm using a dynex DX-WGRTR v1000 router

have you forwarded the ports from the router?
it looks like you need to login into your router and make that change. If you have access to your server locally then you must open the same port your trying to access on your router.

---

### Post by kehon on 2009-07-04
yeah i already forwarded them forgot to mention that and i type in the ip i get from whatismyip.com and i cant get to them and if i goto canyouseeme.org it says my ports are closed

---

### Post by mamut0o1 on 2009-07-04
> **kehon said:**
> yeah i already forwarded them forgot to mention that and i type in the ip i get from whatismyip.com and i cant get to them and if i goto canyouseeme.org it says my ports are closed

The ip you enter in your router must be your local IP not your WAN ip.

---

### Post by kehon on 2009-07-04
if i enter my local ip 192.168.2.* then yeah it works but i want to access it from my ip so that i can access it from another computer not on the local network but on the internet

---

### Post by mamut0o1 on 2009-07-04
> **kehon said:**
> if i enter my local ip 192.168.2.* then yeah it works but i want to access it from my ip so that i can access it from another computer not on the local network but on the internet

Are you trying to connect you your WAN ip from home? if you are using the same wan ip to connect to your local network you wont get connected. you will need to do the test from your friends home or maybe you could try an open wireless network but it must be from a different WAN ip or try ctunnel that might work also.
I hope that helps.

mamut

---

### Post by kehon on 2009-07-04
i tried through a proxy and through port scanner websites but it cant find them it says ports are closed well it really says connection timed out or connection refused

---

### Post by mamut0o1 on 2009-07-04
> **kehon said:**
> i tried through a proxy and through port scanner websites but it cant find them it says ports are closed well it really says connection timed out or connection refused

Does your isp block those ports? I had them same problem with my apache webserver; I ended up changing the port for my webserver and it worked fine after that. I could never get it to work on port 80.

---

### Post by kehon on 2009-07-04
how can i tell if my isp blocks ports i'm with bellsouth/at&t

---

