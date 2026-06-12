---
title: "Firewall Configuration Policy"
date: 2005-12-15
forum: Networking &amp; Wireless
---

### Post by djur on 2005-12-15
I'm a relative beginner when it comes to setting up firewalls.  I want to set up a firewall that generally allows most transmissions to pass except those that are known to be exploitable.  Can anyone give me some guidelines, or rules of thumb for firewall policy?  I'm working with guard dog (because firestarter gives me an sit0 not ready error).  It seems when I enable to firewall my connectivity goes away.  I'm guessing this is because of a deny all  > ask questions later set up to begin with.  I tried opening some things up, like http, etc.  still no connectivity.  Anyone know a good security resource that has a listing of ports that need to stay closed, and protocols that need to be blocked as opposed to protocols that should be allowed in most instances?

---

### Post by GreyFox503 on 2005-12-15
[quote=djur]Can anyone give me some guidelines, or rules of thumb for firewall policy?[/quote] 
Well, my rule of thumb goes against your policy:  To block all traffic by default and use a whitelist to filter.  If you're really concerned about security, then only blacklisting known vulnerabilities is setting yourself up for failure, IMO.

I don't know how to use Guard dog, but I strongly recommend using firewalls as they were intended.  If you don't already have one, a cheap router will provide you with great hardware firewall that will do most of the work you need.

---

### Post by FLeiXiuS on 2005-12-15
I agree with GreyFox, you would want to participate in whats called "DENY ALL".  Blocking every single bit of traffic other then what you really need.

What you need, is what's up for you to decide.

---

