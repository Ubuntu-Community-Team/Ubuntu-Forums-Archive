---
title: "No Ip when DSL connected"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by RiSE69 on 2009-04-12
Hi

I have one network port on my pc which is connected to a ADSL router. 3 other PC's are connected to this router. The router is not set up as a DHCP, and uses bridge mode. I've set up a Ethernet connection with manual settings, which works fine when I want to browse the other PC's on the network, but I cant connect to Internet. So I made a DSL connection, which also works fine to browse Internet, but then it doesn't give me a IP, and then I cant connect to the other PC's on the network.

So in short, I can only use one at a time. Is there a way to make the DSL connection use my Ethernet IP, so I am connected to other PC's on LAN, as well as the Internet?

Here's screenies to show what im talkin bout:

[IMG]http://img15.imageshack.us/img15/7980/wires.png[/IMG]  [IMG]http://img13.imageshack.us/img13/8809/dsl.png[/IMG]

---

### Post by hyper_ch on 2009-04-12
you need to add a namesever...

open /etc/resolv.conf and enter
```

nameserver ROUTER_IP

```
of course replace the router ip with the actual one.

Also you need to manually configure all the rest (as you said it's not dhcp)

---

