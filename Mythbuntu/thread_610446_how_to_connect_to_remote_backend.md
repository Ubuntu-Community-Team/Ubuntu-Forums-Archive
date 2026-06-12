---
title: "how to connect to remote backend"
date: 2007-11-12
forum: Mythbuntu
---

### Post by android6011 on 2007-11-12
I can't really find anything that says how to connect to  a backend from a frontend on another machine. what do you need to do on the backend and how do you setup the frontend? i have the backend setup in my room with its own frontend already, i just want to be able to connect from my laptop also

---

### Post by superm1 on 2007-11-12
Open up MCC, and enable the SQL service.
Open up mythtv-setup and change the two ip addresses on the general tab to be your network interface addresses.

Restart.

Get the information from /etc/mythtv/mysql.txt on the backend and put it in MCC on the frontend and hit test.
Apply the settings.
Start mythfrontend.

---

### Post by android6011 on 2007-11-13
the step before restart, i assume that is on the backend?

---

### Post by superm1 on 2007-11-13
Yes.

---

### Post by pasta514 on 2007-11-13
Having been through this myself I'd say it's not really clear to a newbie that it seems to need to be called out by IP addresses rather than host names.  Would save a lot questions if that could be more clear.  

What I mean is that I changed 'localhost' to the host name of my backend, but it didn't work.  Then changed to IP addr and no problem.  Then changed the backend IP address in the DHCP server to static for good measure. :)

---

### Post by superm1 on 2007-11-13
> **pasta514 said:**
> Having been through this myself I'd say it's not really clear to a newbie that it seems to need to be called out by IP addresses rather than host names.  Would save a lot questions if that could be more clear.  

What I mean is that I changed 'localhost' to the host name of my backend, but it didn't work.  Then changed to IP addr and no problem.  Then changed the backend IP address in the DHCP server to static for good measure. :)
This is highly dependent upon if your network can properly resolve hostnames.  Most off the shelf routers don't setup a DNS server that registers your hostname.

---

### Post by pasta514 on 2007-11-13
> **superm1 said:**
> This is highly dependent upon if your network can properly resolve hostnames.  Most off the shelf routers don't setup a DNS server that registers your hostname.

Fair enough, I just thought this part of the setup instructions could be clarified a bit.

---

### Post by superm1 on 2007-11-13
> **pasta514 said:**
> Fair enough, I just thought this part of the setup instructions could be clarified a bit.
Could you file a bug?  We can make sure to address this next time the pdf is remastered.

---

### Post by rshendershot on 2008-01-01
> **superm1 said:**
> This is highly dependent upon if your network can properly resolve hostnames.  Most off the shelf routers don't setup a DNS server that registers your hostname.

I'm using DD-WRT which modifies the LinkSys WRT54G common router to provide DNS using DNSMasq export-hosts.  This allowed me to remove all the external entries in /etc/hosts.

I have backend and frontend on different machines.

This was fine until the other day I changed the block of static addresses I was using from the default of 192.168.1.100. That's the address this router is configured to begin with by default and as a security measure I wanted to put my machines on different addresses. The backend was not running at that IP, btw.

Previously using hostname and it was working, now the only way I can get it to work is to put the IP address in MasterServerIP 

I can vnc, ssh, etc.  around my LAN from machine to machine to machine without any problems.  They all resolve hostnames just fine.  Except this one application.  As VMware windows machines come online they too are added to the dns and resolvable from each to each.

I'm at a loss of what setting in my system I may have missed.  Is it possible that Myth is resolving differently?

While I don't expect to change the IP addr again anytime soon I'd prefer to use hostname.  And thought I'd throw this out there perhaps it will help someone.

Thanks for any help!

---

