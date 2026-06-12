---
title: "PPTPD on Ubuntu, Windows 7 Client, Default ppp gateway 0.0.0.0."
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by ottodashadow on 2010-11-22
I've setup pptp with Ubuntu, and I can successfully login to the pptp server through a linksys router. Once in the VPN I can access Samba shares using the local IP address, so I know that I'm actually connected successfully.

My Setup:
Ubuntu Server
Internal IP: 192.168.1.125
Subnet: 255.255.255.0
Gateway IP: 192.168.1.125

Windows 7 PPP Adapter (Once connected)
IP: 10.10.10.10
Subnet: 255.255.255.255
Gateway: 0.0.0.0

The linksys router has a public address in the 71.x.x.x range, but I've forwarded the ports to the 192.168.1.125 or the server.

The goal, is to login to the server using VPN and then access, say Google, through the VPN tunnel. So, if someone could help me understand what little part I'm missing I would appreciate it.

I might also mention that I can us nslookup and query the DNS server on 192.168.1.125 to get the address of google.com.

Thanks
Matt

---

