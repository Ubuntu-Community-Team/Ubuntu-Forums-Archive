---
title: "Dapper not detecting D-Link router"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by grimdaze on 2006-06-18
What I have:
Comcast highspeed internet->Cable modem->Computer

Breezy: Works
Dapper: Works


What I want:
Comcast highspeed internet->Cable Modem->Router->Computer

Breezy:Works
Dapper: Does not work


The second setup worked just fine in Breezy with no problems at all, but when I switched to Dapper I was no longer able to use my router.
The router is a D-Link WBR-1310.
Any help would be much appreciated.

---

### Post by grimdaze on 2006-06-22
C'mon I know one of you has the fix for me.
If there's anymore info that would help you help me just let me know.

---

### Post by mips on 2006-06-22
Can you ping the router ?
Can you ping the modem ?
How is your wireless setup ?
If you disable all stuff like wpa etc can you then connect to the router ?

---

### Post by grimdaze on 2006-06-23
[QUOTE=mips]Can you ping the router ?
Can you ping the modem ?
How is your wireless setup ?
If you disable all stuff like wpa etc can you then connect to the router ?[/QUOTE]

1 & 2
Dunno. How do I test that?

3
It's a wireless router but everything uses wires right now.

4
What is wpa?

---

### Post by yopnono on 2006-06-23
Try to dis/enable the network interface. Also try to reset the router, use ifconfig to see if you get any IP from the router. 
Then try to ping your router/gateway using ping -w4 IP_ADDRESS .
The router is normally using any IP like 192.168.0.1

---

### Post by mips on 2006-06-23
ping "router ip address"
ping "modem ip address"

From the question to the above I think you should give us a bit more information.

Modem:
IP address WAN side, Subnet Mask, Gateway
IP address LAN(router) side, Subnet Mask, Gateway

Router:
IP address WAN side(cable modem), Subnet Mask, Gateway
IP address LAN(PC) side, Subnet Mask, Gateway

(Wan->Modem->Lan) -> (Wan->Router->Lan)  -->PC

There should be a ip address for each side of the modem and router as depicted above.

---

