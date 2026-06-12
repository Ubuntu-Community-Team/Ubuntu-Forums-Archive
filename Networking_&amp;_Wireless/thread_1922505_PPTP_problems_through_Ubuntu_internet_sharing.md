---
title: "PPTP problems through Ubuntu internet sharing"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by nislink on 2012-02-08
Background:
Hello all. I currently have Ubuntu connecting to a wireless signal and providing internet access to two window 7 PC's. I have it setup this way as I don't have enough wireless adapters for all of the computers, and it also allows me to put a firewall between my two main computers and an external wireless network. There is a wireless router hooked up to the Ubuntu PC that connects one W7 PC wirelessly and one W7 PC via ethernet cable. This can be seen with the attached image if the description seems confusing. 

Problem:
My problem is getting PPTP VPN working correctly on the two windows 7 PC's. The VPN will connect just fine, but after a couple minutes the VPN stops receiving packets, but can still send. Once this happens it's only a minute or so later until the VPN disconnects completely.

What I have tried so far:
1.  At first I thought it was a double NAT issue, so I removed NAT filtering on WAP2. This produced the same result. 

2. Next I placed one of the PC's in the DMZ to rule out the firewall all together. This also produced the same result. 

3. I wanted to make sure it was not anything on WAP1, so I connected a W7 PC to WAP1 wirelessly and the VPN worked correctly. 

Ideas:
I am thinking it must be something within the internet connection sharing on Ubuntu causing the issue. I am using Ubuntu 11.10. The only other thing I can think of is a network conflict between my home network and work. My work network uses a subnet of 10.10.15 and my home network uses a subnet of 10.10.24. There are also over 150 networks with 10.x.x. and 192.x.x subnets connected to our company network through a VPN Concentrator. I don't know if that would cause any issues or not.

---

### Post by poolet on 2012-02-09
To configure an VPN behind the NAT it's a little bit confusing especially for user that are not familiar with module router...  To see the IP NAT translation table please open up a new serial connection with your router and copy the following cmd... At the end paste the output here... (NOTE: Do that before the VPN stops  and after the VPN stop working) 
```
show ip nat translations
```Also before you continue you need to consider a lot of things such IP nat outside 
and inside configuration, access-list...., etc... I can give you a lot of tutorials how to do that
but first I need to know about the translations of ip nat....

---

