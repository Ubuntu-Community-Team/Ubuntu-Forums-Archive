---
title: "iperf doesn't work with TCP but does with UDP"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by KOTAPAKA on 2009-07-24
I have a server and I want to examine some network traffic. I ssh to the server (via IP) and do iperf -s. Then on my computer I do iperf -c IP. I get:
```
connect failed: No route to host

```

If I become the host and the distant server the client (i.e. iperf -s on my PC and iperf -c myIP on the server) it works. It also works if am the client but specify the -u option i.e. use UDP. I have no idea why this happens.

---

