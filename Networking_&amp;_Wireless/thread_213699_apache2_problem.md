---
title: "apache2 problem"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by deil on 2006-07-11
Hi all,

I just installed ubuntu today and I'm really pleased with it ( I used debian before that ). I have a strange problem. I installed apache2 via apt-get. Now when I type [http://localhost/](http://localhost/) everything is OK I see the server. But when I aks some friends to type http://<IP>/ they receive connection timeout. As far as I red there is no firewall turned on by default. I use ADSL router but the problem is on my computer since apache workeds OK with the debian installation. 

Can you help?

---

### Post by halitech on 2006-07-13
by connecting to [http://localhost](http://localhost), you are bypassing the router completely and just connecting to the computer. Are your friends trying to connect to a 192.168 IP or your WAN IP address? also, if they are trying the WAN IP, is it the same IP as what your system had under Debian?

---

### Post by tturrisi on 2006-07-14
Most all broadband isps filter port 80, the default wwww port.  They do this to prevent residential customers from running www servers and to prevent code red virus propogation.  Set the default www port in apache to 8080 (port apache listens on) or 8090, use port forwarding in router to forward 8080 requests to the local ip of comp w/ apache & have friends access like so:
[http://your-real-ip_address:8080/](http://your-real-ip_address:8080/)

---

### Post by halitech on 2006-07-18
I don't think the ISP is the problem, could be wrong and have been before, but the connection was working previously under debian which should lead us to say that port 80 isn't blocked by the ISP. 

Personally, it sounds to me like his router has assigned a different IP to the computer under Ubuntu then what it had in Debian (or he had a static in Debian and set it differently in Ubuntu)

---

