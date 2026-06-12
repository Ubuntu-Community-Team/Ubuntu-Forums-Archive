---
title: "Creating my server with LAMP question..."
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by Eremis on 2010-10-04
Hi everyone,

I was experimenting with LAMP and so I created a server on my laptop...
Now when someone types in my ip address they get my simple webpage thats in /var/www/index.html

My question is: How would I run an applications on that server? would I just run it on my computer while the server is running? 
For example I have a simple Daytime server application I made in java, how would I run it on my server? 

The second quesiton...
How would I change it so instead of people typing in my ip, they can just type my name like ([www.whatever.com](www.whatever.com) instead of ###.##.##.##)

Sorry, but I am kind on  a newbie when it comes to networking... Just started learning it in CS... 


Thanks for you help,

- Eremis

---

### Post by Iowan on 2010-10-05
> **Eremis said:**
> The second quesiton...
How would I change it so instead of people typing in my ip, they can just type my name like ([www.whatever.com](www.whatever.com) instead of ###.##.##.###
The quick/dirty method would be to edit the **hosts** file on client machines (location depends on OS - in Ubuntu it's */etc/hosts*) Otherwise, a DNS server will need to link the two. Is your IP fixed, or assigned by DHCP? My network uses DNSMasq to tie the two together. That's IF I have the client send it's hostname (by editing the "send hostname" line in */etc/dhcp3/dhclient.conf*)

---

### Post by kreggz on 2010-10-06
you can add java applets to html

[http://www.ehow.com/how_4460742_add-java-applets-using-html.html](http://www.ehow.com/how_4460742_add-java-applets-using-html.html)

once you have apache installed browser to the file as shown in /var/www/ e.g

/var/www/java.html

[http://myserver/java.html](http://myserver/java.html)

---

### Post by Eremis on 2010-10-06
Is there a way to stop apache server from autostarting?

---

### Post by Iowan on 2010-10-06
I'm not as familiar with how the "new" **service** works... under the old system, you could rename a script in the appropriate /etc/rcX.d  directory to keep it from starting.

---

### Post by Eremis on 2010-10-09
ok, thx I found a tool that lets me stop services from autostarting, the tool is called: bum.

you can get this tool from simply doing: 

sudo apt-get install bum

---

