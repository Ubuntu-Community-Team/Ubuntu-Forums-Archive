---
title: "I can't connect to my server over WAN"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by thebigredone on 2011-04-25
Ok this may seem like a "USE SEARCH FUNCTION" Topic at first, but trust me i have.

So my problem is the following:

I installed Ubuntu Sever 10.10 on a old PC of mine and installed all the required stuff for a webserver (apache, sql, php, ftp, ssh, etc)

Our network system is one of these stupid kinds, it's a brigded connection to the ISP so every computer on our LAN gets its IP directly from the ISP and there is no local IP addresses (port forwarding isn't needed)

This might be relevant but our LAN is build as follows.

<<<<<<<<<<<<<<<<<<  -----------Switch with WLAN ------- My laptop (WLAN)
<<<<<<<<<<<<<<<<<< |
Modem/router --------------
<<<<<<<<<<<<<<<<<< |<<<<<<<<<<<<<<<---- Windows 7 PC
<<<<<<<<<<<<<<<<<<  -------------- Switch ----- |
<<<<<<<<<<<<<<<<<< |<<<<<<<<<<<<<<< --- Ubuntu Server
<<<<<<<<<<<<<<<<< 2 other PCs

My Windows 7 PC can at all times connect to the server over ssh, ftp and http, no problems. But my laptop, and my friend from his place can only connect to the server if I have recently connected with the Windows 7 PC. 

If there is no connection for a while and i try to connect with laptop or from friends place the connection just times out...

Help would be appreciated, i am kinda new to ubuntu and i had to google alot to get the server up and running, but now google did not even want to help...

---

### Post by conradin on 2011-04-25
I think its not your computers, rather the router setup. Perhaps you can give more detail about that. I have a similar issue, where if I reset the router, everyone can connect for a moment, (several hours)? but later, new connections are denied, where old connections remain intact. Maybe it has to do with dhcp, or having a limited IP pool IDK. In my case, access to the router is limited. Perhaps you have admin control to the bridge?

---

### Post by thebigredone on 2011-04-25
> **conradin said:**
> I think its not your computers, rather the router setup. Perhaps you can give more detail about that. I have a similar issue, where if I reset the router, everyone can connect for a moment, (several hours)? but later, new connections are denied, where old connections remain intact. Maybe it has to do with dhcp, or having a limited IP pool IDK. In my case, access to the router is limited. Perhaps you have admin control to the bridge?
I was browsing around in the router control panel and found that the DHCP aswell as NAT is disabled, the entire router is only there to bridge my connections to the ISP which then hands out IPs and so on. When i run ifconfig i get the same IP as if i would go to some webpage to find out the external one...

---

### Post by thebigredone on 2011-04-25
Found a solution. It seems that it was my ISP that has some weird timelimit on idle connections that made it impossible to connect from outside if the connection had been idle for 10-20 minutes.

Solution: 

> ping -i 120 [www.google.com](www.google.com)

---

### Post by conradin on 2011-04-25
Wait.. I don't get it. Did you call your ISP or something?

---

