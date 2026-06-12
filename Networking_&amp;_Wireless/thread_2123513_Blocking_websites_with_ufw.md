---
title: "Blocking websites with ufw"
date: 2013-03-08
forum: Networking &amp; Wireless
---

### Post by oksendal on 2013-03-08
Hi.

I have set up a 12.04 server version of ubuntu as a router, using iptables or ufw. It is set up virtually using VMware, where i have the router, a Windows 2008 server and a win 7 client.
I have been trying to find a way to block facebook and other pages, but without a solution.
One problem that I have found is that facebook uses a https page for the login, so I need to be able to block https sites as well as http.
Is it possible to do this using ufw, or do I have to use iptables or something else.

Oksendal

---

### Post by slickymaster on 2013-03-08
_With IPTables:_
```
sudo iptables -A OUTPUT -d <ip address> -j DROP
```
This syntax also supports a wildcard. By typing an IP with a zero in it, you are effectively blocking the entire span of that field. For example, 192.168.13.0 references the IP range of 192.168.13.1 to 192.168.13.254

_With UFW:_
```
sudo ufw deny from <ip address>
```
To block an IP range you should do:
```
sudo ufw deny from 192.168.13.1/254
```

---

### Post by oksendal on 2013-03-11
Hi.

It did not work. Might it be because I have enabled IP-Masquerading on the server/router?
As you might have understood I am pretty new to ubuntu and linux. 
Is there a way you can use urls for blocking, or is blocking with IPs the best way to do it?

---

### Post by albandy on 2013-03-11
Of course you can use iptables for doing this, but in web filtering (you want to block some pages) iptables are not the best option. I think using squid with squidguard in transparent mode is a better option for you.

[http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)

---

### Post by slickymaster on 2013-03-11
[The Ubuntu Server Guide shows information on how to implement IP masquerading on ufw]("http://books.google.pt/books?id=NxUMMBGsn4sC&pg=PA411&lpg=PA411&dq=IP-Masquerading+and+ufw&source=bl&ots=5Cn6nN0kjo&sig=6GtNo6AQCaftoPma1idaJ_Y_bd8&hl=pt-PT&sa=X&ei=Fcc9UZ7IJq-A7QarjoHABA&ved=0CHcQ6AEwCA").

[IP Tables Primer]("http://bodhizazen.net/Tutorials/iptables/")

---

### Post by oksendal on 2013-03-11
> **albandy said:**
> Of course you can use iptables for doing this, but in web filtering (you want to block some pages) iptables are not the best option. I think using squid with squidguard in transparent mode is a better option for you.

[http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)


Is it possible to block https sites using squid?
I have not yet mentioned that I am running the server without gui, just command line. Does this affect any functionality when it comes to blocking pages?

---

### Post by vasa1 on 2013-03-11
> **oksendal said:**
> Is it possible to block https sites ...
You should add the bit about wanting to block http**s** sites to your original post.

---

### Post by slickymaster on 2013-03-11
Blocking websites can be done with squid dstdomain access lists (ACL).

Edit the **squid.conf** configuration file:
```
gksudo geany /etc/squid/squid.conf
```
Adding these three lines to it
```
acl lan src 192.168.10.0/24                           # client ip range to block web sites
acl bad_sites dstdomain .foo.com .fooo.com            # Block two domains in single acl
http_reply_access deny bad_sites lan
```

This, will make squid server deny browsing if anyone from the acl "lan" access the domain foo.com and fooo.com. In any case you should keep in mind that squid will also deny all sub domains of the blocked domain.

---

### Post by oksendal on 2013-05-23
Does it matter where in the squid.conf file i add this?
What do I do to all the documentation that is already there, is all of that commented so that it's not being used?



> **slickymaster said:**
> Blocking websites can be done with squid dstdomain access lists (ACL).

Edit the **squid.conf** configuration file:
```
gksudo geany /etc/squid/squid.conf
```
Adding these three lines to it
```
acl lan src 192.168.10.0/24                           # client ip range to block web sites
acl bad_sites dstdomain .foo.com .fooo.com            # Block two domains in single acl
http_reply_access deny bad_sites lan
```

This, will make squid server deny browsing if anyone from the acl "lan" access the domain foo.com and fooo.com. In any case you should keep in mind that squid will also deny all sub domains of the blocked domain.

---

### Post by SeijiSensei on 2013-05-23
> **oksendal said:**
> Is it possible to block https sites using squid?

Yes, but it takes quite a bit of work.  Read [this]("http://wiki.squid-cache.org/Features/SslBump") for more details.  I'm testing the current 3.3 version now to see how well it works with transparent proxying of HTTPS requests.  I've gotten 3.2 to work with SSLBump, but it requires that the browser be configured to use the proxy for HTTPS requests.  

None of my servers and gateways run GUIs.  In fact the server version of Ubuntu comes without any GUI at all.

---

