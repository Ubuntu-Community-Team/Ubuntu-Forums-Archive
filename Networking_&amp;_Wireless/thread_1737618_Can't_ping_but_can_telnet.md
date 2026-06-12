---
title: "Can't ping but can telnet"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by oj0kksn5 on 2011-04-23
Hello

I am trying to solve an email issue i am having as i can't send emails or receive them from my ubuntu server 8.04 running webmin latest version, however i can't telnet any external website on port 25 nor can i ping them however i can telnet on port 80 to google and im getting a bit stumped tried resetting alot of things and restarting the router and server but still no joy.

I can download files from the internet so the internet connection is there but can't ping IPs or DNS names :(

Help

---

### Post by oj0kksn5 on 2011-04-25
any ideas?

---

### Post by SeijiSensei on 2011-04-25
Most likely your ISP is blocking remote port 25 and maybe pings.  Ask them.

---

### Post by collisionystm on 2011-04-25
> **sephedo said:**
> Hello

I am trying to solve an email issue i am having as i can't send emails or receive them from my ubuntu server 8.04 running webmin latest version, however i can't telnet any external website on port 25 nor can i ping them however i can telnet on port 80 to google and im getting a bit stumped tried resetting alot of things and restarting the router and server but still no joy.

I can download files from the internet so the internet connection is there but can't ping IPs or DNS names :(

Help

Can you ping from another computer on your network? As for the DNS problem, you probably do not have your DNS forwarders configured correctly. Also, check to make sure under /etc/resolv.conf on your server that it is using 127.0.0.1 for DNS. 

Follow this HOW-TO

[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

I haven't noticed anything good about webmin.

Upgrade your box to this....

It is Free, Runs on 10.04 and is the BEST thing you will ever use. 

[http://www.zentyal.com/en/](http://www.zentyal.com/en/)

I highly recommend it.

---

### Post by oj0kksn5 on 2011-04-25
> **SeijiSensei said:**
> Most likely your ISP is blocking remote port 25 and maybe pings.  Ask them.

The port is open

---

