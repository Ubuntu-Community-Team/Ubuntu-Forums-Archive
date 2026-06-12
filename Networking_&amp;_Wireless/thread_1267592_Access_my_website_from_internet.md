---
title: "Access my website from internet"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by w1z8it on 2009-09-15
I have setup an Apache website on my home server computer, and also bought a .com domain which resovles to my IP address (tested with ping).

I can connect from any computer on my network through the server computers static router IP 192.169.1.3 (or localhost 127.0.0.1 from the server machine) but I am unable to connect using my domain, or even my external IP.

My router firewall is off and the server computer is in the DMZ, any help would be appreciated.

---

### Post by wojox on 2009-09-15
Stay away from DMZ. Try and use port forwarding on 192.169.1.3 for port #80 and # 443

---

### Post by Warren Watts on 2009-09-15
Do you have port 80 forwarded (on the router) to the computer running Apache?  This tells the router to direct all HTTP traffic to the server.

---

### Post by w1z8it on 2009-09-15
> **Warren Watts said:**
> Do you have port 80 forwarded (on the router) to the computer running Apache?  This tells the router to direct all HTTP traffic to the server.

 I just said the server is in DMZ meaning all ports are opened.

---

### Post by cariboo on 2009-09-16
Even though your system is in the dmz, your isp may be blocking port 80. Use [canyouseeme]("http://canyouseeme.org") to make sure the ports aren't blocked.

---

### Post by w1z8it on 2009-09-16
> **cariboo907 said:**
> Even though your system is in the dmz, your isp may be blocking port 80. Use [canyouseeme]("http://canyouseeme.org") to make sure the ports aren't blocked.

I tried this with port 80 amongst about 50 other ports, they always time out... even though I have the server computer in DMZ and firewall turned off, what gives?

---

### Post by badger_fruit on 2009-09-16
> **w1z8it said:**
> I have setup an Apache website on my home server computer, and also bought a .com domain which resovles to my IP address (tested with ping).

I can connect from any computer on my network through the server computers static router IP 192.169.1.3 (or localhost 127.0.0.1 from the server machine) but I am unable to connect using my domain, or even my external IP.

My router firewall is off and the server computer is in the DMZ, any help would be appreciated.


if you perform a traceroute from a remote pc to your domain, how far does it get?

i agree with the other comments about stay away from DMZ though. And forgive my question here, I am not sure 100% about how a DMZ works myself,  but surely if it is in a DMZ then how can you access the website using a local IP address??

i was always under the impression to access it you'd have to go out to the internet then back into the DMZ - the DMZ is unable to see the rest of the LAN, hence it being allowed open to the world.

---

### Post by ChumleyEX on 2009-09-16
um here is a dumb question. Can other people use your domain name to get to your site?

---

### Post by ahood on 2009-09-16
> **w1z8it said:**
> I have setup an Apache website on my home server computer, and also bought a .com domain which resovles to my IP address (tested with ping).

I can connect from any computer on my network through the server computers static router IP 192.169.1.3 (or localhost 127.0.0.1 from the server machine) but I am unable to connect using my domain, or even my external IP.

My router firewall is off and the server computer is in the DMZ, any help would be appreciated.

Maybe I can help. Much apologies if I have included too much detail.

> The static router IP 192.169.1.3

I believe that an address that begins with 192 is reserved for local area networks (LAN). Thus, this address will work for computers on the same LAN network (i.e., behind the router).

Check the wide area network (WAN) by visiting [**[COLOR="Blue"]myipaddress[/COLOR]**]("http://www.myipaddress.com/show-my-ip-address/") .

What you will see is the WAN ip address that is assigned to your router and that others external to your LAN can use to access your network if allowed.

Once you have identified the correct WAN ip address, it is then necessary to update the DNS record for your domain name with this WAN address. This is usually done at the domain name registrar configuration tool, or through a third party dynamic DNS service like dyndns.com. What this will do is populate the numerous internet routers with your domain name and WAN address so that your server can be reached by Internet users. It may take up to 72 hours for the process to take effect fully.

Next, it is necessary to configure your router to forward incoming internet traffic to the server machine on your LAN. I think this is something that you probably know how to do for your router. Port forwarding may provide additional level of security rather than using the default port (80); however, doing so may limit/restrict visitors. Port forwarding is highly recommended for accessing browser based server administration tools. 

Lastly, the server machine must be configured correctly to recognize the domain address and serve up the appropriate information. Again, I assume that this is the case. 

IMPORTANT: If I am at home at a desktop machine residing on the same LAN as the server, I  have found that my ISP will prevent me from accessing the server if I enter the URL or WAN. Of course, I can access the server using the LAN ip address. I must connect to the Internet using a neighbor open wireless network, some other Internet connection (work, school, cafe, etc.), or ask a family member/friend assigned a different WAN address to test if my server is accessible via the Internet.

Below are some links to some resourceful sites.

[**[COLOR="Blue"]Internet Protocol (IP) addresses[/COLOR]**]("http://www.iusmentis.com/technology/tcpip/ipaddress/")

[**[COLOR="Blue"]myipaddress[/COLOR]**]("http://www.myipaddress.com/show-my-ip-address/")

[**[COLOR="Blue"]The Perfect Server - Ubuntu 9.04 [ISPConfig 3][/COLOR]**]("http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3")

[**[COLOR="Blue"]Geek to Live: How to assign a domain name to your home web server[/COLOR]**]("http://lifehacker.com/software/web-publishing/geek-to-live--how-to-assign-a-domain-name-to-your-home-web-server-124804.php")

[**[COLOR="Blue"]Geek to Live: How to set up a personal home web server[/COLOR]**]("http://lifehacker.com/124212/geek-to-live--how-to-set-up-a-personal-home-web-server")

[**[COLOR="Blue"]Geek to Live: How to access a home server behind a router/firewall[/COLOR]**]("http://lifehacker.com/software/top/geek-to-live--how-to-access-a-home-server-behind-a-routerfirewall-127276.php")
[I]
Note: Use the above information at your own risk. Running servers accessible outside a LAN presents security challenges. Runner commercial services from a home LAN may violate ISP terms and conditions of use.[/I] 

I hope this helps.

---

