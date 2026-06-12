---
title: "DNS Proxy (behind firewall)"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by shaferwr on 2010-04-19
All,
 
Here is my dilemma:
 
I have a small network behind a firewall.  The network consists of 2 servers and 2 clients separated by a router.  On the top side of the router, I have a firewall with a connection to our corporate network.  Our corporate network, is of course, firewalled from the internet.
 
So basically I have a router with three interfaces.  One goes to the client network, one goes to the server network, and one goes to the lab firewall.
 
My two servers are a DHCP server and a DNS server.  The clients request a DHCP address, and the DHCP server in turn reports to the DNS server that it just issued an IP address to "pc.example.com".  Now I can browse "pc.example.com" with the new DCHP IP address.  This works for my local network within my lab, and also within my corporate network, but not for the internet.  I can't do an nslookup on [www.ubuntuforums.org]("http://www.ubuntuforums.org"), for instance.
 
The problem that I'm having is my corporate network requires us to use a proxy server for all web browsing.  So, in my firefox browser, I have the proxy server set up to proxy all web connections.  This works great for firefox, but if I use the apt-get command in the terminal window, nothing works because the machines can't resolve us.archive.ubuntu.com.
 
I gave you all this information to find out if there is a way to proxy a DNS connection directly on the internet.  If so, would I have to use those internet DNS Servers as my forwarders on my DNS server or would I proxy it somehow through the internet?
 
Any help would be greatly appreciated. I'm willing to try all suggestions at this point.
 
-Will

---

