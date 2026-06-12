---
title: "Failed to connect using tsclient to Windows 7 with VPN connected"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by potvora on 2011-04-18
I am quite new Ubuntu user. 
I am running Ubuntu x64 10.10 and I am trying to connect using tsclient to my work laptop (Windows 7) connected to my home network. If no VPN client is running on my laptop I have no any issues to connected it using tsclient. Unfortunately, when I am connecting with Cisco AnyConnect VPN client (2.4.1012) on my laptop (Windows 7) to my corporate network, my tsclient on the Ubuntu box is getting disconnected and it is failing to reconnect to my  laptop (Windows 7). I am not able to connect to my laptop  (Windows 7) even using telnet:
 telnet <IP> 3389
telnet: Unable to connect to remote host: Connection timed out

It was working for me before upgrading Windows and VPN. 
Any ideas how to fix this issue? Is this configuration issue? (I have the "Enable local LAN acces" switched on in VPN Any Connect preferences)

Thanks in advanced

---

