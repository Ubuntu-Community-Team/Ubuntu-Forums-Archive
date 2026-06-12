---
title: "VPN PPTP Connection Woes"
date: 2013-06-27
forum: Networking &amp; Wireless
---

### Post by Siyfion on 2013-06-27
Okay, so I have a PPTP VPN connecting to a MS Windows PPTP server at the other end (Windows 2012 Server).
I'm trying to make it so that everything in the 192.168.0.x range (the remote network IP range) is sent over the VPN, but everything else is sent straight over the internet / internal network (192.168.1.x).

However, I can only get the VPN to work with no internet connectivity, or no remote connectivity. :\

So far I have tried setting the IPv4 Settings to:

> Method: Automatic (VPN)
Routes:
  Use this connection only for resources on its network: **checked**

Which results in all internet traffic going out normally, but attempting to ping 192.168.0.15 (a machine on the remote network) fails entirely, as does all communication with all remote servers.

> Method: Automatic (VPN)
Routes:
  Use this connection only for resources on its network: **un-checked**

Which results in me loosing all internet connectivity, but having access to the remote servers.

---

