---
title: "etc/network/interfaces"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by Nick Kruger on 2010-08-18
I set up a static address for eth0 which works fine with my dsl router.
 
Now I would like to add a mail server.
 
Do I need to make any changes or additions to etc/network/interfaces ?
 
Thanks,
Nick

---

### Post by Andrew Woolfgang on 2010-08-18
hi, i dont think so, because if you put in your interfaces an static IP, its the same that you put an static ip for you machine in the AP, so, i recommend that you put an static IP in to AP an become your machine in a Server, obviously if you con change the options of the AP or Router =)

---

### Post by Nick Kruger on 2010-08-18
Thank you for your reply Andrew,
 
I went ahead and installed dovecot-postfix, but something is not right. 
 
If I _send_ email via my service provider, should I not have in /etc/hosts something like 
 
127.0.0.3 smtp.myserviceprovider
 
or do I use say
 
192.168.1.3 smtp.myserviceprovider
 
in which case I should set that up in /etc/network/interfaces.
 
Thanks,
Nick

---

### Post by endotherm on 2010-08-18
no you shouldn't need to do anything in hosts, or in interfaces, unless you have installed a new nic that you wish to operate the smtp service on. I assume you have some naming system (DNS) in place already, right?

---

### Post by Nick Kruger on 2010-08-18
Aaah ... that could be it !
 
My web page is working with ddclient updating my IP for [www.mydomain]("http://www.mydomain") 
 
So, ddclient must do the same for mail.mydomain 
 
Was it unnecessary to put the line below in hosts ?
 
192.168.1.2 [www.mydomain]("http://www.mydomain")
 
Thanks,
Nick

---

### Post by endotherm on 2010-08-18
> **Nick Kruger said:**
> Aaah ... that could be it !
 
My web page is working with ddclient updating my IP for [www.mydomain]("http://www.mydomain") 
 
So, ddclient must do the same for mail.mydomain 
 
Was it unnecessary to put the line below in hosts ?
 
192.168.1.2 [www.mydomain]("http://www.mydomain")
 
Thanks,
Nick
without seeing your full config, can't tell for sure, but yes it may be needed so you can access the services from within you network, without going out and coming back in over the wan.

---

### Post by Nick Kruger on 2010-08-19
Thanks Endotherm,
 
/interfaces
 
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
 
/hosts
 
127.0.0.1 pluto.bluejade.za.net  localhost.localdomain  localhost  pluto
 
192.168.1.3 [www.bluejade.za.net]("http://www.bluejade.za.net")
 
 
This seemed to work. Is there a better way ?
DDclient was updating my IP at Zoneedit.
At one stage I tried ppp0 - in order to establish my internet IP for ddclent to use.
 
My goal is to add email server using Imap. Don't know if I should use my isp to send email or not.
 
Am I on the right track ?
 
Nick

---

### Post by endotherm on 2010-08-19
everything looks good on the face. I think it should work, though I'll admit, your getting into realms beyond my experience. 

my best advice on naming configuration and testing, is to ping around. if you can ping by name, then your hosts file requires no further configuration, and whatever issue will be higher in the app stack. just make sure you can ping each host you need internally, and use a tools like nslookup and [http://www.canyouseeme.org/](http://www.canyouseeme.org/) to make sure that the addresses and ports you need externally accessible, can be reached. if you can, then it's time to look at the dovecote config, cause your network is good.

---

### Post by Nick Kruger on 2010-08-19
Thanks, I think you're right.
 
I found plenty of documentation on configureing an email server.
 
I'll do all the testing you advise first - and alot of reading tonight. :D
 
Nick

---

