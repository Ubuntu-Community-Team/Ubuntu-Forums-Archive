---
title: "Router page?!"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by MRoeDesigns on 2011-06-18
I can't seem to get to my router page. 

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
173.31.64.0     0.0.0.0         255.255.240.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         173.31.64.1     0.0.0.0         UG    0      0        0 eth0

```

So 173.31.64.1 should get me in. But i tried that, and .0, and 169.254.0.0 and nothing will connect. Any suggestions? I need to forward my ports.

---

### Post by nbound on 2011-06-18
If you are using wireless, try a wired link

Also, whats the router you are using?

---

### Post by MRoeDesigns on 2011-06-18
Wow I feel very stupid. Mind you it's 10am and I haven't gone to bed yet since last night, but I just rememeber something. I don't have a router, I have a cable modem. /facepalm Sorry for the ignorance. 

How would I go about bridging my connection so that outside people could connect? This kind of set-up would be necessary in things like hosting a private gaming server.

---

