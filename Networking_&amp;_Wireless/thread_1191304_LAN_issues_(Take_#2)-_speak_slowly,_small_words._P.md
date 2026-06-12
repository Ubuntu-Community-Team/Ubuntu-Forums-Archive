---
title: "LAN issues (Take #2)- speak slowly, small words. Please. :)"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by Icky_Ev on 2009-06-18
I have made no progress with "naming" my private webserver, and could really use a shove in the right direction. 

Situation: Currently running a LAMP/SAMBA server on Jaunty. This server and all the computers harnessed to it are strictly an internal network with no internet exposure. 

They are all connected through a router. SAMBA is configured for WINS and hangs off the router with an IP lease (the server is still configured for DHCP) 

Everything is up and running fine, but it's necessary to access the server via its IP. 

I would really rather be able to access it via a name. IE: [http://pretzel](http://pretzel). 

I can get this to work IF the server is hanging off the internet. Without the internet connection, it's back to the raw IP. 

I've been all over the internet and these forums and honestly have not found anything that speaks to this specific scenario (everything I've found assumes an internet connection is in play). BINDs, DNS, hosts, avahai conflicts, resolv.conf ect- been in all of them, haven't been able to cobble anything functional together. 

Can anyone point me in the direction of a tutorial specifically for private LANs that do NOT have an internet connection involved? Offer some guidance? Reveal to me that what I'm attempting to do cannot actually be done so to stop trying? ;)

---

### Post by DGortze380 on 2009-06-18
Have you added the correct workgroup and netbios to your samba.conf?
Do you have firewalls running anywhere?

For reference: [http://www.mail-archive.com/samba@lists.samba.org/msg97695.html](http://www.mail-archive.com/samba@lists.samba.org/msg97695.html)

---

### Post by Icky_Ev on 2009-06-18
Yes, SAMBA is working just fine, and actually finds the server by name (now that I think about it- that was a recent victory ;)) 

No firewalls to be seen. 

We're also running a mySQL DB with a browser interface and to access it everyone has to key in the IP addy, not the server's name. Same if I Telnet into the server. Can't get in by name- have to get in by IP. 

IE:

[http://192.1.1.100/database](http://192.1.1.100/database)

I'd rather have:

[http://server/database](http://server/database)

---

### Post by doas777 on 2009-06-18
what you are looking for is a DNS server. bind9 is the one I've been using and it has been quite reliable for some time. DNS is a service that maps names to IP addresses. when I type [www.ubuntuforums.org]("http://www.ubuntuforums.org") into the browser, firefox asks the dns server what the ip address of ubuntuforums.org is. then it creates a connection, and I can peruse.

here is a quick intro: [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

look into forwarders. that way, you can configure your clients to point to your dns server, and if the name is not found locally, it can be configured to pass the query onto a ISP dns server, and proxy the reply back to the client.

when i put in [www.ubuntuforums.org]("http://www.ubuntuforums.org"), my laptop asks my dns server what the ip address is. my server doesn't know, so it asks my isps dns server. the isp replies to my server, and my server tells my laptop. that way, I can make queries for both my lan and the internet but only configure one DNS server on the clients. 

on your clients, you can configure them in /etc/resolv.conf, or in windows, set it in your network connection properties for Internet Protocol.

btw, I think samba may be a dead end for http name resolution. I may be wrong, but i think it only works for smb/cifs.

good luck

---

### Post by Iowan on 2009-06-18
Quick/dirty method is to add entry in **hosts** file (on each computer) that equates server name with IP address.  Is the server address static or dynamic _lease_? The **hosts** file entry will only work as long as the server gets the same address.
Another method would be to install DNSMasq to act as DHCP and DNS server.  It's in repos, but that assumes internet connection...

---

### Post by Icky_Ev on 2009-06-18
Thanks for the feedback. :)

I'm familiar with the generalities DNS and like I said, was able to successfully configure everything to work WITH an internet connection. 

Without an internet connection the server acts lost. I've tinkered with the hosts, resolv, interfaces ect to try to convince it to point at itself, but it's not buying. Tried forwarding things through the router, not working. I've tried BIND9 and DNSMASQ. All of the above assumes I've done it correctly. Big assumption. ;)

Maybe this will offer a clue: I cannot #host localhost or #host (server name). 

I was really just hoping to stumble across a quick tutorial or "do A,B,C" but like I said, everything assumes there's an internet connection. 

Now that I have SAMBA up and running (I abandoned the DNS project since it was "functional" in favor of getting SAMBA running) maybe I'll see if that helps it see things...

---

### Post by DGortze380 on 2009-06-19
> **Iowan said:**
> Quick/dirty method is to add entry in **hosts** file (on each computer) that equates server name with IP address.  Is the server address static or dynamic _lease_? The **hosts** file entry will only work as long as the server gets the same address.
Another method would be to install DNSMasq to act as DHCP and DNS server.  It's in repos, but that assumes internet connection...

He has a dynamic address on the server, which is why I skipped this to begin with.

But depending on the number of hosts on your network. It may be easiest to configure a static address for your server and push a hosts file to each client. That's what I do at home.

---

### Post by Iowan on 2009-06-19
If the DHCP server is capable, the server can be set up with a static lease - based on MAC address. The server can remain configured for DHCP, but it will have a fixed address.

---

