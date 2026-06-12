---
title: "Block all domains except one"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by GRboss on 2012-05-11
Hello everyone.

We have some PCs in our company and I want to block their access to all websites except one specific. Through the hosts file I have to block one be one site and it is not what I want. I need a rule or something.

Does anyone have any idea?
Thanks

---

### Post by Sergius14 on 2012-05-11
has this site a static and known ip address?

In that case will configure none or local only DNS servers and put the domain-ip at the hosts file...

---

### Post by SeijiSensei on 2012-05-11
I'd do it at the egress router between your network and the Internet.  If you have a Linux box as the router, you can do this with iptables:

```

iptables -A INPUT -p tcp -d ip.addr.ok.host --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j REJECT
iptables -A INPUT -p tcp -d ip.addr.ok.host --dport 443 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j REJECT


```

Replace "ip.addr.ok.host" with the address of the site you want to permit.  The first pair of rules handle HTTP requests; the latter pair handle HTTPS requests.

---

### Post by absoord on 2012-05-11
You may also have a http cache proxy (squid, for example), this way you only configure the allowed/restricted domains for once, you may redirect all 80 and 443 traffic to that proxy cache, and if you wish to add another domain to the allow list you just do it in one place instead of configuring it on EVERY computer.

---

### Post by SeijiSensei on 2012-05-11
> **absoord said:**
> You may also have a http cache proxy (squid, for example), this way you only configure the allowed/restricted domains for once, you may redirect all 80 and 443 traffic to that proxy cache, and if you wish to add another domain to the allow list you just do it in one place instead of configuring it on EVERY computer.

How do you push HTTPS requests through Squid without the browser complaining that it has detected a "man-in-the-middle" attack?  I've looked into this a couple of times.  It always seems the only option is to generate a certificate for the proxy and install it on all the browsers.  Is there something I'm missing?

---

