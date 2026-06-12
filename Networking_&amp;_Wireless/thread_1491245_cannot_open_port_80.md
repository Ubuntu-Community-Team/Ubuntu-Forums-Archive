---
title: "cannot open port 80"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by evaristegalois on 2010-05-23
I just installed apache. I didn't change the configuration files at all except add

> # added servername to avoid the could not determine fqdn error
ServerName myname.homelinux.org

to apache2.conf. Apache is working locally (I get the `it's working' screen at [http://192.168.0.150](http://192.168.0.150)).

However, I cannot access my computer from an external computer by going to [http://myname.homelinux.org](http://myname.homelinux.org), which is equivalent to [http://96.49.75.14](http://96.49.75.14) -- [IP address changed slightly for privacy]

[Here]("http://www.streetgreek.com/anderson/di-624.png") is a screenshot to my router settings.

I disabled the filter for port 80 on the router.

There shouldn't be a firewall, unless it's automatically installed with ubuntu 10.4. (sudo ufw status says `inactive'.)

I checked my ports from [http://ping.eu/port-chk/](http://ping.eu/port-chk/) and indeed port 22 is open (ssh-ing into my computer externally is not a problem), whereas port 80 is closed.

What step in opening up port 80 am I missing? (I also made sure my ISP isn't blocking port 80.)

---

### Post by Iowan on 2010-05-23
> **evaristegalois said:**
> I disabled the filter for port 80 on the router....
What step in opening up port 80 am I missing? (I also made sure my ISP isn't blocking port 80.)
Have you forwarded port 80 from the router to your server? Do you get a static address from your ISP?

---

### Post by mituw16 on 2010-05-23
just to let you know, they way those things work, services like dynamic dns and such, arent actually a FQDN that you own. they are actually a host that redirects all request to that host to your pc. therefore, you cant actually access your pc using your dynamicdns or wan ip if you are connected to the same LAN as your server. 

so basically, go somewhere else, and then try to access your server using your wan ip or you dyndns...

---

### Post by evaristegalois on 2010-05-23
Yes, port 80 is forwarded from router to server (see my screenshot). I already tried to access port 80 from somewhere else (this is also what ping.eu does) and it doesn't work.

---

### Post by evaristegalois on 2010-05-23
I just found out that there is a tiny button I needed to enable on the router, which I failed to do. Problem solved. Many thanks!

---

### Post by duceduc on 2010-07-11
> **evaristegalois said:**
> I just found out that there is a tiny button I needed to enable on the router, which I failed to do. Problem solved. Many thanks!

:biggrin: That is so funny. I got the same problem until I read that line above. I didn't realized on my Linksys router that there is a difference between a **save** and a **apply settings** button whenever you modify something in the router. 

Haha. I fixed my connection to by pressing that tiny button.

---

