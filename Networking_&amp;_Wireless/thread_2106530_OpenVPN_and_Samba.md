---
title: "OpenVPN and Samba"
date: 2013-01-19
forum: Networking &amp; Wireless
---

### Post by lotsofsnow on 2013-01-19
Hello,

I am using openvpn on ubuntu to connect to a vpn. I have samba shares on my internal network (a usb-harddisk mounted to the router). Once the VPN is connected, access to the samba shares slows down significantly, probably because all internal network traffic gets routed through the VPN. Is there a way to around this?

Kind regards

---

### Post by ahallubuntu on 2013-01-19
If you don't need your internet traffic routed through the VPN, you can disable that so you access only the additional network you are connecting to. 

You can tell the Network Manager plug-in not to route traffic through the VPN this way: there's an option under "IPv4 Settings" - click the "Routes" button and then check the box next to "Use this connection only for resources on its network" and see if that works.

---

### Post by lotsofsnow on 2013-01-19
Thank you for the reply. I want internet traffic routed through the VPN but not internal traffic. So what I want is the other way around, I guess.

I'm running ubuntu on a headless system, without graphic interface, and use openvpn from the shell without network manager.

---

