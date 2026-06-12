---
title: "No internet, help please."
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by CCCody on 2008-12-29
I can connect to wireless. (Not mine.) But I can't connect to my home wired internet.

My Laptop (Inspiron 1525) is connected directly to the modem and the modem does work, I was using it on a windows machine a few hours ago.

All the Modem lights are on (Power, Ethernet, DSL, Internet.)

I don't know what to do. I'm new to Ubuntu. :(

---

### Post by Josep CA on 2008-12-29
I'm a noob in Ubuntu too but have you tried nslookup and dig?
Post the results.

---

### Post by CCCody on 2008-12-29
Server:		192.168.2.1
Address:	192.168.2.1#53

** server can't find l: NXDOMAIN


nslookup results. Not sure what it means.

---

### Post by Iowan on 2008-12-29
It's possible you have a winmodem that may need some additional software to run (unfortunately, it might also be one that has no "linmodem" equivalent).

---

### Post by Mintux on 2008-12-29
You say you can connect to wireless networks but not your wired one. I would like to know if you're connected to both at the same time.

In my experience Ubuntu will connect to the wired networks automatically, but if it is connected to a wifi network simultanously, programs wil prefer the wireless network (opposite to Windows, which will prefer the wired network). 

Also, as long as there is a configured wireless network within range, the network manager will connect to it, and use it over any connected wired network. If this is the case, try right-clicking on the network manager icon in the notification area and disabling the wireless network, then connect to the router and try to surf. 

If this doesn't solve your problem, open a command window (terminal) and write "ifconfig". Post the output here. You also should provide some basic information, such as what version of Ubuntu you are using and what type of network card you have if you want more help.

---

