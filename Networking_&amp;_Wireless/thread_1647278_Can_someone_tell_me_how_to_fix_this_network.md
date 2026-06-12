---
title: "Can someone tell me how to fix this network?"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by TheOnlyMrK on 2010-12-17
Okay in basic my network goes like this...
DSL Router - WiFi connection - Desktop 1 - ethernet connection - Wireless router - Desktop 2 (and various other networked devices)

This setup has been beating my a** ever since I had to start using it months ago (can't afford internet till I find a new job, so am using neighbors wifi) and I have yet to learn enough about networking to figure out what I'm doing wrong. So far I have everything set up like this:

DSL Router:
IP Address: 192.168.0.1
IP Netmask: 255.255.255.0
WAN IP Address: 173.87.178.38
Default Gateway: Use WAN
Host Name: speedstream
DHCP Server: Enabled
Start IP Range: 192.168.0.2
End IP Range: 192.168.0.254
Default Gateway: Self
DNS Server: Use WAN
Domain Name: domain.invalid
Lease Time: Infinite
Reserved IP Addresses: 192.168.0.2 for **:**:**:**:**:** (desktop 1 MAC address)

Desktop 1:
Currently running Windows XP, will be switching to Ubuntu 10.04.1 tomorrow.
Network bridge between wifi card connected to DSL router and ethernet card connected to wireless router WAN port
IP Address: 192.168.0.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.0.1
DHCP Server: 192.168.0.1
DNS Server: 192.168.0.1

And that's as far as I've gotten stuff to set up AND work, after that obviously is the wireless router and using it's factory default settings (Dynamic WAN) when I plug desktop 1 into it's WAN port the connecting light never stops blinking orange (meaning still working) and nothing can connect to the internet, then I tried messing with the settings and set it to use a static WAN to 192.168.0.1 for default gateway, DNS server, etc. and the connecting light stays on flashing orange for a little then turns solid blue (meaning connected) but when a computer tries to access the internet it still can't connect but desktop 1 can.
Giving up on the wireless router for the night I took the ethernet cable from desktop 1 and plugged it directly into desktop 2, immediately desktop 1 and 2 reported that their is an IP address conflict and after looking into it they both were using 192.168.0.2, so I went into the settings on desktop 2 and set it up manually like this:
IP Address: 192.168.0.3
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.0.1
DNS Server: 192.168.0.1
and it connected right away without a single problem. So... I'm kinda clueless at this point. If anyone could help me with this and get it to work I swear I could probably kiss you. :lolflag: Just remember that if anything needs to be done to desktop 1 put the directions for it running Ubuntu because Windows XP bugs the hell out of me and will be erased tomorrow morning. That's all the information I can come up with right now, if more is needed just tell me and I'll post it.

---

### Post by grahammechanical on 2010-12-17
I just want to clarify something. It may help others to help you. I, myself, do not know much about this subject.

Desktop 1 connects to the DSL router by wireless. Am I correct? Desktop 2 is to connect to desktop 1 by ethernet cable. Am I correct? And both desktops are or will be running Ubuntu?

May I suggest that as soon as you get Ubuntu installed on desktop 1 you make sure that it is connecting to the DSL router. You will be going around in circles if you are not confident of that part of the setup functioning correctly.

As I have only one computer I cannot advise on how to network two computers together. Someone else may help you do that. There is also community documentation that you can study.

Regards.

---

### Post by TheOnlyMrK on 2010-12-17
> **grahammechanical said:**
> I just want to clarify something. It may help others to help you. I, myself, do not know much about this subject.

Desktop 1 connects to the DSL router by wireless. Am I correct? Desktop 2 is to connect to desktop 1 by ethernet cable. Am I correct? And both desktops are or will be running Ubuntu?

May I suggest that as soon as you get Ubuntu installed on desktop 1 you make sure that it is connecting to the DSL router. You will be going around in circles if you are not confident of that part of the setup functioning correctly.

As I have only one computer I cannot advise on how to network two computers together. Someone else may help you do that. There is also community documentation that you can study.

Regards.

Yes I've already been testing the network in order to see where internet/network access ends, and that is the wireless router, desktop 1 still has internet, so their is a problem with how either desktop 1 or the wireless router are set up.

---

### Post by spiky001 on 2010-12-17
Ok lets see what we can do. So you have DT1 connected via wireless to Internet? then you want eth0 to connect to other pc,s? DT1 connects and receives internet ok but nothing else can?

---

### Post by TheOnlyMrK on 2010-12-17
> **spiky001 said:**
> Ok lets see what we can do. So you have DT1 connected via wireless to Internet? then you want eth0 to connect to other pc,s? DT1 connects and receives internet ok but nothing else can?

Yes, when I plug desktop 1 (via ethernet) into the wireless router WAN port it doesn't connect/doesn't connect properly, and I'm not sure what I need to set on the wireless router to get it to work. If I take the wireless router out of the network and just plug a computer directly into desktop 1 it makes an IP conflict unless I manually set up the desktop with these settings;
IP Address: 192.168.0.3
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.0.1
DNS Server: 192.168.0.1

---

### Post by spiky001 on 2010-12-17
Ok I take it DT1 has the internet then you want to send it to router so others can use it, have you tried setting the wired connection to shared with other pc's?

---

### Post by TheOnlyMrK on 2010-12-18
> **spiky001 said:**
> Ok I take it DT1 has the internet then you want to send it to router so others can use it, have you tried setting the wired connection to shared with other pc's?

Yes it has been set like that.

---

### Post by spiky001 on 2010-12-18
Is the wan port not meant for the modem to plug in to what happens if you plug DT1 eth0 into a lan port on router

---

### Post by TheOnlyMrK on 2010-12-21
> **spiky001 said:**
> Is the wan port not meant for the modem to plug in to what happens if you plug DT1 eth0 into a lan port on router

If I do that then my network will interconnect with my neighbors network and I do not want that, that's why I always used the WAN port because it separates me from their network.

---

