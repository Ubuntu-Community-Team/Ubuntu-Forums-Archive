---
title: "Get a local static IP?"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by Strategist01 on 2010-10-19
Hi guys.

I did search for this topic, but all I came up with on here and Google were all old articles from 3 years back.

I'm using Ubuntu 10.04.1 on my laptop, which has a wired and wireless connection. The wireless doesn't have to be static as the PC is almost always near enough to the LAN cable that I can just plug it in.

I want to assign a local static IP to my wired connection. I have a router and use a LAN cable to connect to it, and then to the Inetrnet from there. I use a Billion 400G router. How would I do this?

Thanks guys.

---

### Post by perspectoff on 2010-10-19
I haven't been able to do it with Network Manager. 

I had to install Network Manager and either use the usual method of editing the interfaces config file, or installing and using Wicd instead of network manager.

I used these instructions:

[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Set_a_static_IP_address](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Set_a_static_IP_address)

---

### Post by Strategist01 on 2010-10-19
Hi there, I am trying the instructions there out now, but I do need network manager...is it OK if i just edit that config file?

Also, this is what I have put in:
```
auto eth0
iface eth0 inet static
address 10.0.0.134
netmask 255.255.255.0
network 10.0.0.2
broadcast 10.0.0.225
gateway 192.168.0.1
```

I have not entered that in and saved it, as I do not know what my gateway is. My router says 0.0.0.0 but that's for the internet - to obtain the gateway automatically. Should I put that in? Also, can you explain what the network line means? What should I enter? My router works within the 10.0.0.* range, so I just put in my router's IP...will that work?

Thanks.

---

### Post by Strategist01 on 2010-10-19
OK, I have managed to get the info. If you right click on your network icon, and go to "connection Information" you can see the details. Default route is gateway, and where it says network - just enter your router IP.

---

