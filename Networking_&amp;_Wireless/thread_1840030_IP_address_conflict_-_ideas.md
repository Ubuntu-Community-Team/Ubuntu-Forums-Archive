---
title: "IP address conflict - ideas?"
date: 2011-09-06
forum: Networking &amp; Wireless
---

### Post by Webgirl on 2011-09-06
I'm in the process of setting up a VPN connection and am having IP address conflicts. The local LAN (my home router) is using 192.168.1.* but the remote LAN is also using it because it is using 192.168.0.* through 192.168.7.* I know one of these ranges need to be changed, but in addition to setting up a VPN on this computer (Ubuntu 10.4) I also have an Apache2 server, Samba, and Drupal running. So if I change the home routers address to a new range then all my servers configs are wrong.

The end goal is to have my mac able to connect (through a VPN) to my apache2 linux server at home.

Other than changing the address of the home router, is there another way to resolve this issue?

---

### Post by e79 on 2011-09-06
Unfortunately no. You simply cannot have the same subnet for both locations, there is no way to circumvent it as far as I know. Changing the subnet @home would be the only viable solution. I suggest you create something in the 10.0.x.x or 172.16.x.x (with either mask /16 or /24, whichever suits you best)  or anything that would mostly differ from the usual 192.168.x.x.

Hope this helps

---

### Post by papibe on 2011-09-06
Check your router (manuals, support site, or just connecting to it). Some of them have the ability to set different DHCP ranges. For example mine have this options:
```
192.168.1.0 / 255.255.255.0 (default)
172.16.0.0 / 255.255.0.0
10.0.0.0 / 255.255.0.0
```
Hope it helps,
Regards.

---

### Post by Dangertux on 2011-09-06
There are ways around it using a reverse proxy or SSH tunnel. At that point you might as well just change up your server configurations though, since you're essentially going to be tunneling twice.

If you are really interested in doing it that way you can research setting up a reverse http proxy with apache and obviously using ssh tunneling over different subnets.

---

### Post by Webgirl on 2011-09-06
Would it be easier/possible to change the remote ip address instead of the local ip? As it's my server I have control over both ends. As you can probably tell, this is my first time setting up a server/vpn.

---

### Post by Dangertux on 2011-09-07
It would be about the same to change either way imo

---

### Post by e79 on 2011-09-07
Assuming you have physical access to the remote location, it also depends on how many machine it affect on both ends ;)

If you don't have physical access, I don't think you could change the subnet without kicking you out of your VPN and causing temporary problems on your network.

---

