---
title: "cant connect; cant get IP"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by chickentravis on 2010-09-25
I have been using ubuntu for about a month now, and dont planon returning to windows.
I recently ran cat5e cable through my home and installed a 24-port linksys(ef412) switch. Since the swap i have been unable to connect to the network. I took the same computer to school and connected fine through their network. I installe Wicd and it told me that at my home i could not get an ip address. My dad's XP conects with no issue. tried diferent port, different wire and nothing changed
 
P.s. I wanted to install a Linksys wireless N router(wr160N) i already have, should i install it before or after the switch.

---

### Post by grahammechanical on 2010-09-25
I have just been checking the Ubuntu help doc under Internet and Networks - Ways of connecting - Wire (LAN). Have you looked through this document? It says this:

> If you are not connected, your network may not have a DHCP service (DHCP is responsible for assigning network settings). In this case, you will have to manually enter your network settings.

Right click the network icon and select Edit connections. Choose the Ethernet connections (eth0 or eth1 and select Edit. Go to IPv4 Settings and make sure that the method is set to Automatic (DCHP). Also check if you have ticked the box Connect automatically. 

Do not take me for being an expert but this is what I have seen in the Ubuntu help document.

regards

---

### Post by n.brenner on 2010-09-25
if u are using net manager and setting up static ip, then be sure to enter

your gateway ip...usually and with linksys 192.168.1.1 and hit enter

net manager will not take it if u dont.

I have 11 boxes  both ethernet and wireless and had a h of a time

sorting this out.   if u need help (n.brenner@hotmail.com)

put the router before the switch and in linksys u can reserve ip's

to mac addresses (not the operating sys)...

believe it or not but ubuntu and windows connect differently

I can also tell u how to have a server handle the internet and local

networking seperatly

---

