---
title: "Laptop in multiple networks"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by storm76 on 2009-05-08
Home network using Linux/Windows computers wired/wireless and would like to use share files and printers: Work Domain Server: Open random networks. Need help to configure all on a single laptop

---

### Post by superprash2003 on 2009-05-09
you could use samba for this [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by storm76 on 2009-05-09
Can you give me an example of how to configure? I've had a Hard time following tutorials. I've managed to edit smb.conf, nsswitch.conf and a couple of others to have connected to each one at a time. My latest config, I was able to connect to Win2k Domain, but lost all other access to web services.

---

### Post by superprash2003 on 2009-05-09
post your smb.conf file , if you have already configured that , you should have it working by now..

---

### Post by storm76 on 2009-05-10
> **superprash2003 said:**
> post your smb.conf file , if you have already configured that , you should have it working by now..

Trying to figure out why I had no internet access but could still connect to Domain, I started to revert *smb.conf* back to original. Unable to succeed in trying to connect to domain and internet at same time I deleted files and started fresh again. 

I think the problem was on this line of [I]nsswitch.conf[I] 
original
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
modified
hosts:          files mdns4_minimal [NOTFOUND=return] wins mdns4
maybe it should have been
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

I will have to try tomorrow at work.

---

### Post by storm76 on 2009-05-15
Sorry for the delay, I've been sick :cry:. Any case I've played with the configuration and the only thing that matters is the nsswitch.conf file.
when I change
host:  files mdns4_minimal [NOTFOUND=return] dns mdns4
to 
host:  files mdns4_miniaml [NOTFOUND=return] wins mdns4
this allows me to access server shares but unable to browse internet.

all other conf files are default configuration.

---

