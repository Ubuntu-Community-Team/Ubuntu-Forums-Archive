---
title: "Verizon FIOS Support?"
date: 2013-08-18
forum: Networking &amp; Wireless
---

### Post by frankentower on 2013-08-18
Has anyone who has or tried using Verizon FIOS with Ubunto or Linux Mint and had any problems? Their website says they only support windows or Mac but Time Warner said that too. I only use Linux, There should not be a problem should there?

---

### Post by Kevin_Arnold on 2013-08-18
No problem at all.  You're just going to grab an IP from their router, you could use any OS to do that.  

You won't be able to install any of the crap software they give out but you don't need that anyway.

---

### Post by frankentower on 2013-08-18
Thanks much! I only have Linux OS in here ,anyway. I figured if he sends me an ethernet cable with a signal, I'll do the rest. Was just reading horror stories from earlier years of the techs not knowing what the hell linux was or how to set it up. I had the same thing years ago when they came with time warner and the dude said to me whao with both hands in the air, he says "I don't do no Mac OS man" I said dude it aint gonna bite you just give me a signal. SMH....

---

### Post by Kevin_Arnold on 2013-08-18
I'd tell them to keep their dirty hands off the computer. Just get the router going and I'll take care of the rest :P

---

### Post by frankentower on 2013-08-19
Thats exactly what I'm going to do. Im not even going to mention I have linux until he starts setting up the router. By then he'll have the fiber optic line ran from aross the street, the new box installed, he will have no choice then to let me do the computer.:D

---

### Post by kurt18947 on 2013-08-19
I think they do need a Windows box to activate the service.  Unless it's activated, it dies in two weeks, or so I was told by a tech.    Could they do it from a Mac or linux box?  I don't know.  it's a little surprising to me that they don't have their own tablets/netbooks to activate the service.  I've been involved in a few FiOS installs, it seems like they're supposed to install some diagnostic stuff on the customer's PC but don't seem to insistent about it.  They use MOCA over coax which seems like it could be an alternative to WiFi or pulling Cat5/6 cable.  New MOCA ethernet bridges are pretty $$ but there are used Motorola NIM100s on Ebay or one could collect Actiontec FiOS routers and make them bridges, and/or  wireless extenders.

---

### Post by frankentower on 2013-08-19
Kurt ~ Verizon is supplying their own router. Why would I need to buy one? All they have to do to activate the service is call it in with the router M.A.C addee. Now when you say they use MOCA over coax are you talking about TV connectivity? If thats the case then they can by all means connect my TV's with what ever type cabling they want to. But the requirements say you need an ethernet card for internet connectivity, so that uses ehternet cabling. I see no reason why if you get a signal and activate it why it won't run on linux. I think what you may be referring to as MOCA over coax is probably the line they run form the pole to the connection box which has phone, ehternet and coax coming out of it. The MOCA connection to the box is probably their fiber optic line.

---

### Post by Hadaka on 2013-08-19
Hi, the VZ FIOS router is just like any other wifi router
you type 192.168.1.1  enter your user name--password
and can configure it anyway you want for security..or none
nothing magic..nothing complex. This information transmitted
to you via Ubuntu 12.04...VZ wireless - Fios connected.

---

### Post by bab1 on 2013-08-20
> **frankentower said:**
> Kurt ~ Verizon is supplying their own router. Why would I need to buy one? All they have to do to activate the service is call it in with the router M.A.C addee. Now when you say they use MOCA over coax are you talking about TV connectivity? If thats the case then they can by all means connect my TV's with what ever type cabling they want to.

Your correct.  You don't need to by one.  Especially if you are getting a TV package.  You need  a router that accepts coax and is MOCA aware for the FIOS TV package.
> 
But the requirements say you need an ethernet card for internet connectivity, so that uses ehternet cabling. I see no reason why if you get a signal and activate it why it won't run on linux.

The FIOS router has LAN side Ethernet ports for you to connect to.  The activation may require you to have a windows host to do that.  IDK that for sure in your area however.
> 
I think what you may be referring to as MOCA over coax is probably the line they run form the pole to the connection box which has phone, ehternet and coax coming out of it. The MOCA connection to the box is probably their fiber optic line.
The line "from the pole" is fiber optic and it is terminated by the ONT (Optical Network Terminator) in the device that is installed by Verizon at the cable drop (the demarc).  The ONT has connectors for both coax and Cat6,  but you should use coax to connect to your routers WAN side.  

MOCA means Multimedia over Coax Alliance.  This is a set of protocols for your TV and it is for coax only.  If you use the Verizon supplied router, it accepts the coax cable for MOCA services.

There seems to be multiple issues here:  [LIST=1]
[*]Activating a FIOS  install where there is no Windows or Apple Mac hosts
[*]Are you using Internet only (no MOCA) or Internet + TV (MOCA)
[*]Are you supplying the router for the LAN (DD-WRT or somesuch Linux based router)
[/LIST]
My understanding is that the Verizon router is fine with wired Ethernet, but not so good with wireless.  All my hosts are wired and have static IP addressing except the mobile hosts.  I don't use the wireless section or DHCP in the Verizon router I have. I do use a wireless  AP connected to my main switch,  which is then connected to the router.

---

### Post by kurt18947 on 2013-08-20
I'm sorry if I gave the impression you needed to buy another router, you don't.  What some people have done is buy a used Actiontec router and make it into an inexpensive wireless access point or ethernet bridge.  It's a nice option if wireless is problematic for you or you just prefer the simplicity and reliability of a wired connection.  Any coax/TV outlet can provide wired ethernet.

