---
title: "howto debug slow WLAN connection?"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by edgue on 2009-03-02
Hi there,

My Lenovo 61P is happily connecting to my WLAN router at home; I can ping to the WLAN router and to the gateway modem of my provider without any problem. 

BUT - anything that goes out to the internet takes .... forever. Sometimes it is a bit faster; but in general the connection is way "slower" compared to my old Windows XP experience. 

The really strange thing - as soon as I invoke the AT&T vpn client to connect to my companies intranet ... the problems are gone. The same website that would take a minute to load before is now showing up within seconds. 

To me that sounds like some DNS or whatever problem - but I specified the same DNS servers for my connection that I am using with my Windows XP installation. 

So - where should I look to find the root cause for this problem? It is really annoying to see that my otherwise nice Linux installation is giving me such troubles ...

---

### Post by edgue on 2009-03-13
Again; I got my answer from a different place.

Turned out that the resolv.conf.d auto-generated resolv.conf was no good when working from home.

---

### Post by Ezetreal on 2009-03-14
Hi

Would it be possible for you to give a bit more detail about what the problems were and what changes you've made ?

I have an intel 3945abg card and I've been having issues with a slow connection that would sometimes disconnect when under heavy load...

Thanks

---

### Post by edgue on 2009-03-15
The auto resolv.conf.d process rebuilds the resolv.conf file during startup. For some reasons, this auto generated resolv.conf includes nameserver entries that point to DNS servers of my company. These work fine when you are in our INTRANET ... but when I start my laptop at home, any DNS request to one of these servers will need a lot of time ...
When starting the AT&T dialer, that program will overwrite the resolv.conf file and now any DNS requests are executed much faster.

My solution is a little helper script that I invoke manually when logging in at home (when i dont want to start the AT&T dialer because I DONT want to login my companies intranet). This script overwrites the resolv.conf file and inserts nameserver entries that work for my DSL provider.

But I think this wont help you - as it has nothing to do with networking hardware; and with the wrong nameservers ANY request needs a lot of time; independant of network load.

---

### Post by Ezetreal on 2009-03-15
Thanks for the reply, although you are probably right, it won't help me much... Maybe it will help someone else...

Cheers

---

### Post by saechen on 2009-03-28
Thank you so much this is exactly what was causing my problem!!!

---

