---
title: "How can I connect to 2 networks and access the internet?"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by TurnOfTide on 2010-03-04
1) I connect to the internet on a wireless router from my isp.

2) I use an older router for my media server (pc) to my ps3. The router given to me from my isp is the only one I can use to connect to the internet, yet it has the worst UPnP support (ie: none).

So with this current setup, I have to disconnect from the the wired network to be able to access the internet. So how can I access the internet while still connected to the wired network?

---

### Post by psusi on 2010-03-04
Set the one connected to the Internet as your default route.  And why can't you just use your better router instead of the POS from your ISP?  For that matter, what difference does it make that your router supports upnp when you are only using it as a hub, rather than a router to the Internet?

---

### Post by pricetech on 2010-03-04
Manually configure the interface that connects to your older router and leave the Default Gateway empty.

Works for me.

---

### Post by TurnOfTide on 2010-03-04
> **psusi said:**
> Set the one connected to the Internet as your default route.  And why can't you just use your better router instead of the POS from your ISP?  For that matter, what difference does it make that your router supports upnp when you are only using it as a hub, rather than a router to the Internet?

I'm not using it as a hub, it is used for my own LAN/Hubs don't run dhcp. As for what I am using the POS one... after a lot of very long calls with outsourced staff and finally local staff (Verizon), they discovered that only their official router solved my connection dropping issue, which it did. It plays well on their network, but it is just a bad router in terms of features (UPnP), as my ps3 media server just doesn't show up on my PS3 with it.

---

### Post by Charly85551 on 2010-03-05
Normally don't want to get involved when already 2 others take care of the case,  but I have a kind of revolutionary idea:
If I understand your description correctly you have one working network with a router that is not connected to the internet and another one from your ISP that is working with the internet but very limited elsewhere. I also assume that both routers have a DHCP function.
My proposal to you is to use both routers in a row!!:o?
It is working - I have an article in an IT-magazine describing exactly this approach.
The 1st router (from the ISP) is left as is, assuming it has an internal IP like 192.168.1.1 (=your gateway and DNS-server). 
Switch off the DHCP-function in this router. You can also limit IP-range if you want since the 2nd router gets a fixed address (normally to the Internet!) of 192.168.1.2 in the same subnet (normally 255.255.255.0)
Program the 2nd router as described and give it a different network IP for your internal network, i.e. 192.168.10.1 for example (hopefully the already existing network IP-range will fit!). The only important step you need to add is "port forwarding" to be switched on on the 2nd router. Sometimes they call it also "virtual server".
Hope it will work for you! Good luck. charly85551

---

### Post by TurnOfTide on 2010-03-05
Well I kind of lied when I said that I have two routers, I really only have 1, the other is my neighbors wifi. I just didn't want a bunch of ppl getting detracted about my question at hand hahaha.:D

---

### Post by Charly85551 on 2010-03-06
Well, before we go any further you need to be a bit more precise about your hardware set-up anyway. What hardware is used to log into the WiFi-network? How many ports does your old router have? 
It might well be that you need just a clever IP-addressing to get all working, but you need to be aware about the consequences as well! You become vulnerable and transparent to other WiFi-users in the neighbourhood!
Best might be still to spend $20 for a cheap router - for example Edimax BR-6214K - to be put between your WiFi-Access Point and your own network to protect it from unwanted access. Just think about it.
cheers - charly 85551

---

### Post by Pauligrinder on 2010-03-06
I have a ppp0 (3G/GPRS) + eth0 (router) running all the time, using networkmanager.
I use them pretty much the same as you (3G for internet, ethernet for streaming video/music to xbox360)
Here's how you do it:
Right click the icon in the tray -> Edit Connections -> Choose the connection that isn't connected to the internet -> IPV4 Settings -> Routes... -> Tick the "Use this connection only for resources on its network"-option. Then it works :)

---

