---
title: "Static IP in Wicd but no Firefox"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by mcman56 on 2011-01-12
I'm new to Ubuntu and using 10.04.  I set up a static IP in Wicd.  Wicd says that it is connected but Firefox does not connect.  Wicd shows the ip and a signal strength.  My settings are in the attached file.  How can I resolve?  
 
Background
This same system will connect with dynamic DCHP but eventually the connection breaks requiring a restart of the netgear WNR2000 router.  This periodic disconnect has been an ongoing issue with my home wireless system.  It affects Linux systems and itouch but not XP.  I have resolved the disconnect in Puppy and Fedora with a static IP.

---

### Post by chili555 on 2011-01-12
Your thumbnail shows no DNS servers. DNS translates names like [www.google.com](www.google.com) to numbers like 72.14.204.147 which the internet can use. It is likely that your router has the correct numbers. You can either grab them from the router's configuration pages or simply appoint the router as your DNS server. Please try filling in your router's IP address 192.168.1.1.

---

### Post by mcman56 on 2011-01-12
It is a little hard to see but I do have that number in DNS Domain.  However, DNS Search, DNS1, DNS2 and DNS3 are empty.  Should it go in one of those spots also...DNS1 maybe?

---

### Post by chili555 on 2011-01-12
> **mcman56 said:**
> It is a little hard to see but I do have that number in DNS Domain.  However, DNS Search, DNS1, DNS2 and DNS3 are empty.  Should it go in one of those spots also...DNS1 maybe?Try it in DNS1.

---

### Post by mcman56 on 2011-01-13
That solved the problem.  Thanks for the help!

---

