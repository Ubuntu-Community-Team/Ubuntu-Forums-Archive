---
title: "No internet connection during OpenVPN session"
date: 2013-01-12
forum: Networking &amp; Wireless
---

### Post by p8r on 2013-01-12
Hi all, 

a few days ago finally I switched to Ubuntu 12.10 after many years of suffering with Windows or MacOSX. Now I think I found what I really need.:) But... I've got a problem. I'm working on a project and I need to connect to a remote intranet server through VPN. Since I have to use certificates I'm using OpenVPN. (I used OpenVPN on Windows as well). My problem is when I'm connecting with VPN my internet connection stops working and I can't browse any site, use ftp, mail etc. How could I configure my VPN client to keep my internet connection alive during a session? 

Thanks!

---

### Post by ahallubuntu on 2013-01-12
Do you have no internet connection or no DNS?

Can you ping this IP address while connected to the VPN?

```
ping 173.194.33.34
```

(That's a Google IP.)

If you can ping it, then you just don't have DNS.  In your OpenVPN config, under IPv4 Settings, choose "Automatic (VPN) addresses only" and then fill in some DNS servers.  Try Google's: 8.8.8.8 and 8.8.4.4 .

---

### Post by p8r on 2013-01-13
Hi, 

thank you for the quick reply. I tried to do a ping but it doesn't work. I can not ping any server... But I still access the VPN server. (btw much faster than on Windows. :) )

---

### Post by ahallubuntu on 2013-01-13
It's possible your OpenVPN server does not route gateway traffic out to the internet.

As I recall, by default the Windows (free) OpenVPN client does not by default route all traffic through the VPN but the Linux/Network Manager client does.  So in Windows, your non-VPN traffic may never have been routed through the VPN and thus you wouldn't have seen this problem.

You can tell the Network Manager plug-in not to route traffic through the VPN as well.  There's an option under "IPv4 Settings" - click the "Routes" button and then check the box next to "Use this connection only for resources on its network" and see if that works.

---

### Post by p8r on 2013-01-13
Cool, thank you very much, that was the main problem! Thanks again, now runs everything well!

---

