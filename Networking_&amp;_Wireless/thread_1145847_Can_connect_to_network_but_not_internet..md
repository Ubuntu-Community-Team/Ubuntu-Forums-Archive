---
title: "Can connect to network but not internet."
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by Tkdmaster on 2009-05-02
Hi! I am completely new to linux so please bear with me and my inability to understand linux. 

Anyways, the issue I am having is that I can get ubuntu to connect to the network, it shows that I am connected to the router, the ip, subnet mask, speed, etc. but it can't ping any outside addresses or get on the internet. Any ideas? Please be through on explainations or questions, as I am a bit of a noob when it comes to this. Thanks!

---

### Post by Iowan on 2009-05-02
Does machine get it's IP address via DHCP (router?) or is it a static address? The first thing that comes to mind is whether the machine has the right gateway. Check (in a terminal) the results of **route -n** - and post here.  There *should* be a line with your router's address and "UG" for a flag.

---

### Post by doas777 on 2009-05-02
[LEFT]if you open a terminal and enter:
```
nslookup www.google.com
ping www.google.com
```

what do you get?
[/LEFT]

---

