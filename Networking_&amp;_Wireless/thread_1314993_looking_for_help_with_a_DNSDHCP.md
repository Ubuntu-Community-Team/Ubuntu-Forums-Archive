---
title: "looking for help with a DNS/DHCP"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2009-11-04
I'm setting up a little home server.

It will connect to...

DD-WRT access point
1 windows laptop
1 ubuntu laptop
xbox 360
wii
iPhone

I need a full walk though for this.
I tried bind9 and it broke.
dnsmasq looks good but I don't know how to configure it.

---

### Post by mpokrywka on 2009-11-05
Important question: what do you mean by "a little home server"?
What service will it provide? I ask this, because you mentioned DD-WRT, which by itself can act as a router, dns and dhcp server...

---

### Post by Lars Noodén on 2009-11-05
> **wlraider70 said:**
> I'm setting up a little home server.

It will connect to...

DD-WRT access point
1 windows laptop
1 ubuntu laptop
xbox 360
wii
iPhone

I need a full walk though for this.
I tried bind9 and it broke.
dnsmasq looks good but I don't know how to configure it.

DD-WRT should provide DHCP service for you so it should not be necessary to have a second one inside your LAN:
[http://www.dd-wrt.com/wiki/index.php/Tutorials](http://www.dd-wrt.com/wiki/index.php/Tutorials)
[http://www.dd-wrt.com/wiki/index.php/DNSMasq_as_DHCP_server](http://www.dd-wrt.com/wiki/index.php/DNSMasq_as_DHCP_server)

dnsmasq can also do caching, so that repeat requests are faster.

---

### Post by wlraider70 on 2009-11-05
Im going to do some things like... 

share media,
ssh in from the internet
vnc from inside my network **i woul dlike to use a computer name not an ip.
backup files from clients
FTP or some similar method to get documents from ANY browser.



I don't have it all planed out, but i know i would like to use a name not a 10.10...

---

### Post by Iowan on 2009-11-05
I replaced **dhcp3** with **dnsmasq** when I upgraded my server.  Configuration seems straightforward. [Here]("http://http://www.thekelleys.org.uk/dnsmasq/doc.html") is more information.  I particularly like how it links DNS with DHCP. A new machine on the network is accessible by hostname. Network printer and LAMP server get static lease.  It does what my small network needs.

---

### Post by Lars Noodén on 2009-11-06
I would second @ Iowan's suggestion of dnsmasq, though dhcpd is quite usable. Just to be clear, DD-WRT has a built-in DHCP server.  

However, please make the topology of your planned network more clear so that it would be possible to help.

Is it like this?

```

**A**.
                                    +-- desktop2
                                    |
Internet---DD-WRT---Ubuntu Server---+-- desktop1
                                    |
                                    +-- notebook1, etc
                                    |
                                    +-- gameconsole1, etc


```

Or this?

```

**B**.
                    +-- desktop2
                    |
Internet---DD-WRT---+-- desktop1
                    |
                    +-- notebook1, etc
                    |
                    +-- gameconsole1, etc


```

---

### Post by wlraider70 on 2009-11-06
My setup is "B".


I set up a few host entries in the DD-WRT. It seems good.

Lars do you think i should have both the dhcp and dns on the server?
what are the draw back to doing it on the router?
this seems easier, but id like to do it right.

---

### Post by redmk2 on 2009-11-06
> **wlraider70 said:**
> My setup is "B".
... do you think i should have both the dhcp and dns on the server?


Are you planning on creating a "server"?

You refer to "the server", but setup "B" does not show a separate "server", such as a file/print server.   Is this to be a separate host in your network?   

FYI, The DHCP/DNS on DD-WRT ***is*** DNSMasq.
> 


what are the draw back to doing it on the router?
this seems easier, but id like to do it right.


In my opinion these services should be on an edge host.  The DD-WRT device is an example of that.  

If you have a separate file or print server that also provides DHCP/DNS services and for some reason it is taken off line, your other hosts will loose connectivity.  

On the other hand if these services are hosted by the unit that specifically provides network connectivity (and that is the intended mission of the DD-WRT unit), then the individual hosts in the network can come and go without affecting each other.

---

### Post by wlraider70 on 2009-11-07
Well the way that i have it set up is...



ISP > WW-DRT router > connections to... ubuntu server, Windows box, ububtu lappy, game systems.


I didn't pick A because im not trying to set it up like my windows server at work. where if its not on then the clients don't have internet access.

I want the server to be able to sync files, server files and stuff.
I can do that right?

---

### Post by Lars Noodén on 2009-11-09
> **wlraider70 said:**
> Well the way that i have it set up is...



ISP > WW-DRT router > connections to... ubuntu server, Windows box, ububtu lappy, game systems.

...

Ok.  The dhcp is taken care of, [WW-DRT uses Dnsmasq](http://www.dd-wrt.com/wiki/index.php/DNSMasq_as_DHCP_server) already.

---

### Post by Lars Noodén on 2009-11-09
> **wlraider70 said:**
> 
I want the server to be able to sync files, server files and stuff.
I can do that right?

You'll need a larger system than your router for that.  For file sharing and syncing some of the easier options include SSHFS, WebDAV+HTTPS, and Samba.

---

