---
title: "Remote access problem"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by jhuno137 on 2009-05-06
Hello, I have been trying to use port forwarding to access my desktop over the Internet with no success.

 I have a Gnet GS8100 modem-router that connects to my ISP and then I have a D-Link wireless router which finally provides internet to my desktop (LAN) and my wireless laptop. ( ISP-> Gnet Modem-Router->Wireless router-> ( PC(LAN)+LAPTOP(WAN) )

- The Gnet Modem router has IP 192.168.1.1
- The Gnet router provides my wireless router with IP 192.168.1.150
- The wireless router provides the following IPs:

[LIST]
[*]Desktop (LAN): 192.168.0.101
[*]Laptop (WAN): 192.168.0.100
[/LIST]
I've tryed many things and always checking with Shields Up (online port scanner) that the given port was open but I never could access my computer (using ssh, http,...).

If any one have any ideas I would appreciate it very much.

Thansk

---

### Post by mattgyver83 on 2009-05-08
I made a mistake very early on that I dont know if your making or not and it literally took me 4 weeks to figure out what was wrong.

You can use your internal IP to access your VNC computers while your within your network.
You cannot use your internal IP to access your VNC computers while your off your network, you must supply your external IP.
You cannot access your VNC computers, via your external IP, while you are on your network, you can only use internal.

The last part took me 4 weeks and an accident to figure out.

Hopefully that helps.

*also, verify that your ports are open, and point to a specific machine otherwise you will get nothing.

---

