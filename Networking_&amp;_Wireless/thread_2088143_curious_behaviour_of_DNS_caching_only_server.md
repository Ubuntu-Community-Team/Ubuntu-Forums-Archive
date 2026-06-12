---
title: "curious behaviour of DNS caching only server"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by yizrahomme on 2012-11-25
Hi,
I set up my laptop to be its own caching DNS server.  No reason, just for fun.

Anyway, /etc/resolv.conf points to 127.0.0.1, and the network settings for my wireless connection point to the same place.  All seems to be working, but there's something curious.  As of this moment, I've got a few tabs open in Google's Chromium browser, and one of those is FaceBook.  So why, when I try `dig @127.0.0.1 facebook.com` does the first request take a little over 1000 ms?  

The only thing I can think of is that Chrome is using a different method to resolve the IP?

---

### Post by efflandt on 2012-11-27
What exactly did you set up?  I didn't set up any DNS in 12.04 and it seems to have its own caching nameserver by default.  After doing **host facebook.com** and **host [www.facebook.com]("http://www.facebook.com")**, **dig facebook.com** came back in:

;; Query time: 105 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Nov 26 23:51:50 2012
;; MSG SIZE  rcvd: 126

Web browsers often have their own DNS cache, so it is possible that TTL expired from your caching nameserver and it had to fetch fresh info for dig (do you forward to your ISP's nameservers or use root servers?).

I used to run bind9 using root servers for caching DNS many years when my ISPs DNS lagged and I used Linux as a pppoe router with a DSL bridge modem.  But I have not done that for a long time because the FreeBSD based modem/router I have had for about 10 years does its own caching DNS (and resolves local netbios names for machines that do Windows networking).

---

### Post by bab1 on 2012-11-27
> **efflandt said:**
> What exactly did you set up?  I didn't set up any DNS in 12.04 and it seems to have its own caching nameserver by default.  After doing **host facebook.com** and **host [www.facebook.com]("http://www.facebook.com")**, **dig facebook.com** came back in:

;; Query time: 105 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Nov 26 23:51:50 2012
;; MSG SIZE  rcvd: 126

Web browsers often have their own DNS cache, so it is possible that TTL expired from your caching nameserver and it had to fetch fresh info for dig (do you forward to your ISP's nameservers or use root servers?).

I used to run bind9 using root servers for caching DNS many years when my ISPs DNS lagged and I used Linux as a pppoe router with a DSL bridge modem.  But I have not done that for a long time because the FreeBSD based modem/router I have had for about 10 years does its own caching DNS (and resolves local netbios names for machines that do Windows networking).

The latest versions of Ubuntu use DNSmasq.  This due to Network Manager and the attempt to provide DNS on VPNs.  The cache is local to that host only.  See [**_[COLOR="Blue"]here[/COLOR]_** ]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/")for more info.

---

### Post by yizrahomme on 2012-11-29
> **bab1 said:**
> The latest versions of Ubuntu use DNSmasq.  This due to Network Manager and the attempt to provide DNS on VPNs.  The cache is local to that host only.  See [**_[COLOR="Blue"]here[/COLOR]_** ]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/")for more info.

Thanks, all.  Just out of curiosity, is there any reason why this was changed in Ubuntu, other than 'just for the heck of it'?

Anyway, I've now brought my laptop in to work, and am on my office's WiFi, and even curioser, nothing works but Skype.  I'm guessing that the router is disallowing outgoing TCP traffic on port 53 or something equally strange.

I tried commenting out the dns=dnsmasq in /etc/NetworkManager/NetworkManager.conf and restarting the Network Manager.  I tried adding the office DNS server in /etc/resolvconf/resolve.conf.d/head.  

Anyway, does someone know how to solve this?  If I shut down bind9 and reboot, then dnsmasq is still updating the /etc/resolv.conf so it's still pointing to 127.0.0.1.  Is it not possible to have two different network 'profiles', depending on where one is connecting?

Thanks.

---

### Post by yizrahomme on 2012-11-29
> **yizrahomme said:**
> Thanks, all.  Just out of curiosity, is there any reason why this was changed in Ubuntu, other than 'just for the heck of it'?

Anyway, I've now brought my laptop in to work, and am on my office's WiFi, and even curioser, nothing works but Skype.  I'm guessing that the router is disallowing outgoing TCP traffic on port 53 or something equally strange.

I tried commenting out the dns=dnsmasq in /etc/NetworkManager/NetworkManager.conf and restarting the Network Manager.  I tried adding the office DNS server in /etc/resolvconf/resolve.conf.d/head.  

Anyway, does someone know how to solve this?  If I shut down bind9 and reboot, then dnsmasq is still updating the /etc/resolv.conf so it's still pointing to 127.0.0.1.  Is it not possible to have two different network 'profiles', depending on where one is connecting?

Thanks.

Update: there was a problem with the company's primary DNS, and requests were timing out before the second was queried.

I've added the appropriate DNS box now to /etc/resolvconf/resolv.conf.d/head and am going to rustle up a script or two: 

athome.sh and atwork.sh to swap the appropriate file around and restart the network-manager.

---

