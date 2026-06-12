---
title: "No internet after crash"
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by ziekfiguur on 2013-04-30
Hallo everyone.

This morning my laptop suffered a gpu crash while I was logged in to a vpn. It didn't respond to anything anymore so I turned off the laptop by holding the power button. Now, since I restarted, I have not been able to reach the internet. the weird thing is, I can reach my router and other computer on the home network. Does anyone know how I can fix this?

Thanks.

PS, this is my work laptop so there is some urgency in fixing this.

---

### Post by steeldriver on 2013-04-30
what do you mean by "unable to reach the internet"? can you ping a remote host by IP from a terminal? have you checked whether name resolution is working (using dig or nslookup for example)?

---

### Post by ziekfiguur on 2013-04-30
I am able to ping or ssh to other devices on my home network. I thought I was unable to ping outside that, but apparently I used a wrong IP adress as I can get a response from 173.194.66.103 ([www.google.com](www.google.com)) so that would suggest a dns issue I think?

Edit: Thanks. While looking at the manpage of dig i saw it searches the servers listed in /etc/resolv.conf when I looked there I saw it was still pointing to the vpn's dns servers which I couldn't access whithout being logged in. I reset it to the values on my other computer and everything is fine now :)

---

### Post by steeldriver on 2013-04-30
Hmm.. I don't really have any experience with VPNs but I *think* the switch back to your 'local' DNS should be handled automatically (by resolvconf / dnsmasq) - so perhaps something's misconfigured there? 

Anyhow glad you got it working

---

