---
title: "SMTP proxy"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by ilna on 2011-02-23
The goal is:

- my computer is running daemon which looks like SMTP-server listening to port 25
- all LAN clients' requests to the daemon are forwarded using my SMTP **client** account (host:port, login, password) somewhere outside the LAN).

How to?

P.S. I have used postfix before, but my new internet provider doesn't support reverse DNS for my IP, as a result many MTA are not happy with my MTA. And I still need internal SMTP server in my LAN.

---

### Post by lisati on 2011-02-23
Is changing ISP an option?

Not having a proper reverse DNS for an IP address is bad news: my email server doesn't like it because many spammers want to hide the true origin of their email. The lack of a reverse DNS removes one potential source of information to spam filtering software. An unfortunate side-effect of this that genuine emails are more easily blocked in error. Even a "standard" xx-xx-xx-xx-connection-type.isp-name style reverse DNS is better than not having any at all.

---

### Post by ilna on 2011-02-23
> **lisati said:**
> Is changing ISP an option?It is the reality.

> **lisati said:**
> Not having a proper reverse DNS for an IP address is bad news: my email server doesn't like it because many spammers want to hide the true origin of their email. The lack of a reverse DNS removes one potential source of information to spam filtering software. An unfortunate side-effect of this that genuine emails are more easily blocked in error. Even a "standard" xx-xx-xx-xx-connection-type.isp-name style reverse DNS is better than not having any at all.
I see, and at any case need a workaround of the problem as decribed in the first thread message - using my client account of external SMTP server. Have you some suggestions?

---

### Post by thesavager on 2011-02-23
What could be possible is that ... some internet providers don't allow you to use your own smtp-server ... and block port 25.
A way to get around this is to config SMTP-server to use a port above 1024.

:) give it a try

---

### Post by ilna on 2011-02-23
> **thesavager said:**
> What could be possible is that ... some internet providers don't allow you to use your own smtp-server ... and block port 25.
A way to get around this is to config SMTP-server to use a port above 1024.

:) give it a try
I have requested ISP to open port 25, and it is opened now. And it isn't my question :)

---

### Post by thesavager on 2011-02-23
Also a good free DNS server is available at [www.opendns.com](www.opendns.com). That works for me !
Opendns-servers:
208.67.222.222
208.67.220.220

good luck!

---

### Post by ilna on 2011-02-23
> **thesavager said:**
> Also a good free DNS server is available at [www.opendns.com](www.opendns.com). That works for me !
Opendns-servers:
208.67.222.222
208.67.220.220

good luck!
There isn't any relation between the problem and name servers being in use.

---

### Post by thesavager on 2011-02-23
Well ...I also use servers at home ... but i used opendns , together with a free subdomain. Then set your subdomain in opendns, so opendns does a redirect directly to your external ip-adres , called dynamic dns... then set your SMTP server to that subdomain .... that's how it's done.

---

### Post by ilna on 2011-02-23
> **thesavager said:**
> Well ...I also use servers at home ... but i used opendns , together with a free subdomain. Then set your subdomain in opendns, so opendns does a redirect directly to your external ip-adres , called dynamic dns... then set your SMTP server to that subdomain .... that's how it's done.
Please, stop at a second and reread first thread messages: the problem is **reverse** DNS converting absence: from IP to host. This converting is widely used by MTA to reduce spam streams. Reverse converting is a deal of **IP subnets owners** rather name servers' one.

---

### Post by thesavager on 2011-02-23
A much better idea is start using an SSH-tunnel , and tunnel all trafic through that tunnel , then you don't have any problems with you ISP anymore , and your trafic is also more secure ... my comment on using a port above 1024 is for security reasons mate , cause most hackers scan first the most "common" ports , which port 25 is one of them !
That also counts for the SSH-server , config it to use a port above 1024 ... this is only smart thinking mate ... don't make it those nasty people too easy to hack your server.

---

### Post by thesavager on 2011-02-23
Sorry mate i did my best ... but you don't see my message ...cause opendns supports reverse dns .. so when you use a free subdomain .... and you let opendns know you have it ...and you want to redirect all trafic from that subdomain to your computer at home ... then reverse dns should be working.
This is an old trick to fool the ISP, just use the opendns server, together with an subdomain, and set opendns to start using dyndns.
This is all FREE ...so no costs.

---

### Post by ilna on 2011-02-23
> **thesavager said:**
> A much better idea is start using an SSH-tunnel , and tunnel all trafic through that tunnel , then you don't have any problems with you ISP anymore , and your trafic is also more secure ... my comment on using a port above 1024 is for security reasons mate , cause most hackers scan first the most "common" ports , which port 25 is one of them !
That also counts for the SSH-server , config it to use a port above 1024 ... this is only smart thinking mate ... don't make it those nasty people too easy to hack your server.
Sorry, you are still speaking about anything other than a problem I have. I need a local SMTP server which forwards all outgoing messages to external SMTP server as this external server's client. That's all. Nothing more.

---

### Post by thesavager on 2011-02-23
> **ilna said:**
> Sorry, you are still speaking about anything other than a problem I have. I need a local SMTP server which forwards all outgoing messages to external SMTP server as this external server's client. That's all. Nothing more.

OK ... if you think like that ... no problem mate ... :) then i can't help you !

---

### Post by ilna on 2011-02-23
Have got an answer from postfix mailing list (and it has resolved my issue):
> 
Short version:
[http://www.hardwarefreak.com/postfix-adsl-relay-config.txt](http://www.hardwarefreak.com/postfix-adsl-relay-config.txt)

Long version:
[http://www.postfix.org/SASL_README.html#client_sasl](http://www.postfix.org/SASL_README.html#client_sasl)

---

