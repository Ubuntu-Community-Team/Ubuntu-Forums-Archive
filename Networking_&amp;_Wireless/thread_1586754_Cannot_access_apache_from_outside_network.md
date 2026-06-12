---
title: "Cannot access apache from outside network"
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by larrxu on 2010-10-02
Hi,

I have recently installed newest version of Ubuntu Desktop 64bit. I then installed apache, mysql and php using apt-get. I then installed dynamic dns service on my web server (say [www.myserver.com](www.myserver.com)). Then I set port 80 forwarding to my web server. 

After installation I can use web browser to access my web server correctly from all the home computers (using [www.myserver.com](www.myserver.com) in web browser). However, when I go to school and try to access from there (or anywhere that is outside my home network) the connection to [www.myserver.com](www.myserver.com) in web browser just times out. I also have a java client listening on 13340 port in my web server and it can be accessed from outside my home network (with port forwarding).

My network configuration is:

Cable Modem -> Router -> 3 Computers (one of which is web server)
Router has port forwarding 80 and 13340 to web server. 

I searched web and tried all the methods (editing apache conf etc.) still no luck. Anyone has any idea to fix this? Appreciate it!

---

### Post by larrxu on 2010-10-02
Please, anyone help me?

---

### Post by spiky001 on 2010-10-02
not much of a fix just a thought is the firewall blocking? i see you have port forwarding taken care of

---

### Post by larrxu on 2010-10-02
> **spiky001 said:**
> not much of a fix just a thought is the firewall blocking? i see you have port forwarding taken care of

Thank you for reply!

But if it's firewall why I can access it from my other home computers?

---

### Post by spiky001 on 2010-10-02
I,m no expert I have gufw setup blocks all external acsses to ssh port I would have to allow ssh port have acsess from internet I have lan only

---

