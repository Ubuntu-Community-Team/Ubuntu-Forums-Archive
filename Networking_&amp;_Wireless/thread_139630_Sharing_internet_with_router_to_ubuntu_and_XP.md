---
title: "Sharing internet with router to ubuntu and XP"
date: 2006-03-04
forum: Networking &amp; Wireless
---

### Post by 604 on 2006-03-04
Hi!

I've gone thorugh some threads, but haven't found help yet. 

I've got a DSL connection and a SAGEM modem ( SAGEM  F@st 908 ). I want to share network to an ubuntu desktop and a XP desktop through a router (LevelOne FBR-1418TX). I first connected just the ubuntu computer through the router with modem and followed instructions in the manual, but couldn't get any connection. I really can't figure out how to do the configuring. I'd be very grateful if someone could help me.

Thanks,
Martin

---

### Post by woedend on 2006-03-04
so, where are you at with it now?  Does either PC connect?  If not, try accessing 192.168.0.1 or 192.168.1.1(normal router ip addresses) through a webbrowser and see if you get anywhere.  If not, on both machines, we'll have to see whats going on with the router.  Or you can check the ip address on both machines.  In linux ifconfig in windows ipconfig.  I can most likely help you so let me know how far youve gotten.

---

### Post by jamesr on 2006-03-04
That is unusual that the router manual has linux instructions. As woedend what is connected. It may be easier to connect the XP system as a lot of manuals give step by step instructions and tha t prove out the router and the modem, etc.

---

### Post by 604 on 2006-03-05
Thanks! I set connection to DHCP and then was able to access the router settings. Configuring it on Linux turned out to be quite easy. I'll try it on windows as soon as i have bought a 14 mm drill to get the cable to other room  : D

---

### Post by 604 on 2006-03-05
Alright, got the cable connected to XP comp and i have no idea what to do in windows to get internet running. Help ?

---

### Post by woedend on 2006-03-05
rather than tell you to release and renew, just restart the computer and try it out.  If it does not work, its either not getting an IP address from the router or the router isnt jiving with the modem.  if it does not work, run cmd, type in ipconfig /all  and post the contents here please.  But, if it works in ubuntu, windows should work just as well.

---

### Post by 604 on 2006-03-05
Restarting did not help

Windows IP Configuration

	Host Name :				wdt2fi76y2gc8ct
	Primary Dns Suffix:
	Node Type:				Unknown
	IP Routing Enabled:			No
	WINS Proxy Enabled:			No

Ethernet adapter Local Area Connection:

	Connection-specific DNS SUffix:
	Description: 				Realtek RTL8139 Family PCI Fast Ethernet NIC
	Physical Address:			00-50-22-BB-A8-24
	Dhcp Enabled:				No
	IP Address:				192.168.123.114
	Subnet Mask:				255.255.255.0
	Default Gateway:			192.168.123.254	
	DNS Servers:				192.168.149.45

---

### Post by woedend on 2006-03-05
ah i see, doesnt appear to be using dhcp.  forgive me as I havent used windows in a while, i'll try to get your started.  You want to get to the control panel that shows your connections, in this case apparently just one that will probably say Local Area Connection or LAN or High Speed.  To get there, I believe its under my network places or from the control panel under ?internet or networking? or/and then "Network Connections".  When you see the connection, right click it and go to properties.  Left click Internet Protocol once to highlight it(DO NOT UNCHECK), then go to properties.  select obtain ip automatically and obtain dns automatically.  if it doesnt work straight away, get back to the screen where you see the Local Area Connection(Network Connections), right click it, then choose repair.  let me know how this works.  what am i still doing up...time for bed :p

---

### Post by alamba on 2006-03-05
[QUOTE=604]
I set connection to DHCP 


Family PCI Fast Ethernet NIC
	Physical Address:			00-50-22-BB-A8-24
	Dhcp Enabled:				No
[/QUOTE]

If your router is running DHCP then don't give the XP box a static IP. Let it pull its own settings.

A

---

### Post by 604 on 2006-03-05
I did as you said and got it working. Thank you very very much!

---

