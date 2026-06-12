---
title: "Transferring data from pc to pc via a router"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by vaxetihirr on 2009-06-21
This is the network setup i have in my home in the UK

I have a cable internet service point coming into my house.

From the service point i have a coaxial cable going to a broadband modem.

From the broadband modem i have the coaxial cable,a cable to the mains and a cble to a TrendNet router.

From the TrendNet router i have a cable to the mains, one to the broanband router and one to the back of my desktop.

I also have the wireless antenna plugged in.

The Desktop is a Packard Bell iMedia J2411 unmodified http://support.thetechguys.com/layout.aspx?ID={2dd47f67-19af-4c9c-a8e0-1eb7c02dd7b0}&CatID={82e9f4d8-3ceb-41de-ad53-032a5e5e485c}

The laptop is a Packard Bell Easynote MV46-008 laptop also unmodified
http://support.thetechguys.com/layout.aspx?ID={a4087915-7151-4fff-8803-0bae28937fc7}&CatID={aef50a3a-fc31-4993-ad71-adffeb5a488a}

Both pcs have Ubuntu 8.04 LTS release installed on them.

The desktop is showing connected to the router and has an IP address of 192.168.10.101

The laptop is showing connected to the router wirelessly and has an IP address of 192.168.10.102

Both pcs are detecting a Default Route of 192.168.10.1
I can ping the laptop from the desktop and vice versa using Network Tools in the Administration menu.

I even impressed myself by typing the following command successfully into the command line: ping -c 4 (IP address) It never loses a packet.

But is there a way of transferring data from the desktop to the laptop and vice versa? Because I'm getting sick and tired of putting data on memory sticks and actually getting some excercise !!!

---

### Post by dmizer on 2009-06-22
Please see the 4th link in my sig. :)

If you want both computers to both host and receive files, you will have to set up both computers as both a server and a client.

---

