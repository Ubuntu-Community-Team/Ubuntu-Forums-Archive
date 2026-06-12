---
title: "resolv.conf? DNS alternative"
date: 2012-06-22
forum: Networking &amp; Wireless
---

### Post by enterdavertex on 2012-06-22
I have a question for everyone, is there a way that i could enable 2 DNS server for my resolv.conf? basically it goes like : 
-if the first DNS server return an error it do not look into the second one
the main point of doing this is to keep low one of my server his has all the time DNS query, and use only my main domain DNS only if the query has no awnser from the outside ( 8.8.8.8 ). 

This is for monitoring(Nagios) some computer over my own network and some customer computer all around the internet Network. 

Thank your for your help.

---

### Post by CharlesA on 2012-06-22
Add it to /etc/network/interfaces.

Example here:
[http://ubuntuforums.org/showthread.php?t=2008286](http://ubuntuforums.org/showthread.php?t=2008286)

---

### Post by LightningCrash on 2012-06-22
Do you want a failback dns server, or a second query source?

two scenarios:
[LIST=1]
[*]failover:
[INDENT]query server A for host.somedomain.com
query times out
query server B for host.somedomain.com
query answer[/INDENT]

[*]two sources:
[INDENT]query server A for host.somedomain.com
query returns NXDOMAIN
query server B for host.somedomain.com
query answer[/INDENT]
[/LIST]

As far as I know #2 is not possible without a DNS server such as dnsmasq.

---

