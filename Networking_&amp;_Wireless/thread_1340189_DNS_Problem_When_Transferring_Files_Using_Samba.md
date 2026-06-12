---
title: "DNS Problem When Transferring Files Using Samba"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by brohism on 2009-11-28
I have a Ubuntu Server on my network, which I use to store all my multimedia files, as well as personal storage for each of the users on the network.  Everybody can connect just fine (most computers are Windows, either Vista or 7).  However, when somebody is copying/streaming a file (such as a movie) over the network from the server to their computer, DNS lookups for all computers on the network seem to fail.  No computer is able to access web sites, regardless of whether that computer has any active connections to the Samba server.  However, if you access a site via IP address, or the DNS for that site is cached on the computer, then the page loads perfectly, with speed as if nothing else is happening on the network.

Anybody know what causes this and how I can fix it?  Thanks!

---

### Post by Iowan on 2009-11-28
Is the server also the DNS server - or is the router/modem (supposed to be) providing that service?

---

### Post by brohism on 2009-11-28
> **Iowan said:**
> Is the server also the DNS server - or is the router/modem (supposed to be) providing that service?

No, every computer and the server are set up to use OpenDNS.

---

### Post by Iowan on 2009-11-28
Is the server the gateway?
Guess I'm trying to determine if the server may be getting too busy to provide "something" for the machines. You mentioned that internet is available/useable if the address is cached.

---

### Post by brohism on 2009-11-28
> **Iowan said:**
> Is the server the gateway?
Guess I'm trying to determine if the server may be getting too busy to provide "something" for the machines. You mentioned that internet is available/useable if the address is cached.

No, the server doesn't act as a gateway.  It's a client to my router, it simply provides file sharing service with Samba.  The server doesn't seem too busy to provide other services, since SSH responds just fine. In fact, I don't even have a DNS server running on my Ubuntu server.

---

### Post by redmk2 on 2009-11-28
> **brohism said:**
> I have a Ubuntu Server on my network, which I use to store all my multimedia files, as well as personal storage for each of the users on the network.  Everybody can connect just fine (most computers are Windows, either Vista or 7).  However, when somebody is copying/streaming a file (such as a movie) over the network from the server to their computer, DNS lookups for all computers on the network seem to fail.  No computer is able to access web sites, regardless of whether that computer has any active connections to the Samba server.  However, if you access a site via IP address, or the DNS for that site is cached on the computer, then the page loads perfectly, with speed as if nothing else is happening on the network.

Anybody know what causes this and how I can fix it?  Thanks!

If *all *the computers on the network are having delays in DNS resolution, then it sounds like the network infrastructure is being overloaded.  

Normally the use of network switches rather than hubs reduces this problem.  Do you have a network hub or multiple switches in your network?  What physical devices are involved?  Can you provide the network topology?

---

### Post by brohism on 2009-11-28
> **redmk2 said:**
> If *all *the computers on the network are having delays in DNS resolution, then it sounds like the network infrastructure is being overloaded.  

Normally the use of network switches rather than hubs reduces this problem.  Do you have a network hub or multiple switches in your network?  What physical devices are involved?  Can you provide the network topology?

It doesn't seem to be overloaded since network requests that don't require DNS lookups work perfectly fine.  The network topology is as follows: FiOS modem/router at the top, with a Linksys 802.11N router with 4 port switch below that.  The server is connected via Ethernet to the Linksys router, and all the other computers are connected wirelessly to the Linksys router.

---

### Post by brohism on 2010-02-15
Still having this issue, anybody else have suggestions?  Just to recap, the Samba server doesn't provide any services beyond file sharing, and plays no part in the structure of the network beyond a client to the router.  It acts like any other computer on the network, and all computers (including the server) are set to use OpenDNS.

---

