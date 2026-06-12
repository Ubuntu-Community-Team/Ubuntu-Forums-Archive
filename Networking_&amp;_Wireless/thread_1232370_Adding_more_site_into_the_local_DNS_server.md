---
title: "Adding more site into the local DNS server"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by OOzypal on 2009-08-05
I followed the following tutorial to install DNS on Ubuntu. Everything went ok. Now, I want to add more sites to the DNS so when I write for example [www.xyz.lcl](www.xyz.lcl) it gets resolved to the local server.

[http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/]("http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/")

---

### Post by Warren Watts on 2009-08-05
add your local address to the hosts file:

/etc/hosts

# Add this entry to the Hosts file:

put.your.server.ip (here)     [www.xyz.lcl](www.xyz.lcl)

---

### Post by OOzypal on 2009-08-06
Will this resolve for all computers connected to the network? Let's say the my Ubuntu Server w/ DNS installed is 192.168.1.3 and there is two computers as follows:


Ubuntu Desktop 192.168.1.8
Win XP 192.168.1.9


Router DNS is 192.168.1.3

If in WinXP I type [www.xyz.lcl](www.xyz.lcl) will it resolve ok?

---

### Post by Warren Watts on 2009-08-06
> **OOzypal said:**
> Will this resolve for all computers connected to the network? 

If in WinXP I type [www.xyz.lcl](www.xyz.lcl) will it resolve ok?

No, you would have to add the server to the hosts file in the windows machine as well.  The windows hosts file is at: **c:\winnt\system32\drivers\etc\hosts**

Make sure that if you edit and save the hosts file in windows using notepad, you put the filename in quotes *e.g. "hosts"*  when you save it, or notepad will automatically tack [COLOR="DarkOrange"].txt[/COLOR] onto the end of the filename, and the file will get saved as hosts.txt  -  which windows won't recognize as the hosts file.

---

