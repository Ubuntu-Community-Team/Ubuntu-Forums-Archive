---
title: "help with open ports?"
date: 2013-04-15
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2013-04-15
While trying to determine the reason for slow internet speeds, I ran a port scan on my network. 

First, I keep seeing in my routers log that port scans keep coming from the Bellsouth DNS servers. Now I am running a web server on this IP address, but is it normal for a DNS sever to run a port scan?

The real reason for this post, though, is that there are three ports "filtered" that I don't recognize.... hmmmm. Well, I actually closed that terminal accidentally while I was writing this, so I opened a new terminal and re-ran nmap. Those ports weren't listed any more, but each time I run nmap different ports show up as "filtered", sometimes none show up "filtered". And actually, there are a couple of ports that I have set in "pinholes" that aren't showing up on the port scan.

Is this normal? 

Thanks for the help...

---

### Post by permittivity22 on 2013-04-16
yep, completely normal to have filtered ports when doing an nmap.  
welcome to the world of deceit, deception, and networking.  :)

---

