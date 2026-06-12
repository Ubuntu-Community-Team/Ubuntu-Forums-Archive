---
title: "ADSL2MUE in bridged mode"
date: 2006-05-05
forum: Networking &amp; Wireless
---

### Post by watahero on 2006-05-05
I wanted to ask if anybody can direct me to were I can find how I can set up my linux box to use my linksys ADSL2MUE in bridged mode. Its connected through ethernet. I am new to linux and running ubuntu 5.10. btw my ISP uses rfc2364 pppoa

Thanx

---

### Post by mips on 2006-05-07
[QUOTE=watahero]I wanted to ask if anybody can direct me to were I can find how I can set up my linux box to use my linksys ADSL2MUE in bridged mode. Its connected through ethernet. I am new to linux and running ubuntu 5.10. btw my ISP uses rfc2364 pppoa

Thanx[/QUOTE]

Why would you want to use bridged mode ?

---

### Post by watahero on 2006-05-07
I want to make my linux box the router for my network. It has two network interfaces. So wanted to connect one to the modem in bridged mode and the other to the lan.

---

### Post by mips on 2006-05-07
Why dont you put your Linksys into routed mode so it does all the PPPoE and authentication stuff. Configure the Linux interface with a static ip going to the linksys. Create a new network for the other linux interface, install firewall, nat, dhcp and whatever your heart desires. The linux box will still be a router as it has to route between the two different networks.

You will have the same result if not better with a lot less hassles.

Alternatively if you want to do it your way then use pppoeconf on the ubuntu to establish a connection. This for me is the harder route to take but the choice is yours.

---

