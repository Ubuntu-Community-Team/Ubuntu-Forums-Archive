---
title: "Port Forwarding"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by orrymr on 2011-04-13
Hi guys, I'm having some trouble understanding the basics of hosting a web server from home.

So far here's what I (think I) understand:
Since my IP address is dynamic, I've signed up to dynDNS.com and created an account. I've downloaded the client and set it to autorefresh so that when my IP address changes, it will recognize that change.
This seems to work, since whether I type in 192.168.0.1 or my accountName.dynDns.com I get directed to my router. 
Now, the web server (I'm using apache, if that makes any difference, and I've tested it locally - it's fine) is hosted on 192.168.0.4, so now I want accountName.dynDns.com to direct here as opposed to 192.168.0.1. I'm not exactly sure what I'm meant to do here.

What I've tried to do is, in my router, to go to inbound services, under service -> choose HTTP(TCP:80) 
                Action  -> allow always
    Send to lan  Server -> 192.168.0.4

(see attached image).

This didn't work #-o
Any suggestions?

---

### Post by elliotbeken on 2011-04-13
what you need to do is change or disable the port your router uses for remote management

hope this helps

---

### Post by eerror on 2011-04-13
From your post it looks like you entered your local lan IP into dyndns. 
yourname.dyndns.com should resolve to the IP your router obtained from your ISP.  It will be something other than 192.168.x.x and 10.x.x.x.
Set that up properly at dyndns.
Then set up the port forward.

Also, you didn't mention if you got any error messages.

---

### Post by orrymr on 2011-04-15
> **elliotbeken said:**
> what you need to do is change or disable the port your router uses for remote management

hope this helps

Remote management isn't enabled...
If I don't change the inbound rules, I get directed to my router (that is, if I do no port forwarding). However if I do a port forward to 192.168.0.4 then nothing happens

---

### Post by gareththered on 2011-04-15
Is there a firewall running on your router that's stopping http traffic getting through?

---

### Post by orrymr on 2011-04-16
Well, I added a new firewall rule to allow http traffic through...

---

### Post by gareththered on 2011-04-16
Try running a port scanner against your domain name. Google for "nmap online". See if that shows your port open or not.

---

