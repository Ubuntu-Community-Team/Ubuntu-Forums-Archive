---
title: "Cannot ping Ubuntu Server from laptop"
date: 2013-01-19
forum: Networking &amp; Wireless
---

### Post by stingblue on 2013-01-19
Hello

I'm having an odd problem, and am out of ideas on how to fix it. The problem may not be on the Ubuntu side of things, but I'd appreciate any suggestions. 

I just set up Ubuntu server on an old laptop to play around with on my home network, and would like to administer it from my recent MacBook Pro. However, I cannot ssh or even ping the Ubuntu machine from my MacBookPro, nor vice versa. 

Where I'm confused is that it seems to be only the network connection between my MacBookPro and the Ubuntu machine that has problems. I also have two windows machines and two smartphones on my home network. All four devices can ping both the MacBookPro and the Ubuntu server, and the MacBookPro and Ubuntu server can in return ping all four of these other devices (I can also ssh into Ubuntu from these other four devices, and the Ubuntu machine can reach Google and Yahoo). These windows machines aren't mine, so I really would like to be able to use my laptop with this server. 

I've flushed iptables, and checked the firewall settings on my MacBook. If it helps I'm using a Belkin router from a few years ago -- the Ubuntu server is at x.x.x.2 and the MacBookPro is at x.x.x.5. 

Thanks

---

### Post by chadk5utc on 2013-01-19
> **stingblue said:**
> Hello

I'm having an odd problem, and am out of ideas on how to fix it. The problem may not be on the Ubuntu side of things, but I'd appreciate any suggestions. 

I just set up Ubuntu server on an old laptop to play around with on my home network, and would like to administer it from my recent MacBook Pro. However, I cannot ssh or even ping the Ubuntu machine from my MacBookPro, nor vice versa. 

Where I'm confused is that it seems to be only the network connection between my MacBookPro and the Ubuntu machine that has problems. I also have two windows machines and two smartphones on my home network. All four devices can ping both the MacBookPro and the Ubuntu server, and the MacBookPro and Ubuntu server can in return ping all four of these other devices (I can also ssh into Ubuntu from these other four devices, and the Ubuntu machine can reach Google and Yahoo). These windows machines aren't mine, so I really would like to be able to use my laptop with this server. 

I've flushed iptables, and checked the firewall settings on my MacBook. If it helps I'm using a Belkin router from a few years ago -- the Ubuntu server is at x.x.x.2 and the MacBookPro is at x.x.x.5. 

Thanks

If your IP addresses are private please post the output from ifconfig on both the server and mac for reference. Can the MAC surf the web? can you ping google.com from either machine?

---

