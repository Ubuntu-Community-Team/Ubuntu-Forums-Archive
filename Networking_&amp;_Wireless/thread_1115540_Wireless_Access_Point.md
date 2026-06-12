---
title: "Wireless Access Point"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by WitchCraft on 2009-04-03
Hi, question:

I have a cablemodem, and a wireless router attached to it.
Now I've installed a webserver on one of my computers, but when I type my public IP in the browser, I only get to the web login for my wireless router...

If I take the router out, I get to my webserver via the public IP.


That's not the only thing. I've installed a VNC server, and I can access my computer via the internet IF I take the router out.
I've set up port forwarding for all ports, and a test program confirms that they are open, but that doesn't help.

Another thing is, my quake server doesn't get a connection out except if I take the router out of the network...
I've added the quake ports to SUA/NAT (which normally solves the problem), but it didn't help...


What's wrong with my network settings?
Could that be caused by the cable modem not being in bridge mode, or is that a bug in the wireless router?

---

### Post by bukwirm on 2009-04-03
Make sure you're forwarding the ports to the right computers - it's a silly mistake, but I've done it before.
You might also need to disable remote administration (or whatever it is called on your router) on your router.

What kind of modem and router do you have?

---

### Post by WitchCraft on 2009-04-04
> **bukwirm said:**
> Make sure you're forwarding the ports to the right computers - it's a silly mistake, but I've done it before.
You might also need to disable remote administration (or whatever it is called on your router) on your router.
 
What kind of modem and router do you have?
 
I have a ZyAir B 2000 wireless router and a ARRIS TM502A cable modem.
The IP NAT forwards to is correct, 192.168.1.33
 
I fear it's a bug in the router, as there are other bugs in it...
The other possibility might be that the modem is not in bridge mode, but I don't know how to access the modem, since somebody else installed it, and I have no documentation...

---

### Post by WitchCraft on 2009-04-04
> 
How can I configure the modem to forward or open some ports to connect to the Internet with a few of my games?
 
All ARRIS modems will pass all port traffic unless provisioned to block ports by your cable operator or your service provider.
For further assistance, please contact your service provider regarding this issue. 

 
 
I just found the above.
Since it did work with another router, I think I'm gonna call the router company and demand my money back...

---

