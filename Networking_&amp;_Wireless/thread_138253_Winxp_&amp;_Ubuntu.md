---
title: "Winxp &amp; Ubuntu"
date: 2006-03-01
forum: Networking &amp; Wireless
---

### Post by Arinux on 2006-03-01
Hey all, here is the situation i want everyone to figure out.My desktop pc has got winxp,and my laptop has got ubuntu.I connect to the net through my desktop.I got two lan cards one for the isp & other for the laptop.Is there any way i can connect my laptop to the net also?Like may be net sharing or some proxy!Any ideas on this??

---

### Post by Dylan103 on 2006-03-01
Well, I had a router previously (for my ps2 online). So I hooked my Modem upto my router, and from the router, i had 3 ethernet cords, 1 going to my PC(main) and 1 going to my PS2, and then 1 connecting to my current PC, and it automaticlay bridged( I belive ) and setup a server. Oh yes, my other pc is windows that I had for awhile, and this computer brand new, has ubuntu.

---

### Post by Razorback on 2006-03-01
You can share your XP box connection with ICS (internet Connection Sharing).  Under advanced in your connection properties window in XP there is a check box for this.  Your XP box will then assign the linux box an address by DHCP and allow access for your laptop thru your LAN connection.

---

### Post by Arinux on 2006-03-02
Nope its not working! both the Lans are connected , and win xp ubuntu is configured by DHCP, but can't access net from ubuntu any other solutions?

---

### Post by Razorback on 2006-03-02
Did you enable Internet sharing on the XP box?  If you did your XP box LAN nic (not the one connected to the internet) should have an IP of 192.168.0.1 by default and your Linux box should have 192.168.0.### address.  Your linux box should be set to DHCP.  Check to see if your pcs are communicating.  NOTE: You should have ICS configured on the nic connected to the internet.

Another question is: are you connecting your laptop nic directly to your xp box nic?  If so, are you using a crossover cable?

---

