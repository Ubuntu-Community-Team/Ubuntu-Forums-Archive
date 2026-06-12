---
title: "SSH Connection Refused"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by 3m_g33k on 2010-04-02
Hey guys,

Im trying to set up SSH on ubuntu so that I can transfer files to and from home from work using scp.

Now the host machine runs 9.10 and the machine I am using to access is running 8.10. I've installed SSH on both machines and I can connect to the host machine on the local network i.e. ssh craig@192.168.1.4.

When I try to use my external IP (which I have determined is correct as I can run vncviewer with it) I get a connection refused error. I dont think I have any firewalls up and running and I think port 22 is up and running ok but have run out of any further ideas - help please [-o<

Thanks!

---

### Post by Iowan on 2010-04-02
Does the host machine connect directly to Internet - or (more likely) does it go through router/modem? You may need to set up port forwarding on the router/modem.

---

### Post by 3m_g33k on 2010-04-02
Heya, thanks for the reply!

Yeah It connects through a router - I've checked port 22 and its forwarded for a particular IP so I think I'm going to have to set up a static IP on the host machine and then forward port 22 on that?

It also seems my external IP has changed three times? During the course of today as I've been playing around with this I've now had three different external IP's??

---

### Post by bpalone on 2010-04-02
You are on dynamic IP from your ISP.  Go to DynDNS or DNSExit, or several others, and set up an account and use one of their free domain names (myplace.dnsexit.com).  Download and install their software for updating your IP address.

Now, I also recommend using a port other than 22 for sshing into your machine.  This will decrease the chance of being attacked through your ssh port.

Your ISP may also be blocking port 22.  Go to [http://www.canyouseeme.org/]("http://www.canyouseeme.org/") to check.

Hope this gets you going.

---

