---
title: "VPN Connection"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by Dj1210 on 2012-10-21
Hi there

I have been using Ubuntu not so long, and I was wondering if you can help me with some information about how to set up a VPN connection (documents, tutorials, or links related here in the forum). 

I just want to be able to go anywhere and connect to one of the machines using a VPN, and then SSH to transfer basic files (text, music, photos..). I was also wondering if the only way I can listen to music (remotely!! :P) is to connect using a VPN, and then fire up VNC to run VLC. (Not possible through CL?)

I have two Ubuntu machines and both are running *Precise Pangolin, *and my machines are just laptops not servers.  My goal is to set up one of them as a "server", so I can connect to it any time, and of course it is going to be a very very limited server. 

Thank you very much for any help and guidance. 

Kind Regards :P

---

### Post by Reflectoman on 2012-10-21
Hi,

I've had great success with OpenVPN connections.   They have encryption and authentication not only via IP addresses but also via key exchanges and SSL/TLS certificates.

Have a look at this tutorial made for Ubuntu and how to install OpenVPN as a server, and also on another computer as a client.

[https://help.ubuntu.com/11.10/serverguide/openvpn.html]("https://help.ubuntu.com/11.10/serverguide/openvpn.html")

It also creates virtual interfaces on your computers, so it makes it easier for routing, troubleshooting, firewalling, QoS, etc.

Best of luck!

---

### Post by ahallubuntu on 2012-10-21
I also recommend OpenVPN.  However, an alternative you might consider is to install OpenVPN on your home router.  That way, you don't have to leave on a laptop or tower computer all the time; you can even leave them in standby (sleep) and wake them up remotely once you have connected to your VPN.

Unfortunately, OpenVPN isn't supported out of the box on any consumer router I've ever seen.  But if your router supports the free (Linux-based) DD-WRT firmware -  and has enough RAM and flash memory to support the full image of DD-WRT - you can use OpenVPN that way.  There are other open firmwares like Tomato and OpenWRT but DD-WRT seems to support the widest range of devices.

If you can find an old Linksys WRT54G (verison 4 or older) or a WRT54GL for cheap, you can use it as a DD-WRT/OpenVPN gateway for your network (Wireless G only - if you have an N router you could disable the G radio and just use the WRT54G as a gateway).   These are good, solid routers too, even though they are a few years old.

---

### Post by Dj1210 on 2012-10-22
Hey!!

well, all that sounds so great to do, I reckon I can get one of those routers, but to be honest I am a total new to all of this VPN communication, however I am so willing to give it a go!!. Where can I find more info about what you are proposing me to do with the WRT54GL mate?

I just found one of those and it is just 90 bucks!! 

Cheers

---

### Post by Reflectoman on 2012-10-22
Hi,

DD-WRT downloads for the router can be found at [http://www.dd-wrt.com/site/support/router-database]("http://www.dd-wrt.com/site/support/router-database").

The WIKI to install it is available from [http://www.dd-wrt.com/wiki/index.php/Installation]("http://www.dd-wrt.com/wiki/index.php/Installation").

The OpenVPN installation on DD-WRT is available from [http://www.dd-wrt.com/wiki/index.php/OpenVPN]("http://www.dd-wrt.com/wiki/index.php/OpenVPN").

---

### Post by ahallubuntu on 2012-10-22
Here's a tutorial for setting up OpenVPN with a DD-WRT router:

[http://www.dd-wrt.com/wiki/index.php/VPN_(the_easy_way)_v24%2B](http://www.dd-wrt.com/wiki/index.php/VPN_(the_easy_way)_v24%2B)

I can also recommend a newer router, the Asus RT-N13U B1, for DD-WRT and OpenVPN.  I have a couple of them; one is my primary router/gateway.  This is a budget router you may be able to find cheaply but should be much newer than a WRT54G/GL. The Asus router also has N wireless.

I paid $15 USD (used) for my last two WRT54G routers (careful again to get version 4 or older; newer versions have less flash and not enough to run the OpenVPN image).

---

