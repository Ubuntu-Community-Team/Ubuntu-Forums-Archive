---
title: "/etc/postfix/main.cf: No such file or directory"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by ivanp on 2010-06-28
Hi,

Sometimes my desktop (Ubuntu 10) doesn't recognize the eth0 interface. An ifconfig will answer only with the lo interface Direc. inet:127.0.0.1  Másc:255.0.0.0, and, when this happens I can't access to the network.

At this point the /etc/network/interfaces file looks like
auto lo
iface lo inet loopback

So I have to switch to a fixed IP address in the /etc/network/interfaces file
auto eth0
iface eth0 inet static
	address 172.16.10.84
	netmask 255.255.240.0
	gateway 172.16.1.2

Then I restar the networking service and get the following message, even when network starts working again and an ifconfig answers with both interfaces lo and eth0.

 * Reconfiguring network interfaces...                                                             
ssh stop/waiting
ssh start/running, process 1570
postconf: fatal: open /etc/postfix/main.cf: No such file or directory

Why does this fatal error apears? Thank in advance.

---

### Post by selimhanov on 2010-10-12
I had a similar problem, fixed with ```
sudo dpkg-reconfigure postfix
```

---

### Post by blackmonjd on 2011-12-06
I tried 
```

sudo dpkg-reconfigure postfix
sudo /etc/init.d/postfix reload
sudo /etc/init.d/networking restart

```

and still got the same error. I figured it's asking for this file so I created it, but I'm not sure what effect this will have. If it is only for an SMTP server, will this cause me any issues?

---

### Post by octobuntu on 2012-04-23
I had the same issue. My fix was super simple:

apt-get remove postfix

I am not trying to send mail.

---

### Post by mdacova on 2012-07-09
> **selimhanov said:**
> I had a similar problem, fixed with ```
sudo dpkg-reconfigure postfix
```
fix my issues

---

