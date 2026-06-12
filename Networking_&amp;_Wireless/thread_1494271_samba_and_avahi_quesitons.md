---
title: "samba and avahi quesitons"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by methodtwo on 2010-05-26
Hi
I would like to be able to mount a share served by my mac os X machine(10.6.1). I have read the Ubuntu community doc on Ubuntu samba clients.It didn't say what to do when using dynamic LAN I.Ps.I understand the way to go is to use avahi on the client side(Ubuntu) and Bonjour on the server side(mac os 10.6.1).I can't find anything about how this is done.What do i need to do to set up the client side(Ubuntu) to use avahi  with SAMBA?.Because in the Ubuntu community doc it just referenced /etc/hosts, which is for static I.Ps.So i'm assuming that SAMBA on Ubuntu doesn't use avahi by default.
All i need to know is how to set up the client side of SAMBA on Ubuntu when i'm using dynamic LAN I.Ps.can anyone help?
Thank you for your time
regards methodtwo

---

### Post by methodtwo on 2010-05-26
Hi i've just seen the avahi community doc.The main quesiton i have now is:
To set up file sharing, using SAMBA, between a Mac os X server and  a Ubuntu client would it be enough to follow the SAMBA and Avahi docs on the Ubuntu side. Then follow the SAMBA file sharing with windows giude on the mac side?.Because all the good guides i've found for the mac file sharing talk mainly of serving SAMBA for windows machines.Also is bonjour enabled by default on the mac when you enable file sharing in the system preferences?
Thank you for your time, regards
methodtwo

---

### Post by capscrew on 2010-05-26
> **methodtwo said:**
> Hi
I would like to be able to mount a share served by my mac os X machine(10.6.1). I have read the Ubuntu community doc on Ubuntu samba clients.It didn't say what to do when using dynamic LAN I.Ps.
For a Samba server?  Never use DHCP IP's for a server.  You need to be able to rely on the servers IP address being the same.  Configure it manually at the conf. files.  Don't even use DHCP with reserved IP addresses.  Too many things can go wrong. > 
I understand the way to go is to use avahi on the client side(Ubuntu) and Bonjour on the server side(mac os 10.6.1).
I think you will find that Avahi and Bonjour are the same.  Specifially they provide IP addresses for networks that have not been configured.  See [**_here _**]("http://developer.apple.com/networking/bonjour/faq.html")> .
I can't find anything about how this is done.
For good reasons.  Don't do this.  Take the time so set  up the addressing correctly and control your own network.  Think of what can happen if a Bonjour/Avahi developer changes something and you network stops working.  Yes it can (and has) happened.> 
What do i need to do to set up the client side(Ubuntu) to use avahi  with SAMBA?.Because in the Ubuntu community doc it just referenced /etc/hosts, which is for static I.Ps.So i'm assuming that SAMBA on Ubuntu doesn't use avahi by default.
The /etc/hosts file is for DNS type nameservice.  It has nothing to do with setting up IP addressing in Linux, Apple or Windows.

Samba uses IP addressing to communicate and any number of nameservices for browsing identification.> 
All i need to know is how to set up the client side of SAMBA on Ubuntu when i'm using dynamic LAN I.Ps.can anyone help?
Thank you for your time
regards methodtwo
What do you mean by "client side of Samba"  The Samba suit of protocols includes a client to facilitate requests to a Samba server.  The client package is smbfs.

---

