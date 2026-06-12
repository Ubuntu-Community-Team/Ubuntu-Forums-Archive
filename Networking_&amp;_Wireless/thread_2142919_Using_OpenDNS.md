---
title: "Using OpenDNS"
date: 2013-05-07
forum: Networking &amp; Wireless
---

### Post by jsvidyad on 2013-05-07
What are the IP addresses of the openDNS DNS servers? How do I set up my ubuntu laptop to use the openDNS DNS servers? Do I have to register to use the openDNS DNS servers?

---

### Post by prodigy_ on 2013-05-07
OpenDNS is [garbage](http://en.wikipedia.org/wiki/OpenDNS#Issues.2C_conflicts_and_Google_redirection). Use [Google Public DNS](https://developers.google.com/speed/public-dns/) instead.

---

### Post by CharlesA on 2013-05-07
> **jsvidyad said:**
> What are the IP addresses of the openDNS DNS servers? How do I set up my ubuntu laptop to use the openDNS DNS servers? Do I have to register to use the openDNS DNS servers?

Technically you don't have to register and you can just tell your machine to use their DNS servers:

```

208.67.222.222
208.67.220.220

```

If you want parental controls or whatever I think you have to register.

With that being said, I don't use OpenDNS, I either use Google's DNS or a couple servers from the [OpenNIC Project]("http://opennicproject.org/").

As far as configuring your machine, it would depend on what version of Ubuntu you are using.

---

### Post by clearski on 2013-05-07
> **jsvidyad said:**
> What are the IP addresses of the openDNS DNS servers? How do I set up my ubuntu laptop to use the openDNS DNS servers? Do I have to register to use the openDNS DNS servers?


This tells you how to use OpenDNS:
[https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)

&

This tells you how to use Google's DNS:
[https://developers.google.com/speed/public-dns/docs/using](https://developers.google.com/speed/public-dns/docs/using)


Your choice. :)

---

### Post by jsvidyad on 2013-05-07
Hello,

   Is there any particular reason why you prefer Google DNS rather than OpenDNS ?

---

### Post by clearski on 2013-05-08
> **jsvidyad said:**
> Hello,

   Is there any particular reason why you prefer Google DNS rather than OpenDNS ?

To me there are two reasons for using OpenDNS:

- the first is to stimulate competition (I believe that Google's DNS work better, but having just one big provider isn't a good perspective from my own point of view)
- the second is that I don't like the idea of Google knowing more than it already knows

But, as you said, these are personal (particular) reasons. Yes, I've been using OpenDNS for some time. Some people might have had problems with it, but it was just fine to me.

---

### Post by jsvidyad on 2013-05-08
Do I have to register to use google DNS  servers?

---

### Post by CharlesA on 2013-05-08
> **jsvidyad said:**
> Do I have to register to use google DNS  servers?

You don't need to register to use Google's DNS servers, or the OpenNIC Project DNS servers.

---

### Post by jsvidyad on 2013-05-09
What are the IP addresses for the google DNS servers?

---

### Post by CharlesA on 2013-05-09
> **jsvidyad said:**
> What are the IP addresses for the google DNS servers?

[https://developers.google.com/speed/public-dns/](https://developers.google.com/speed/public-dns/)

---

### Post by haqking on 2013-05-09
I see alot of people recommend one DNS provider over the other, when it is only something you can experience for yourself and not a universal constant, there is no universal answer, it will depend on your location, ISP etc.

If you want to see what the "best" one is in terms of performance/speed/reliabiity for your location and connection then:

[https://code.google.com/p/namebench/](https://code.google.com/p/namebench/)

If you run it in Linux it is a python script, in Windows it is a .exe.

Peace

---

### Post by CharlesA on 2013-05-09
> **haqking said:**
> 
If you want to see what the "best" one is in terms of performance/speed/reliabiity for your location and connection then:

[https://code.google.com/p/namebench/](https://code.google.com/p/namebench/)

If you run it in Linux it is a python script, in Windows it is a .exe.

Peace

+1. I've used it before and it's very nice.

---

