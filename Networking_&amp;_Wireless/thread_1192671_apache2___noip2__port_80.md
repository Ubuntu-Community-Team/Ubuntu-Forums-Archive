---
title: "apache2   noip2  port 80"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by g-louis on 2009-06-20
Hi all 
I am trying to put a small web page on the internet which i am trying to run off a laptop jaunty 9.04 and a netgear router installed apache2 noip2 and open port 80 on laptop with firestarter and port forward in router. Localhost  "It works" 
192.168.0.2 "It works" 
127.0.0.1 "It works"

Firefox just can not load the page on the net" network error "

 daemon log reads noip2[2794]: myserver.zapto.org was already set to xx.xx.xx.95 the right ip address.   
 
"netstat -an | grep 80  tcp6  0  0 :::80   :::*   LISTEN "

[http://www.canyouseeme.org/](http://www.canyouseeme.org/) port 80 open
my ISP dont block port 80

nslookup myserver.zapto.org
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
Name:	myserver.zapto.org
Address: xx.xx.xx.95

If i put  "http://" and then do a nslookup i get a different ip address.


Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
Name:	[http://myserver.zapto.org](http://myserver.zapto.org) 
Address: 69.65.19.125

any one help please

regards graham

---

### Post by jhannah on 2009-06-24
The host lookup you are doing for "http://myserver.zapto.org" is actually looking up an invalid domain name. However, since zapto.org's DNS servers seem to be setup to return an IP that does a redirect based on the requested host, you are getting a response. The first look up you did for "myserver.zapto.org" is correct but when I look it up, I get a valid Internet IP address, x.x.x.212. Is this your external IP currently? It appears to be a Versatel IP. When I try to telnet to it on port 80, I get a connection refused which makes me think the issue lies with the port mapping you are doing on your netgear. 

The rest of your configuration sounds fine.

---

