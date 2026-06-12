---
title: "linking eth0 and ath0"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by smTdust on 2009-02-18
I have working eth0 and ath0 devices on my box. 

A visual representation may serve to explain the problem. This is the way things are connected.

[IMG]http://lh3.ggpht.com/_iEABaKLj3_Q/SZvohrIFOhI/AAAAAAAAD3M/2acrtdnhauU/arch.png[/IMG]
see: [http://lh3.ggpht.com/_iEABaKLj3_Q/SZvohrIFOhI/AAAAAAAAD3M/2acrtdnhauU/arch.png](http://lh3.ggpht.com/_iEABaKLj3_Q/SZvohrIFOhI/AAAAAAAAD3M/2acrtdnhauU/arch.png)

I can log in wirelessly into the system with a laptop. From the laptop, I can ssh into the system, no probelm. I can also pull up a terminal in the laptop and ping ath0 192.168.2.1. I would like to, however, be able to also from the laptop ping the device (192.168.99.100) connected to eth0.

I've enabled ipv4 forwarding and tried these commands

iptables -A FORWARD -i eth0 -o ath0 -j ACCEPT
iptables -A FORWARD -i ath0 -o eth0 -j ACCEPT

i get an error when i try to ping 192.168.99.100 from the laptop. 

What do I need to add to make this work? I messed around with bridging, but I don't really seem to get what that does or how it works.

thanks much

---

### Post by superprash2003 on 2009-02-18
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by smTdust on 2009-02-19
Cool works well for the most part. I can now ping 192.168.99.101 from the laptop on wifi.

However, i get no response when i try to ping the 192.168.99.100 device connected to eth0. Do I need to edit iptables to fix this so that eth0 forwards something to the device?

thanks

---

### Post by superprash2003 on 2009-02-19
the link to the arch.png doesnt open.. so i dont have an idea about your current network setup.. so i dont know what 192.168.99.100 and 192.168.99.101 is!

---

