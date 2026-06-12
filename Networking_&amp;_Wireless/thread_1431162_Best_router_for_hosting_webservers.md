---
title: "Best router for hosting webservers"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by lateralus-paradox on 2010-03-16
Alright, I'm not 100% sure this hasn't already been posted but I'm going to post anyhow.
 
This is in relation to my previous post about help in setting up a Ubuntu webserver, which can be found here... [http://ubuntuforums.org/showthread.php?t=1430346](http://ubuntuforums.org/showthread.php?t=1430346)
 
Basically i have a few questions about which kind of routers work the best for hosting a websever on Ubuntu Server 9.10. Which ones work the best for forwarding ports, setting up a static IP address, etc. Are certain routers better than others? Dlink over Netgear, Belkin over Linksys, or others.
 
As of right now right now I'm using a Dlink DIR 825. Good choice or is there a better type? 
 
In the future I may eliminate the said router and switch over to using a 25 port switch directly connected to the modem. Will the webserver still work if the router is removed or will it have to be reconfigured for the new device? Or will the router still have to be connected to the computer the webserver is hosted on?
 
These are the two possible configurations, which one will work the best?
 
MODEM ==> 25 Port Switch ==> Computer
OR
MODEM ==> 25 Port Switch ==> Dlink Router ==> Computer
 
Thanks for any advice
lateralus-paradox

---

### Post by jacknjill111 on 2010-03-16
> **lateralus-paradox said:**
> 
Basically i have a few questions about which kind of routers work the best for hosting a websever on Ubuntu Server 9.10. Which ones work the best for forwarding ports, setting up a static IP address, etc. Are certain routers better than others? Dlink over Netgear, Belkin over Linksys, or others.


I think you need to answer the following question first:
1. Are you hosting a web server that will be accessible to the internet, or 
2. Are you just needing it visible to you and your networked computers.

There are various ways to setup, starting simple and moving towards a secure, complex network.

You could start as simple as:

MODEM <===> ROUTER <===> Internal network (pc1, mac1, ubuntuServer1, ...)

A router (wireless is even better) generally acts as a DHCP server as well, which saves you a lot of work in terms of assigning IP addresses, etc. as your network (of computers) grows. Also, your network now has a set of private IP addresses (for example, 192.168.x.x or 172.168.x.x, ...). This also gives you the ability to assign static address to machines (for example, your ubuntuServer1)

Almost all routers allow you to set up rules for port-forwarding, etc. So for example, if you host your web server on ubuntuServer1, you could set up a port-forwarding rule that tells your router to allow traffic on port 80 of your router to be forwarded to ubuntuServer1 (on whatever port the web server is listening on)

I currently use Linksys DSL modem/router and a Netgear wireless router. Never used DLink. Do a comparison search on routers on Google.

You could also throw in your switch behind the router if you want to like this:

MODEM <===> ROUTER <===> Switch <===> Internal Network ((pc1, mac1, ubuntuServer1, ...)



> 
As of right now right now I'm using a Dlink DIR 825. Good choice or is there a better type? 
 
In the future I may eliminate the said router and switch over to using a 25 port switch directly connected to the modem. Will the webserver still work if the router is removed or will it have to be reconfigured for the new device? Or will the router still have to be connected to the computer the webserver is hosted on?
 
These are the two possible configurations, which one will work the best?
 
MODEM ==> 25 Port Switch ==> Computer
OR
MODEM ==> 25 Port Switch ==> Dlink Router ==> Computer
 
Thanks for any advice
lateralus-paradox

HTH,
RS

---

### Post by lateralus-paradox on 2010-03-16
Great, thanks for the quick reply. I'll be sure to test that out and I'm doing a comparison search between Dlink and other routers right now. 
 
My hope was to get the server to be visible anywhere on any computer, but I haven't been able to get access to it from a remote computer yet. I've read through and tried following a few tutorials I've found on google but none of them were for ubuntu server 9.10 so I don't think they worked quite right.
 
My friend and I managed to get a static IP set for the computer, and I think I forwarded the ports on the router correctly, but still no connection from a remote location. 
 
If anyone knows of a really good tutorial for configuring your network for a webserver, a link or any information is greatly appreciated. 
 
Thanks again for all the help
lateralus-paradox

---

### Post by gordintoronto on 2010-03-16
More details!  What is your static IP address? What port forwarding?

Can another computer on your network access the web server?

Connecting your switch to your modem will make your life very difficult...

---

### Post by perspectoff on 2010-03-21
Consider VLANs and VPN tunnels. You will want them sooner or later.

Cisco/linksys makes a nice inexpensive router with these capabilities for around $100 (avail. at office Depot, Newegg, other places).

If you don't get VPN, you will be unhappy sooner or later.

I like the Cisco/Linksys RVS 4000. Cheers.

---

### Post by maclover201 on 2010-03-21
I run a WRT600N with DD-WRT 24/7. It's fast :)

---

