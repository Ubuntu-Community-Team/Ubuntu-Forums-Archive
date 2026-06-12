---
title: "How to determine which port needs opening"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by jabrown65 on 2011-08-02
I am unable to open my webmail on my small business computers (all ubuntu 10.04 LTS using a Billion router) but am able to access it from my home computers (also ubuntu 10.04 LTS but with a different router).

The most likely problem is obviously that the firewall in the router is blocking access. I know how to open ports in the router's firewall, but how do I determine which port or ports need to be opened?

I have asked my email provider, and that have replied that the port can vary and I need to get my technical support people to do it. Obviously they struggle to understand the concept of 'small business"!

Suggestions?

---

### Post by new_tolinux on 2011-08-02
You say that it is webmail, which means that you are probably connecting to [http://here.the.address](http://here.the.address) or an [https://here.the.address](https://here.the.address)

By default normal HTTP-traffic goes on port 80 and HTTPS-traffic goes on port 443
Only exception: if you are connecting to your webmail with something like [http://here.the.address:1234](http://here.the.address:1234) or [https://here.the.address:1234](https://here.the.address:1234) you should open the port number which you specify there

---

### Post by psusi on 2011-08-02
Opening ports means allowing other computers to connect to you.  Web traffic, including webmail, is an outgoing connection, which is normally unrestricted.

---

### Post by HermanAB on 2011-08-03
All the ports are listed in /etc/services, so you can do:
$ grep http /etc/services

Your webmail is hosted by your ISP?  Can your business computers access the web?  If so, they should be able to access your webmail.

My guess is that you have a DNS problem, not a firewall/routing problem.  In other words, I guess that your business computers cannot resolve the webmail address - try the IP address.

---

### Post by new_tolinux on 2011-08-03
Probably I thought a step too far ;)
I actually was thinking about his webmail runing at home on a server...

---

### Post by jabrown65 on 2011-08-06
Thanks. Yes, it was [https://here.the.address:1234](https://here.the.address:1234) type so I allowed the relevant outgoing port and now its all working!

Thanks again.

---