### Post by capscrew on 2010-05-26
> **methodtwo said:**
> Hi i've just seen the avahi community doc.The main quesiton i have now is:
To set up file sharing, using SAMBA, between a Mac os X server and  a Ubuntu client would it be enough to follow the SAMBA and Avahi docs on the Ubuntu side. Then follow the SAMBA file sharing with windows giude on the mac side?.
Set the samba server up on the Mac.  Don't worry about what type of client it will have. There is lot's info info on this subject.  Here's a [**_google search_**]("http://www.google.com/search?q=samba+server+Mac+osx&btnG=Go!").  The Linux client is smbfs.  You install  that with```
sudo apt-get install smbfs
```

> 
Because all the good guides i've found for the mac file sharing talk mainly of serving SAMBA for windows machines.Also is bonjour enabled by default on the mac when you enable file sharing in the system preferences?
This is primarily a Ubuntu (Linux) forum.  You might try a Mac OSX forum for that information.

But once again, I will tell you Bonjour/Avahi is NOT the way to go for successful use of Samba.

---

### Post by methodtwo on 2010-05-27
Thank you for your informative reply.All i meant about /etc/hosts is that it can be used so if you have static I.Ps then it gives the systems a way of referring to other systems by name.This is primarily my problem.I want to use dynamic I.Ps but be able to refer to systems by name.Is this impossible?.I thought bonjour/avahi was the way to do this for SAMBA.In what way was i wrong...i'm not being funny i genuinely would like an opportunity to learn from my mistaken assumptions.
Thank you for your time
regards methodtwo

---

### Post by capscrew on 2010-05-27
> **methodtwo said:**
> Thank you for your informative reply. All i meant about /etc/hosts is that it can be used so if you have static I.Ps then it gives the systems a way of referring to other systems by name.
The essence of any name service (e.g. DNS or WINS or NETBIOS)> 

This is primarily my problem.I want to use dynamic I.Ps but be able to refer to systems by name.  Is this impossible?.  
It is possible, but it becomes more complex.> 
I thought bonjour/avahi was the way to do this for SAMBA.  In what way was i wrong...i'm not being funny i genuinely would like an opportunity to learn from my mistaken assumptions.

Let's step back from the issue of creating a Samba server for a second here.  Just think of the connectivity between the Apple and Linux systems.  

Think of this connectivity as a street.  There are multiple aspects to this. What it is made of and what are the rules upon it's usage.  This can be seen [**_here_**]("http://www.google.com/imgres?imgurl=http://www.novell.com/info/primer/art/prim02.gif&imgrefurl=http://www.novell.com/info/primer/prim05.html&h=649&w=420&sz=113&tbnid=rFT_8z8d-bOUCM:&tbnh=137&tbnw=89&prev=/images%3Fq%3Dosi%2Bnetworking%2Bmodel&usg=__moKqXQ5XPHwBa1hAkgWyBNRJ4Ro=&ei=N6H-S4v8DozANr355Ts&sa=X&oi=image_result&resnum=4&ct=image&ved=0CC4Q9QEwAw"), [**_here_**]("http://www.google.com/imgres?imgurl=http://i.msdn.microsoft.com/Ff571073.101osi(en-us,VS.85).png&imgrefurl=http://msdn.microsoft.com/en-us/library/ff571073(VS.85).aspx&h=391&w=434&sz=15&tbnid=0JhN_dm44KOlfM:&tbnh=114&tbnw=126&prev=/images%3Fq%3Dosi%2Bnetworking%2Bmodel&usg=__fSeWMhfRbvTBeCmsdc3Ul3qHnM8=&ei=N6H-S4v8DozANr355Ts&sa=X&oi=image_result&resnum=9&ct=image&ved=0CDgQ9QEwCA") and [**_here_**]("http://en.wikipedia.org/wiki/OSI_model").

The OSI model breaks down every aspect of networking connectivity.  So you can see that this is not just one big thing that you configure, but more a group of parts that you get to setup as you need it.

Both the Apple and the Linux hosts (and Windows too) can use the same physical hardware, and addressing schemes (Ethernet and TCP/IP addressing).  DHCP and Name services are part of this too.

Samba uses this connectivity (the road) but it is not part of it.  Think of Samba as the car that is on the road.  You could set up the network and not ever use Samba.  

The IP addressing can be statically configured or you can add a DHCP server to handle it dynamically you can provide simple name resolution with static files or you can provide a central location for this in a DNS server.  For very dynamic networks (always changing) you can provide dynamic DNS records.

Bonjour/Avahi tries to implement this for users that don't want or need to understand the underlaying protocols.  This ultimatly will become a dead end for a couple of reasons: this will not help you learn how networking really works and ultimately the whole system will be changing to IPv6 making Bonjour/Avahi as we now know it useless.

As I said earlier: Samba uses this connectivity but it is not a part of it.  My advice is to construct a simple static network to start with.  Static addressing and static name services.  The test will be for you to be able to ping every host by hostname or IP address.

At that point you can add Samba services. Start simple and do one thing at a time.  This will help you trouble shoot the system in the future. 

Networking is complex and frustrating at times.  I can not stress enough how important it is for you to understand the basics.  My advice is for you to read all you can about TCP/IP and Samba.

---

