---
title: "localhost alias works in server but not in client - How to configure?"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by nabil_kadimi on 2009-06-20
Hello everyone, 

I'm not a newbie nor a guru in Linux, I'm trying to build a home web server for testing purposes (I build Cross-platform Web applications), everything went smoothly; I installed and/or configured Apache, MySQL, PHP, FTP, SSH...

The server and the client(s) are connected to each other through a router which is the Internet Gateway (192.168.1.1) for all other PCs in my office, this router is not suited for experiments and its configuration should not be altered.

I can access the web server like this:

[LIST]
[*]From the server itself with the URI **[http://192.168.1.20](http://192.168.1.20)** or **[http://localhost](http://localhost).[COLOR=Red]com[/COLOR]**
[*][COLOR=Red][COLOR=Black]From the client using the URI **[http://192.168.1.20](http://192.168.1.20)**[/COLOR][/COLOR]
[/LIST]
I want to be able to access the server from the client using the URL **[http://localhost.com](http://localhost.com)**

Please show me how I can do that, I'm sure it's something related to **DNS** and the files **/etc/ne../interfaces** and **/etc/resolv.conf** 

Thank you in advance for your help.

Nabil KADIMI

---

### Post by nabil_kadimi on 2009-06-22
SOLVED

I figured I had to setup a DNS server, I used dnsmasq which is sueted for small DNS servers

Further reading: [http://www.linux.com/archive/articles/149040](http://www.linux.com/archive/articles/149040)

---

### Post by Iowan on 2009-06-22
I'll be curious to see if your client accesses the server by **localhost.com** - and if it can still find "itself" at **localhost **(127.0.0.1)

---

