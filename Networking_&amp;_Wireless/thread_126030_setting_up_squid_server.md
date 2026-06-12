---
title: "setting up squid server"
date: 2006-02-05
forum: Networking &amp; Wireless
---

### Post by eyebrowman92 on 2006-02-05
i just came accross an old computer in my basement from about 1996. the hdd has about 7 gigs on it, so i really didnt know wht to do with it. then i thought i might be able to set it up as a squid server. how can i do this?

---

### Post by nixclusive on 2006-02-05
I just downloaded squid:

apt-get install squid

the preconfiguration should work fine just make sure that you stop the service.

/etc/init.d/squid stop

edit the file /etc/squid/squid.conf

and un-comment the line:
#http_port 3128  
to
http_port 3128

Start the service: /etc/init.d/squid start
and set up your browser to use a proxy server listening on port 127.0.0.1:3128

Hey I'm a noob but I like to experiment :D more info at:
[http://www.squid-cache.org/](http://www.squid-cache.org/)

good luck.
I'm sure squid can do more than that.

---

### Post by eyebrowman92 on 2006-02-05
can i do this all just with a server install?

---

### Post by mips on 2006-02-06
Yes

---

