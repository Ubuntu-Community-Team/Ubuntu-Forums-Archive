---
title: "Apache, Virtual hosts and DNS, oh my!"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by Jh60082 on 2009-06-18
So I am trying to host a webserver in my network and I got it running. but I can not access the server by name , i.e. "http://server01/" from another computer, i can using the IP address, But I want to be able to use the server name. How do I go about doing this? Will this work the same for virtual hosts?
I use webmin to manage this kind of stuff. Thanks.

---

### Post by alphacrucis2 on 2009-06-18
> **Jh60082 said:**
> So I am trying to host a webserver in my network and I got it running. but I can not access the server by name , i.e. "http://server01/" from another computer, i can using the IP address, But I want to be able to use the server name. How do I go about doing this? Will this work the same for virtual hosts?
I use webmin to manage this kind of stuff. Thanks.

You can edit the file /etc/hosts and add the name/ip address combinations in there. This is what they used to do before DNS existed.(Warning - don't mess with the existing localhost entries in that file). You could install and configure a dns server. bind9 is in the repos but will take some work to set it up.

If you go the /etc/hosts method then add lines as follows:

<ip address> <domain name> alias

e.g

```
192.168.1.7 www.fred.local fred
```

You have to do this on each machine you want to resolve the name on. Whereas the DNS only needs setting up once.

---

### Post by Iowan on 2009-06-18
If you opt for DNS server, DNSMasq is another option for local DNS (and DHCP) server. It's still on my To-Do list, but reportedly much easier to set up than Bind.

---

### Post by Jh60082 on 2009-06-18
Thank you for the advice.
See, the thing is, I had a windows computer running xampp and I could access its server name [Http://server02](Http://server02) (for example purposes) just fine on other computers, I can't seem to do it with ubuntu. I am sure it is possible but I will need some help. So I am not really sure where to begin (And i really do not want to go around editing everyone's hosts file)
Thanks!

---

### Post by Jh60082 on 2009-06-18
I solved like 75% of my own problem! I installed samba and now my windows computers can connect just fine :)
Now, I want to be able to create virtual hosts like [http://clienta](http://clienta) and [http://clientb](http://clientb)   but im not sure how to do that. Also, how do I open a port in apache and ubuntu?

---

### Post by Iowan on 2009-06-18
[Here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is a tutorial for name-based virtual hosts.

---

