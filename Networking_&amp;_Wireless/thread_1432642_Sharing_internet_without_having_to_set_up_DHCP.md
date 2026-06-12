---
title: "Sharing internet without having to set up DHCP"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by BriMan83 on 2010-03-18
So, as the title implies, I'm trying to share an internet connection between two computers.  The one currently online is a HP Presario running Ubuntu 9.10, and connects through a wireless connection.  It has an ethernet port, which I'm hoping to use to connect to a Dell Desktop running Windows XP pro SP 3.  I'm hoping to make this happen one of two ways.

1.  Without having to mess with any DHCP settings.  Sadly, I live with my parents, and the router in their room uses DHCP and sets the addresses for all the computers on the network.  My parents don't want me screwing with any of the settings on the router.  is there a way to just have Ubuntu pass information from the ethernet connection to the wireless connection without having to deal with DHCP.

2.  I'm sure this has been explained, but as I'm new to Ubuntu, I will pretty much need step by step instructions to do this part.  Sorry to be difficult.  Is there a way to have Ubuntu keep the current settings it has on the wireless side (let the router determine it's address and all of that good stuff), but have a DHCP server kick in on the hard-wired side so Internet Connection Sharing has an address to look for on the laptop?

I'm hoping this post makes has a least a slight resemblance to making sense.  If you have an answer, or need me to try to explain what I'm trying to do better, feel free to post a reply or e-mail me, and I can find another way to explain it.  Thanks for taking the time, and again sorry if this exact post has already been done.

Brian

---

### Post by errrata on 2010-03-18
Yes you can do this without touching DHCP on the router. To explain I'm going to assume that Ubuntu sees two connections on your laptop, eth0 wired and eth1 wireless to the internet. In Network Manager choose Edit Connections -> Wired -> eth0 -> IPv4 settings tab then select Method: Share with other Computers. This should configure and start something called dnsmasq which will provide dhcp for xp box (usually in the 10.42.43.* range). The only problem i had at least with a Vista box is the windows client wasn't getting DNS info so you may have to add that manually to xp box. Find your Primary DNS from eth1 Connection Information and add that number in xp Connection Settings -> IPv4 -> properties. Good luck

---

### Post by BriMan83 on 2010-03-19
Alright, so here is a run through of what I have done so far, and maybe someone can fill in what step or steps I am missing as my Linux laptop can still get on the net, but my XP desktop still is unable to.

First, I set the wired network to be shared to other computers. and that activated the the dnsmasq app.

Here is some info for IP address both on the wireless side and the ethernet side.

Wireless Primary DNS: 209.18.47.61
Wireless Secondary DNS: 209.18.47.62
Ethernet (Wired) IP address on Linux: 10.42.43.1
Broadcast Address on Linux: 10.42.43.255
Subnet Mask on Linux: 255.255.255.0

I put both DNS address, as well as the subnet mask in to the Windows machine, and I set it's IP address to 10.42.43.105, and restarted the machine.

If I have missed a step, or done something wrong, please let me know so I can give it a try, or if this should have it working, please let me know that too so I don't feel too much like an idiot.  Thanks.

---

### Post by gordintoronto on 2010-03-19
Did you use a "null modem" ethernet cable?

---

### Post by BriMan83 on 2010-03-19
As far as I know, it is just a standard CAT5 Ethernet cable.  I have acquired a collection of cable over the years, some of them I'm not completely sure where they are from.  As far as I know it's just a normal cable.  Not to sound to ignorent, but what is a Null Modem cable.  

One other thing I thought of looking at my set-up.   I have a router in between the laptop and desktop, and I have the DHCP service turned off on that router. Would the cable going from the router to the laptop need to go into one of the normal computer ports, or into the WAN port where you would normally plug in a cable modem.

---

### Post by Iowan on 2010-03-20
> **gordintoronto said:**
> Did you use a "null modem" ethernet cable?
Crossover cable? Computer-computer *usually* needs crossover cable (but i read that some gigabit NICs autoconfigure). The router *probably* uses straight cables - logic would suggest using the WAN connection to the laptop - but I misguessed that once when connecting a short-haul modem (it wanted to be plugged into a LAN port - even though it linked to Internet "source").

---

### Post by gordintoronto on 2010-03-21
> **BriMan83 said:**
> As far as I know, it is just a standard CAT5 Ethernet cable.  I have acquired a collection of cable over the years, some of them I'm not completely sure where they are from.  As far as I know it's just a normal cable.  Not to sound to ignorent, but what is a Null Modem cable.  


As Iowan pointed out, the other name is "crossover cable," and in many cases you *must* have such a cable to connect two computers directly to each other. Or you could connect each of the computers to a switch or router.

---

### Post by errrata on 2010-03-22
"I put both DNS address, as well as the subnet mask in to the Windows machine, and I set it's IP address to 10.42.43.105, and restarted the machine."

Not sure of the default config for dnsmasq but it may limit ip range to 2-100
ie. 10.42.43.**number_ lower_than_100**. Can u ping 10.42.43.1 from xp box?

---

