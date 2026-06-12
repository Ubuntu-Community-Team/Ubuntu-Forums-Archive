---
title: "Restricting HTTPS Websites with exceptional sites"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by psrdotcom on 2011-09-13
Hi all,

I am trying to allow only specific websites.

With the combo of Dansguardian, TinyProxy, Firehol; I was able to control the http websites.

But as everyone know, Danguardian won't restrict the HTTPS websites.

I want to restrict all HTTPS with some exceptional HTTPS websites. 

Can anybody please help me to resolve this issue?

Thanks in advance.

---

### Post by psrdotcom on 2011-09-16
I tried IPkungfu to block the ports and I had a success with it except HTTPS blocking.

---

### Post by SeijiSensei on 2011-09-16
> **psrdotcom said:**
> I want to restrict all HTTPS with some exceptional HTTPS websites.

Use iptables rules like these:

```

iptables -A INPUT -p tcp -d ip.addr.ok.site1 --dport 443 -j ACCEPT
iptables -A INPUT -p tcp -d ip.addr.ok.site2 --dport 443 -j ACCEPT
[...]
iptables -A INPUT -p tcp -d ip.addr.ok.siteN --dport 443 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j DENY

```

Replace "ip.addr.ok.siteX" with the IP addresses of the sites you wish to permit.

---

### Post by psrdotcom on 2011-09-17
Thanks for the help. I will try and let you know the status.

---

### Post by psrdotcom on 2011-09-23
I can't guarantee that, one website will use same server for long time. The IP addresses may get changed. Please suggest me in this.

I want to restrict all Secure(HTTPS) websites except few Secure(HTTPS) sites.

Please help me.

---

### Post by psrdotcom on 2012-06-01
Hi,

Issue was solved. I re-configured the Tinyproxy, Dansguardian and Firehol with proper settings.

---

