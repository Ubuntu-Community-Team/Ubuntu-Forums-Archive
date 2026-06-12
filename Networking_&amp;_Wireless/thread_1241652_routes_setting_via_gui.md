---
title: "routes setting via gui"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by spork on 2009-08-16
Hi 
To set up a default gateway from the command line:
"sudo route add default gw 192.168.1.1"  --- no problem
I am trying to set up a PC for a friend that doesn't like command lines and I can't get this to work by using the "NetworkManager/Edit Connections/Wireless/.../edit/IPv4 settings" method.
My static IP is 192.168.1.8
My default gateway is 192.168.1.1
I can't figure out what I'm doing wrong
Does anyone know of a howto concerning static IP address setup using Networkmanager for idiots?
Thanks
Spork

---

### Post by mhgsys on 2009-08-16
Do I understand correctly?:

 You already assigned a static ip adress and added your default gateway correctly, 

did you set the netmask to 255.255.255.0 ?


I guess your question is how to get the www working like this.

If that's the case; you should also add your dns manually.

You can find the correct dns setting in your router setup, or you can copy them when you got a working connection due to dhcp.
(right click, connection information,.. your primary dns and secondary dns will show up.)

Use these settings in your manual input, and everything should be working correctly.
EDIT: use a , to divide the primary and secondary dns. 

f.e  194.134.5.5,194.1430.97

---

