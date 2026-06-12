---
title: "how to set dns servers..."
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by hockey97 on 2009-01-16
Hi, how in ubuntu can I set a dns server for my connections.

I want to use opendns servers cause I hear it's faster then ISP's dns servers.


I also have a question. Is it possible to host my own dns server?? I mean would I be able to create domain names and host them myself??

or do I need to have a backbone internet connection.

In other words how could I host my own domain names for free using my own dns server .... bind9.

---

### Post by wmdiem on 2009-01-16
dns servers are in /etc/resolv.conf

just edit that with the ip of the new dns server

however, if you are using dhcp, it might overwrite your manual configuration each time. 
I don't know whether there is an elegant solution if that is the case.

---

### Post by wmdiem on 2009-01-16
> **hockey97 said:**
> 

I also have a question. Is it possible to host my own dns server?? I mean would I be able to create domain names and host them myself??

to sell domain names you need to become a registrar through ICANN (or at least work through one, i.e, buy and sell through a registrar)
> 
or do I need to have a backbone internet connection.

No, just a static external ip address.
> 
In other words how could I host my own domain names for free using my own dns server .... bind9.
A domain name costs like $6. I can't imagine it would be worth the headache. Or the fees.

---

### Post by hockey97 on 2009-01-16
ok... I sent a e-mail to ICan group.

I dont' plan to sell at this point. I just want to host my own domain names.

I am trying to cut costs.

are the fees expensive? well I will find out. Thanks for the help.

---

### Post by Iowan on 2009-01-16
> **wmdiem said:**
> ... if you are using dhcp, it might overwrite your manual configuration each time. 
I don't know whether there is an elegant solution if that is the case.There is a "prepend" option in dhclient that lets you put your preferred servers at the top of whatever list the DHCP server provides.

---

