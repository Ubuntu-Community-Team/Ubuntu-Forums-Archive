---
title: "Router behind Router"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by Matsuri on 2009-05-14
I'm trying to setup a router behind another router. I'm home for the summer from college and I want to work on my network and my server. I would prefer doing that on my network and my router rather than my parents. That way I can just transplant the whole setup to school next year.

I know it is possible to place a router behind a router, but I'm not quite sure how to go about it. Something along the lines of subnetting. I want to be on my own network but still have full internet access. The network is setup and everything works, I can view computers on the network and access the router... however, no internet.

The router is a Linksys WRT54GL that is hacked with Tomato. Setup currently with a WPA2-Personal security set up with DHCP protocol. My home network that my parents maintain is setup the same. Any help on getting this to work and not have the IP address conflict between routers would be greatly appreciated.

Thanks!
Matsuri

---

### Post by morphodone on 2009-05-14
That should be doable.  

Just make sure the dhcp addresses that are assigned are different...
meaning if your parents router assigns 192.168.0.xxx
then you should have your router assign 192.168.1.xxx or 10.0.0.xxx

---

### Post by Ericyzfr1 on 2009-05-14
It should work, I had a set-up but for it to work I had to use the IP address of the router connected to net as the gateway for the local router.

---

### Post by Matsuri on 2009-05-14
Ok, I changed the DHCP ranges. Mine are now set to 192.168.2.XXX. However, I don't seem to be getting an internet connection. When I connect to My network there is no internet. But everything else works fine. How would I go about changing the gateway address in tomato? I can't find an option any where in the control panel.

Overview page on my router:
14.18 MB / 5,368.00 KB (36.97%)
WAN
Connection Type	DHCP
IP Address	0.0.0.0
Subnet Mask	0.0.0.0
Gateway	0.0.0.0
DNS	
MTU	1500

---

### Post by mdurham on 2009-05-14
I'm not sure if this is any help but take a look anyway. It worked for me. [http://kb.netgear.com/app/answers/detail/a_id/1080]("http://kb.netgear.com/app/answers/detail/a_id/1080")

---

### Post by Matsuri on 2009-05-14
> **mdurham said:**
> I'm not sure if this is any help but take a look anyway. It worked for me. [http://kb.netgear.com/app/answers/detail/a_id/1080]("http://kb.netgear.com/app/answers/detail/a_id/1080")


mdurham, I quickly tried it and it did not seem to work. I dunno if I followed the instructions properly so I'll try again tomorrow when I'm awake, lol.

The only thing I noted is that is for setup the router as an access point of the original network. I'm looking to setup a network within a network. I don't know if thats possible as my knowledge of wireless systems is limited.

---

### Post by mjoolnir on 2009-05-14
Set the second router to the same subnet as the first, and change the ip to 192.168.x.2. On the second router you will need to turn DHCP off, and have it forward DHCP leases. Disable NAT on the second router to avoid double nat. Change it from gateway mode to router mode. Apply + reboot and it should work.

---

### Post by lisati on 2009-05-14
Sounds similar to my setup: computers --- [ehternet and wireless] -> router -> --- [5m ethernet cable] ->  wireless router/ethernet switch/modem -> phone line. Thankfully setting it up was straight forward: use the ISP provided CD in Windows to set up the router/modem with a machine hooked up by cable, then hook up the extra router and run its setup. All the IP addresses etc were taken care of automatically. All that was left was to set up static IP addresses, WPA keys, & MAC access list to my liking.

---

### Post by morphodone on 2009-05-15
> **mjoolnir said:**
> Set the second router to the same subnet as the first, and change the ip to 192.168.x.2. On the second router you will need to turn DHCP off, and have it forward DHCP leases. Disable NAT on the second router to avoid double nat. Change it from gateway mode to router mode. Apply + reboot and it should work.

he wants to be on his own network...

---

### Post by morphodone on 2009-05-15
this may seem like a dumb question, but...

do you have the network cable plugged into the right port on the router?

---

### Post by Matsuri on 2009-06-25
> **morphodone said:**
> this may seem like a dumb question, but...

do you have the network cable plugged into the right port on the router?

lmao, yes its plugged into the proper port. I've been busy with work this summer so I haven't sat down and really tried this stuff. I'll putz with it tonight. Thanks for all the input.

---

### Post by Matsuri on 2009-06-25
> **lisati said:**
> Sounds similar to my setup: computers --- [ehternet and wireless] -> router -> --- [5m ethernet cable] ->  wireless router/ethernet switch/modem -> phone line. Thankfully setting it up was straight forward: use the ISP provided CD in Windows to set up the router/modem with a machine hooked up by cable, then hook up the extra router and run its setup. All the IP addresses etc were taken care of automatically. All that was left was to set up static IP addresses, WPA keys, & MAC access list to my liking.

This also assumes that I even have the evil empire software on my computer. The router that I have is hacked with Tomato, no fun little fix it all magically CD... that I'm aware of. But thanks for the input.

---

### Post by chex_m8 on 2009-07-10
As mentioned before default gateway should be the IP of the other router,
also check to see what the Ip address is of your WAN port. Your WAN port should have an Ip address that is on the other subnet.

---

