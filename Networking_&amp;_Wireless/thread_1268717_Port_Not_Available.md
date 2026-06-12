---
title: "Port Not Available"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by NertSkull on 2009-09-17
So I'm trying to set up an ftp server on my desktop but I can't seem to be able to get port 21 open.  If I forward the port on my router (Linksys WRT54GS) to my Vista laptop the port opens fine when I check it with canyouseeme.org

But in ubuntu when I go to canyouseeme.org the port is closed and I get the message "connection refused" which I think means something is actively denying the port, not just timing out.

I'm pretty sure my firewall is disabled (although I could be wrong, but I was also under the impression firewall is off by default in a fresh ubuntu install)

Any ideas what I am doing wrong?  Because I can get it to my Vista laptop I didn't think it was my router.  But I dual boot my desktop into XP as well and I can't get it to recognize port 21 in XP either.  So now I wonder if its my desktop, or my router.  But it definitely connects to the vista laptop. Even if I put the desktop in DMZ mode through the router I don't get the port recognized.  I can't figure it out.

Any thoughts??

---

### Post by NertSkull on 2009-09-17
So I tried some other things and I've discovered that yes, I can get port 21 accessible in my vista installation.  But I can not get any other ports.  So maybe this isn't an ubuntu/vista/xp problem but a router problem?

Any thoughts?  I'm suspect I'm just really lacking in my knowledge of routers/networking etc because I'm totally at a loss.

---

### Post by zyban03 on 2009-09-17
You may want to check on your Ubuntu Box that you have the FTP server running. Also you may want to try and see if you can connect with Secure FTP via port 22.
Plenty of HowTo's out there that will explain how to set that up.

---

### Post by Iowan on 2009-09-17
Probably silly question, but...
Did you re-direct the port forward to the Ubuntu box?

---

### Post by NertSkull on 2009-09-18
Yeah the ports are forwarded correctly.

But I've found the problem.  I don't know if there is a fix though.  Hopefully someone will have an idea.

It appears that the modem my ISP provided me sets up its own DHCP server that feeds my router.  My router then sets up its own DHCP server as well where I have been forwarding my ports.  The modem from my ISP is a black hole of death and has ZERO configuration options.  So I can't forward any ports to my router, but I can forward my router ports.  But my router gains its IP from the modem, so the modem can't send requests on to the router.

I don't know if I explained that very well.  But at least it looks like its not an Ubuntu problem.  

The only thing I can think of is to get a new DSL modem.  Anyone have any other thoughts?

---

