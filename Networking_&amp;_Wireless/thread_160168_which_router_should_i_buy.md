---
title: "which router should i buy?"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by ice60 on 2006-04-14
hi, i want to get a new router because the one i have now doesn't work with Linux, i have got it working, but i want something which will work when i install Dapper.

i have a DSL connection and need a NAT router that supports pppoe. i don't want a wireless router. i think that's it :-k thanks. :)

---

### Post by az on 2006-04-14
[QUOTE=ice60]hi, i want to get a new router because the one i have now doesn't work with Linux, i have got it working, but i want something which will work when i install Dapper.

i have a DSL connection and need a NAT router that supports pppoe. i don't want a wireless router. i think that's it :-k thanks. :)[/QUOTE]
Any router with a web interface will work fine.


EDIT:  Some routers which are configured using windows software may have linux equivalents.  What kind of router do you currently have?

---

### Post by ice60 on 2006-04-14
[QUOTE=azz]Any router with a web interface will work fine.[/QUOTE]
can you give me a hint which one i should get? i don't know what you're talking about :(

---

### Post by ice60 on 2006-04-14
do routers come with an ethernet card i can plug in? because the only ethernet socket i can see is from this vvv and i think that's an internal modem which doesn't work with Linux. atm i use an usb speedtouch modem

description: Communication controller
             product: HSF 56k HSFi Modem
             vendor: Conexant
             physical id: 9
             bus info: pci@00:09.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:ee000000-ee00ffff ioport:d000-d007 irq:5

or are they USB instead :confused: thanks. :)

---

### Post by stuporglue on 2006-04-14
I recently bought a CompUSA branded 4 port router for ~$25 and liked it a lot. It worked great, and the web-based configuration pages were better than those of the Netgear I was using. EDIT: Thought it was linksys, it's a Netgear

A typical 4 port router has 5 ethernet ports. One is for the incomming internet connection, the other four are for plugging in computers 

So, if you have access to a CompUSA, that's what I'd recomend. It has a checkbox for pppoe too, but I don't use it, so I can't say if it works for sure, but I bet it does.

---

### Post by ice60 on 2006-04-14
OK thanks, i think i get it - any NAT router will work - Linksys, D-Link, NETGEAR etc etc. and if it uses an ethernet socket i'll have to buy an ethernet card too!

---

### Post by stuporglue on 2006-04-14
> OK thanks, i think i get it - any NAT router will work - Linksys, D-Link, NETGEAR etc etc. and if it uses an ethernet socket i'll have to buy an ethernet card too!

Yeah. The main differences are going to be speed (10/100 or GigE or whatever), price, and the quality of the configuration tools. 

Most have webbased configuration. You plug in a computer and visit a specific IP address, and the router is serving some web page where you configure the options. 

I have a Netgear (thought it was a linksys in a previous post, it's a netgear) and the interface stinks. Some parts of it regularly fail to load. Once it's configured it works fine though. 

Some routers have features like having a place to put a dyndns username/password, and some have better routing configuration tools. Some even let you telnet or ssh in. 

That said, most any one will do the job.

---

### Post by ice60 on 2006-04-14
thanks for the help. i was getting confused about the ethernet bit, but when you said "4 port router" i see where i was getting confused now :rolleyes: thanks :cool:

---

