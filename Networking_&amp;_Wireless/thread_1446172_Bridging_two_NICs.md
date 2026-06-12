---
title: "Bridging two NICs"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by DaemonLee on 2010-04-03
Hey, 

I have a PowerEdge 1750, and I want to bridge the two NICs and use them as a gateway/router and every tutorial that I've done, is not successful. Any ideas? 

It's going from my Cable Modem, to the 1750, then to the 18 port switch to the rest of the house that only has about 8-10 PCs connected to the network.

---

### Post by ThaddeusW on 2010-04-03
You want to create a network gateway otherwise known as a router. Bridging is something completely different.

Creating a router using your Poweredge is not hard but its  difficult to create a very secure router with a firewall that is also a server. You need to setup a dhcp server (dhcpd), configure iptables, SELinux and a few others.

Here is a good guide: [http://www.stanford.edu/~fenn/linux/]("http://www.stanford.edu/~fenn/linux/")

It is based on Fedora, not Ubuntu. But with a bit of patience and some searching you can easily follow the guide and apply it to your Ubuntu server.

May I ask why you want to use the server as a router? To me it is much more secure and far simpler to setup a separate router rather than using a full blown Linux install. If you want to go that route I highly recommend m0n0wall which is based on FreeBSD. You can install it on PC hardware using two or more network cards and configure it using a web browser. I have a m0n0wall router at home that is rock solid. Last time I had to shut it down is when the ancient Pentium 2 motherboard finally gave up the ghost. It now runs on a 600MHz Pentium 3 and has been up for over 8 months. It sounds like you might have a spare system or two that you could turn into a dedicated router. I would go that route.

---

### Post by aircftech on 2010-04-03
I am looking into the same thing. You might want to try this its from the 
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
 
 

You will need either two Ethernet ports, one for the incoming internet and 1 for the connection to the other computer, or a Wireless card for the incoming internet and an Ethernet port for the connection to the other computer. When logged into your computer right click on the network indicator in the top right hand corner, click on "Edit Connections..." select "Auto Eth0" and click "Edit..." then go to the "IPv4 Settings" tab and next to "Method:" select the drop down box and select the option that says "Shared to other computers". Restart your computer and then you will be able to just plug-in any computer to your Ethernet port to share the connection. 
 and yes what he said your not bridging your shareing

---

