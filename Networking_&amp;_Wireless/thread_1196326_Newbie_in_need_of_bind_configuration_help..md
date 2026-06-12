---
title: "Newbie in need of bind configuration help."
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by borngunners on 2009-06-24
I badly need help setting up my ubuntu server and also understanding how bind works alltogether.
I am happy to be part of the community. To start with, I have some bind9 issue. I am configuring a mail server (Ubuntu box) that is giving me trouble setting up the bind9 configuration. This is the scenario:
 
My ISP has an ip 192.168.8.2 (hi.com)
I have a windows 2003 server domain (no.hi.com) machine name is "lab" and ip 192.168.4.206
 
I have a firewall that my ubuntu server is sitting behind.
my ubuntu server name is "mail" with ip 172.168.150.17 (private ip)
mail.no.hi.com
 
 
I am trying to setup a dns zone and having trouble with it. I am a newbie and I will like your help.
 
Note* I have already added the mail.no.hi.com MX record to my windows domain "no.hi.com". I understand that I have to setup the bind on ubuntu for my zimbra email server to work properly.
 
Your help is greatly needed.
 
Thanks

---

### Post by alphacrucis2 on 2009-06-24
> **borngunners said:**
> I badly need help setting up my ubuntu server and also understanding how bind works alltogether.
I am happy to be part of the community. To start with, I have some bind9 issue. I am configuring a mail server (Ubuntu box) that is giving me trouble setting up the bind9 configuration. This is the scenario:
 
My ISP has an ip 192.168.8.2 (hi.com)
I have a windows 2003 server domain (no.hi.com) machine name is "lab" and ip 192.168.4.206
 
I have a firewall that my ubuntu server is sitting behind.
my ubuntu server name is "mail" with ip 172.168.150.17 (private ip)
mail.no.hi.com
 
 
I am trying to setup a dns zone and having trouble with it. I am a newbie and I will like your help.
 
Note* I have already added the mail.no.hi.com MX record to my windows domain "no.hi.com". I understand that I have to setup the bind on ubuntu for my zimbra email server to work properly.
 
Your help is greatly needed.
 
Thanks

Probably easier just to set up an entry in the hosts file rather than go to the trouble of setting up bind just to serve one host. Different story if bind is being set up as a DNS server for multiple hosts. I also notice you have your ubuntu server and windows machines on different subnets and you also say your ISP is using a private RFC address block which seems a bit odd. The info you have given doesn't really add up.

In any case if you do go ahead with setting up bind, then you would be best to check out one of more of the various bind howto's on the net. e.g:

[URL="http://www.langfeldt.net/DNS-HOWTO/BIND-9/"]http://www.langfeldt.net/DNS-HOWTO/BIND-9/
[/URL]

---

### Post by MaindotC on 2009-06-24
Sorry to be harsh bro but it's blatantly obvious that you aren't reading the documentation.  I know it's long, I know some of the wording can be cryptic, but you aren't going to understand it without a fundamental understanding of how DNS works (which you can read at the 900-1000 level RFC's per the DNS wiki) and you have to read the BIND documentation (which is also really long) but EVERYTHING you need to know is in there.  Take some time, get a cup of coffee, and start reading.

---

### Post by borngunners on 2009-06-25
strAlan. As you've advice, I started reading it since a week ago, but the thing is I am currently under pressure to get this email server setup and I have no idea about Ubuntu network configuration. I choose ubuntu because we needed a free OS and email app to deploy, and ubuntu with zimbra has seem to be what many people are recommending. My issue now is not with installing zimbra, but configuring the network before installing zimbra mail server. Zimbra recommended setting up bind9 before installing zimbra.

---

