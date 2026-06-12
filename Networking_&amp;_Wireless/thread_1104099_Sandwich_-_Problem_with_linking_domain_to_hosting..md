---
title: "Sandwich - Problem with linking domain to hosting.."
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by Spikerok on 2009-03-23
cant view my website on different computer.

Domain name is set on next nameservers:
    Name servers:
        ns1.web-a.org.uk          92.16.105.131
        ns2.web-a.org.uk          92.16.105.131

my external ip - 92.16.105.131

to check if my website is online i was using [http://www.hidemyass.com/](http://www.hidemyass.com/), and i was asked to download index.php file

My Connection information from modem:
IP Address:	92.16.105.131
Primary DNS:	92.31.241.20
Secondary DNS:	92.31.241.21

server is OFFLINE, RUNNING

---

### Post by Spikerok on 2009-03-23
......

---

### Post by terazen on 2009-03-23
I can't resolve your site in dns from here.  Who did you register your domain with?  Is it only supposed to work from computers locally at your site?

---

### Post by Spikerok on 2009-03-23
should be working on the internet, i can ping my external ip but problem is that domain name is not connected properly. I have used dyndns and my ip address as ns1 and ns2 now. for a start i'm trying to make one hosting which others can see on internet.

domain is registered with [http://www.123-reg.co.uk/](http://www.123-reg.co.uk/)

---

### Post by terazen on 2009-03-25
Was your site web-a.org.uk?  I did a lookup on it starting from 123-reg.co.uk which pointed to ns.hosteurope.com.


> web-a.org.uk
Server:  ns.hosteurope.com
Address:  212.67.202.2

web-a.org.uk
        primary name server = ns.hosteurope.com
        responsible mail addr = hostmaster.web-a.org.uk
        serial  = 2009032405
        refresh = 86400 (1 day)
        retry   = 3600 (1 hour)
        expire  = 1209600 (14 days)
        default TTL = 86400 (1 day)
web-a.org.uk    nameserver = ns.hosteurope.com
web-a.org.uk    nameserver = ns2.hosteurope.com
web-a.org.uk    MX preference = 10, mail exchanger = mx0.123-reg.co.uk
web-a.org.uk    MX preference = 20, mail exchanger = mx1.123-reg.co.uk
web-a.org.uk    internet address = 92.21.146.64

That ip address isn't what you gave earlier.  Maybe you have an idea where that came from?

---

### Post by BkkBonanza on 2009-03-25
Umm. If it asks you download your index.php then that means you are reaching your web server but it is trying to send the file rather then use php to run it. You need to add the following line to your httpd.conf to tell apache to execute php files not send them.

AddType application/x-httpd-php .php

(just checked this - it's likely better to use AddHandler not AddType)

---

