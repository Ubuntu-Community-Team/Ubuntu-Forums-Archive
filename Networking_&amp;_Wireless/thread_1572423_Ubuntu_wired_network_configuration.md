---
title: "Ubuntu wired network configuration"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by su-37 on 2010-09-11
My father has configured his network and the computer has connected to the wired network. The problem is firefox says the server cant be found at the given address. The wired router says its connected to the network and yet firefox doesn't see the router admin page or network.

---

### Post by grahammechanical on 2010-09-11
How do you know that the router is connected to the network? Your Internet Service Provider, I assume. Are you putting in the browser the correct URL for the router? It is something like htttp://192.168.1.254

What do the indicators on the router tell you? My router/modem has 5. Power, Ethernet, Wireless, Broadband, Internet. All five indicators are showing green. The Internet indicator goes green when the router connects to my ISP after I switch the router on. I do not leave the router on 24 hours a day.

In Users and Groups do you have permission for internet access? 

regards

---

### Post by rocknrollmouse on 2010-09-11
> **su-37 said:**
> The wired router says its connected to the network and yet firefox doesn't see the router admin page or network.

Little puzzled by this: how is the router saying the pc is connected to the network?  (Especially as Firefox can't login to the router page.)

No ignoring my first question, I'm going to guess the router is "seeing" the pc as there's a light on by the connected port.  This could just be showing a physical connection, but not actually sending data/communicating.
This tends to point to network configuration on the pc.  (Your Firefox comments tend to point this way to.)  Have you checked network is enabled and active on the pc?

Also open up a terminal and run ifconfig, this should return you ip number - typical home numbers start 192.168.n.n or 10.10.n.n 
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:09:ff:1:ff  
          inet addr:10.10.123.123  Bcast:10.10.12.255  Mask:255.255.255.0
          ...
```
here we see my address is 10.10.123.123

Report back here with what you find.

---

### Post by su-37 on 2010-09-11
My  father managed to find an old tutorial. Thanks for the help though.

---

