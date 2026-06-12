---
title: "no-ip"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by community nerd on 2009-09-24
When i use no-ip, it takes me to the verizon login page which i suspect is the router. Anyone help to bypass it?

---

### Post by SoftwareExplorer on 2009-09-24
You're trying to set up a webserver right? 
Did you forward port 80. Also, try it through a proxy, some routers don't forward ports when they are talking to themselves.

If you need any more help, just ask. :P

---

### Post by community nerd on 2009-09-24
Well i am setting up a static ip so i can access my pc from anywhere but when i type in the host name all that comes up is the verizon login page, from my router.

---

### Post by SoftwareExplorer on 2009-09-24
First you need to understand that there is a difference between LAN and WAN.
LAN is local area network and is the network of computers in your house connected to your router, and your router.
Wan is world area network, and is the internet. 

Your router most likely uses NAT (network address translation).
It gives an address that usually starts with 192.168.0 to all the computers in the house with the router having 192.168.0.1. On the internet, websites communicate through your router using your routers WAN ip address. Then your router translates and routes the connection to your computer using Your computers LAN address. The website's server is blissfully unaware that it's requests are being translated at the other end, all it sees it the router's WAN ip address. This works all fine an good when the connection is established from behind the NAT, but the router has no clue what to do when a connection comes in. 

That's where port forwarding comes in. It makes a rule for the router to follow that says, all traffic coming in on port x send to this LAN address. For these rules to work, you have to make it so the computer always has the same address, however. Sometimes this is done with a static LAN address, or having a rule for the router to assign a specific lan address based on your computer's MAC address (which is unique and built into the hardware).

Once that is in place, then all traffic coming to the forwarded port on your router's WAN address will get where it is supposed to go. 

Next, there is the problem that the router's WAN ip is usually dynamic, and so you can't know what it's WAN ip will be from day to day. So that's where a service like no-ip would come in. An update every few minutes from either your computer or you router updates the address associated with whatever name.

Hope that helps.

---

### Post by community nerd on 2009-09-24
Thankyou. No-Ip is a free static ip host so i am trying to get it going with ubuntu

---

### Post by community nerd on 2009-09-24
So how do i do the forwarding. I was just on my router page but how would i know what port no-ip is coming in on.

---

### Post by SoftwareExplorer on 2009-09-24
No-ip will send all ports that come to your name to your router.
It depends on what you are trying to access on your computer. ssh? port 22 ...http? port 80 . . . https? port 443 (I think)

If you expected to see a web page when you go to your computer, then you would need to install a web server. A browser would be the wrong program to try to connect to your computer with if, for example, you wanted to control your computer with ssh.

You would forward ports at your routers page(s) that you were seeing earlier.

---

