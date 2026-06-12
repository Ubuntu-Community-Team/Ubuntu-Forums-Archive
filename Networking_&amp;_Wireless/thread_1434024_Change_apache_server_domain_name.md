---
title: "Change apache server domain name"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by blakep2 on 2010-03-19
I have seen tutorials on how to change the domain name in apache but i dont understand them.  I have apache set up but you have to type in the ip address i would like to change that to a personal one.  running ubuntu desktop 9.04

---

### Post by zipperback on 2010-03-19
Here is the link to the information on the apache server website.

[http://httpd.apache.org/docs/2.1/vhosts/name-based.html](http://httpd.apache.org/docs/2.1/vhosts/name-based.html)

- zipperback
:popcorn:

---

### Post by zipperback on 2010-03-19
Be aware however that you need to actually register the domain name with a domain registrar, and have DNS setup to resolve your ip address.

If you don't have a dedicated IP address then you can setup your system to resolve a domain name provided by a dynamic dns service such as [http://www.dyndns.com/](http://www.dyndns.com/) any one of the many others as well.

- zipperback
:popcorn:

---

### Post by blakep2 on 2010-03-19
I have read this and i am not quite understanding it.  Also if i do change the domain do I have to own the domain.  I guess what i am asking is if the website is viewable outside my network.

---

### Post by blakep2 on 2010-03-19
What i really want to know is how to create another /etc/apache2/ file for a site other than the one with the ip address and where to put the html files for it.

---

### Post by jrssystemsnet on 2010-03-19
In its default configuration, the same site you see when you browse to [http://your.ip.address.numbers](http://your.ip.address.numbers) is what you would see no matter how you browsed in to that Apache.

So you probably *don't* need to mess with Apache; most likely what you really need to do is just get a domain name and point it to your IP address.  You can either buy a domain from someplace like GoDaddy, or get "dynamic domain service" from someplace like noip.com.

If you don't have a static IP address from your ISP, you will probably need to go the dynamic domain service route, whether or not you buy your own domain also.

---

### Post by blakep2 on 2010-03-19
how would i create like a intranet. a website that can only be viewed in my network

---

### Post by Iowan on 2010-03-19
[Here]("https://help.ubuntu.com/9.10/serverguide/C/index.html") is a help page that might prove useful (unless you've already seen it).

---

### Post by blakep2 on 2010-03-19
this is the main one i have been looking at.  The only part i need is the changing of the domain name

---

### Post by Iowan on 2010-03-19
You have two threads going - I *thought* they were different topics, but they're both asking questions about the other. :confused: The domain name (for local network) may be a DNS issue. You might be able to edit */etc/hosts* with the appropriate name/address pair.

---

### Post by blakep2 on 2010-03-19
yes i know, i edited the /etc/hosts file but it only works for the computer it is serving it on, i want it displayed on all computers on my network how do i do that

---

### Post by Iowan on 2010-03-19
My network uses DNSMasq for DHCP/DNS. Even DHCP-configured hosts can be reached by hostname. The quick/dirty method (well, dirty anyway...) would be to edit the **hosts** file of each client machine (even Windows).

---

### Post by blakep2 on 2010-03-19
so there is no way to access the site from other computers on the network without editing something on the client computer

---

### Post by jrssystemsnet on 2010-03-19
> **blakep2 said:**
> how would i create like a intranet. a website that can only be viewed in my networkSet up a BIND server inside your network, configure a zone on it for your intranet domain, then make sure your client computers use your BIND server for DNS resolution.

---

### Post by blakep2 on 2010-03-19
What i am trying to do is set this up so guests can access this site when they are visiting and they are on my network.  So is there any way to do this without doing anything on the client's computer. Is that what you are saying I can do with BIND.

---

### Post by jrssystemsnet on 2010-03-20
> **blakep2 said:**
> What i am trying to do is set this up so guests can access this site when they are visiting and they are on my network.  So is there any way to do this without doing anything on the client's computer. Is that what you are saying I can do with BIND.Yep.

---

### Post by blakep2 on 2010-03-20
How would I set up a bind server; I just did this command, sudo apt-get install bind9.  how would I configure the bind server and how do i make the clients computer use the bind server for their dns resolution.
thanks for your help

---

