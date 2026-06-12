---
title: "Configuring a netgar router network as DHCP server in ubuntu"
date: 2006-05-21
forum: Networking &amp; Wireless
---

### Post by orlox on 2006-05-21
Hi. I've been trying by myself, and did some searches over google, but still haven't been able to do what I pretend to do...This is, configuring my computer so it can share an internet connection using a netgear router. The network is composed of linuxes and window'ses....
If anyone could give me any insight on this, I'd truly appreciate it...

---

### Post by Slim Odds on 2006-05-21
[QUOTE=orlox]Hi. I've been trying by myself, and did some searches over google, but still haven't been able to do what I pretend to do...This is, configuring my computer so it can share an internet connection using a netgear router. The network is composed of linuxes and window'ses....
If anyone could give me any insight on this, I'd truly appreciate it...[/QUOTE]

Some actual details would be very helpful. Model #, network configuration, anything?

---

### Post by orlox on 2006-05-22
The router model is WGT634U. I currently have no network configured, so there's nothing to say about that...So i want to know if someone knows how to setup the network so my compuetr (with xubuntu dapper drake as the OS) can connect to internet and share it through the router to other pc's with either linux or windows...

---

### Post by RRS on 2006-05-22
Most of your configuration will be done in the router. We'll go on the assumption that you also have a dsl modem that you've been using to access the internet already with your Windows computer. Correct me if I'm wrong.

I'll also guess that your ISP provides DSL thru PPPoE since this is the most common and goes with your request for DHCP.

Connect the modems intranet(lan) port to the routers wan port. then connect your computers ethernet port to one of the routers lan ports and plug in the power cords. 

After any blinking LEDs turn solid green boot up your Linux computer and open a browser window with Firefox.

Type 192.168.0.1 in the address bar and "enter" At the login prompt; user= admin / password= "blank"

This should open the routers setup pages where you should be able to enter the appropriate settings according to your ISP. I've never worked with a Netgear so I can't help you with any details but I'm sure their website has an instruction page.

Hopefully this will get you on the right path but If you still need help please also provide your modems brand and model along with the specifics of you ISP (company and type of service)

---

### Post by Doghouse on 2006-05-22
Did the router come with a user manual?.  Or even a quick get started guild.  If it didn't get the user manual that came with the devise and READ.  It should only take you a few minutes to do the basic setup of the router.... that included renaming it, changing the password and setting the DHCP scope.  If you can follow basic instructions it really is that simple.

From there go to step two.... getting the unbuntu machine online. ;).  The windows machine should be a no brainer.


-K

---