As far as what's involved in the activation process, I don't know.  Like most of the world, the installers were taught using only Windows so they know only Windows.

---

### Post by bab1 on 2013-08-20
> **kurt18947 said:**
> ... ethernet bridge
Do you mean a switch with more wired ports?  Why call it an ethernet bridge?

---

### Post by kurt18947 on 2013-08-20
> **bab1 said:**
> Do you mean a switch with more wired ports?  Why call it an ethernet bridge?

I think that's the proper term.  I'm referring to a device that will receive a MOCA signal from a coax jack and output it as ethernet.  A repurposed Verizon router will include a 4 port switch as well.  These are not required for FiOS service obviously but they may be useful alternatives or supplements to WiFI.  Here are a couple references to what I'm referring to:

[http://www.avsforum.com/t/1145636/actiontec-mi424wr-a-cheap-moca-bridge-for-all](http://www.avsforum.com/t/1145636/actiontec-mi424wr-a-cheap-moca-bridge-for-all)

[http://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/](http://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/)

---

### Post by bab1 on 2013-08-20
> **kurt18947 said:**
> I think that's the proper term.  I'm referring to a device that will receive a MOCA signal from a coax jack and output it as ethernet. 

That would be a media converter.  The MOCA spec's include Ethernet.  Ethernet is not defined by the cable it is transported over.
> 
A repurposed Verizon router will include a 4 port switch as well.  These are not required for FiOS service obviously but they may be useful alternatives or supplements to WiFI. 

Here are a couple references to what I'm referring to:

[http://www.avsforum.com/t/1145636/actiontec-mi424wr-a-cheap-moca-bridge-for-all](http://www.avsforum.com/t/1145636/actiontec-mi424wr-a-cheap-moca-bridge-for-all)

[http://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/](http://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/)

The first one is a description of a MOCA extender (a bridge but not of the Ethernet type).  The second one is a description or a wireless (RF) extender.

The term bridge has a different meaning in conjunction with Ethernet than when used With MOCA or with Wireless (RF).

---

### Post by jrkortze on 2013-09-05
I'm going to bump this to see if I can get some assistance.

I am writing to you all from my laptop computer, running Windows 7, connected via wifi to my FiOS router.  The security is WPA2-Personal, Encription is AES.

This laptop has a dual boot of Windows 7, and whatever flavor of Lubuntu is the latest release.

I set this computer up while at work.  To install linux on it, I ran the live CD, connected to work network, and did the install.  After Lubuntu was installed, I then connected to the work network and downloaded updated.

Tonight is the first time I tried to get on my home network via linux, and it sees the network, but it keeps telling me my password is incorrect.  I'm not trying it incorrectly, and obviously it works and connects though Windows, so I suspect that for some reason, the FiOS router just doesn't like Lubuntu.

Any suggestions? This isn't my first go-around with linux... I was running solely Ubuntu before on this laptop, and it did connect to the FiOS router back then, but would get kicked off somewhat frequently and refuse to reconnect unless I would log out of linux, and log back in.

---

### Post by kurt18947 on 2013-09-06
> **jrkortze said:**
> I'm going to bump this to see if I can get some assistance.

I am writing to you all from my laptop computer, running Windows 7, connected via wifi to my FiOS router.  The security is WPA2-Personal, Encription is AES.

This laptop has a dual boot of Windows 7, and whatever flavor of Lubuntu is the latest release.

I set this computer up while at work.  To install linux on it, I ran the live CD, connected to work network, and did the install.  After Lubuntu was installed, I then connected to the work network and downloaded updated.

Tonight is the first time I tried to get on my home network via linux, and it sees the network, but it keeps telling me my password is incorrect.  I'm not trying it incorrectly, and obviously it works and connects though Windows, so I suspect that for some reason, the FiOS router just doesn't like Lubuntu.

Any suggestions? This isn't my first go-around with linux... I was running solely Ubuntu before on this laptop, and it did connect to the FiOS router back then, but would get kicked off somewhat frequently and refuse to reconnect unless I would log out of linux, and log back in.

If you can connect with Windows 7, I'd suspect your wireless adapter, not your router.  Your symptoms are not uncommon.  There are a couple scripts you can run that will copy your wireless settings to a text file that you can upload.  For starters though, you could post the output of these terminal commands.  If you don't know how to do terminal commands, post back and someone will assist you.  First off, is your wifi adapter USB or internal (PCI)?  If usb type this:

```
lsusb
```

If internal, try this:

```
lspci
```

you can copy & paste the output, it should look something like this:

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 04f9:01f3 Brother Industries, Ltd 
Bus 003 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 011: ID 0a81:0205 Chesen Electronics Corp. PS/2 Keyboard+Mouse Adapter
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 009: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 002: ID 047d:2048 Kensington Orbit Trackball with Scroll Ring
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

You could also paste the output of 

```
lshw -c network
```

This is a start.  Some adapters/chipsets have common issues & fixes.  If it's more involved, there are several experts here to assist you.  I am not one.

Edit:  Upon re-reading your original post, you have this adapter working with Lubuntu on your work wifi connection?  If so, that does bring your home router into question IMO.  Perhaps the wireless encryption at work and home are different?  If you're comfortable doing so, could you temporarily disable encryption on your home router to see if that helps?  Have you tried connecting to a public wifi access point?  Sometimes disabling hardware encryption on the wifi adapter using software encryption instead helps, depending on the chip set.

---

