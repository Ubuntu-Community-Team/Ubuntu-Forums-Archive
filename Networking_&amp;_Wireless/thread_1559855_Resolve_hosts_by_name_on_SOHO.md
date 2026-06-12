---
title: "Resolve hosts by name on SOHO"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by JohnDoe365 on 2010-08-24
I browsed through a lot of messages and advices, yet got not a single satisfying answer.
I think my question is fairly straight forward and a very common scenario.

Assume I bought a network printer, gave it a host name, address should be assigned by my cable or DSL router. Thats what DHCP and DNS is made for right?

Now I will print to that printer from my (Lucid) Kubuntu box and resolve it by it's hostname.

Problem: I can't ping it by printername, I can't ping it by printername.local
It works when I login my router, read out the IP address and hostname the printer registered at the routers DHCP-table and use that address.

What can be done that a router transfers the hostnames it has in it's IP-table to clients upon DHCP resolve AND whenever a client get's a new IP-Address?

* Static IP is unaceptable
* Setting up a DNS-Server is a no-go for a SOHO installation.

Is this problem related to this bug?
[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/80900](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/80900)

Further clarification: Isn't Avahi, dnsmasq & DNS-SD supposed to 'just work'? How can I configure to get local name resolution to work?

---

### Post by sptrsn on 2010-08-24
Irrespective of what you think the host name is, check the attached devices under dhcp to see what host name the router has assigned that device. I have a couple devices where it seems the router is just making stuff up as it goes. As long as that host name is listed on your router/gateway, it should be resolvable.

I've had very good luck using static ips on my printers in a dhcp network. Just list it in the DHCP Reservations List. Now the router won't assign that ip address to anything else.

---

### Post by JohnDoe365 on 2010-08-24
> **sptrsn said:**
> Irrespective of what you think the host name is, check the attached devices under dhcp to see what host name the router has assigned that device. I have a couple devices where it seems the router is just making stuff up as it goes. As long as that host name is listed on your router/gateway, it should be resolvable.


Tried that, but the devices where not pingable / browsable.

BTW. I noticed: Ubuntu laptop always registers fine with hostname at the router. When my latop is already running and I switch the network attached printer on and it registers by DHCP, I can ping/browse printer.local but I can't when it's allready up and running and I start my laptop.

The printer has the following features turned on:

* Dynamic DNS Registration
* UPnP: Multicast DNS

I think the later makes it visible to my laptop dispite avahi / MDNS / DNS-SD is not working properly on my latop.


Maybe I should mention I have a D-Link DIR-635 Router

---

### Post by sptrsn on 2010-08-24
My only other guess is to use wins. 
I have to admit I don't use it, and really don't have a good understanding of it. But you might have a look at this. 
[http://technet.microsoft.com/en-us/library/cc784180(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc784180(WS.10).aspx)

Here is a post on using wins with samba.
[http://ubuntuforums.org/showthread.php?t=65385&highlight=wins](http://ubuntuforums.org/showthread.php?t=65385&highlight=wins)

---

### Post by capscrew on 2010-08-24
> **sptrsn said:**
> My only other guess is to use wins. 
I have to admit I don't use it, and really don't have a good understanding of it. But you might have a look at this. 
[http://technet.microsoft.com/en-us/library/cc784180(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc784180(WS.10).aspx)

Here is a post on using wins with samba.
[http://ubuntuforums.org/showthread.php?t=65385&highlight=wins](http://ubuntuforums.org/showthread.php?t=65385&highlight=wins)

Host names can not be resolved with a WINS server.  WINS resolves NetBIOS (COMPUTER NAME, MACHINE NAME, etc.) names to IP addresses in domain networks.

Host name resolution resolves the host names of TCP/IP resources such as ping, http and ssh.  These do not connect through the NetBIOS interface.

---

### Post by sptrsn on 2010-08-24
There you go. Like I said, I don't understand wins. 

I have a DIR-655. I am not really sure it is a DNS server. I mean I know it does DNS relay for resolving names outside my firewall, but I have to admit I can't find anything about internal DNS services unless it just does it automatically.

I think this discussion supports my thinking. 
[http://serverfault.com/questions/18467/internal-dns-with-dlink-router](http://serverfault.com/questions/18467/internal-dns-with-dlink-router)

---

### Post by capscrew on 2010-08-24
> **sptrsn said:**
> There you go. Like I said, I don't understand wins. 

I have a DIR-655. I am not really sure it is a DNS server. I mean I know it does DNS relay for resolving names outside my firewall, but I have to admit I can't find anything about internal DNS services unless it just does it automatically.

The OP appears to have 2 DNS servers running.  This would be DNS and mDNS.  Avahi uses mDNS (multicast DNS).  This really should be used only when no DNS server is used.  I believe that conflicts like OP has stem form this, but I have no way to confirm it.

---

### Post by JohnDoe365 on 2010-08-24
After some more very carefully investigation it turned out to be an  incompatible combination of WiFi Access Point in Client Mode, operating in 802.11 g mode vs. WIFI MIMO  N-Router. Apparently the mDNS broadcast packages of the printer have not been  propagated to the Router.


 After I directly connected the printer to the LAN and/or used another  WIFI Access Point in client mode, mDNS actually works as advertised

---

### Post by Iowan on 2010-08-24
Would you consider the problem [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") or is the incompatibility still an issue to be resolved? (No pun intended.)

---

### Post by JohnDoe365 on 2010-08-25
> **Iowan said:**
> Would you consider the problem [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") or is the incompatibility still an issue to be resolved? (No pun intended.)

As the incompatibility is not at ubuntus side, this issue can be considered as solved.

BTW. for the record I reliably found the broadcast capability of the Airlive wl-5460ap v2 Access Point in client mode to be defective. Just if somebody has the same issues.

---

