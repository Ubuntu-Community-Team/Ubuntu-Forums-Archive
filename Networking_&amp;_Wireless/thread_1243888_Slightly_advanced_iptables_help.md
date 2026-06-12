---
title: "Slightly advanced iptables help"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by thegammaray on 2009-08-18
hi, longtime reader firsttime writer ;)

So, I've been using Ubuntu for a while, but I'm not technically savvy enough to solve my current problem. I've dug through some iptables tutorials, but no luck. Here's my situation:

I have a computer in a public place in the home. This computer is used by all for various tasks (music, documents, etc.), but I want to restrict internet access. Ideally, the administrator will control all internet access; this might mean blocking all outgoing traffic until the root password is supplied; this might mean creating multiple user accounts and blocking outgoing traffic for all but the administrator. Regardless of the method used, the policy needs to revert to the default (restricted) upon restart.

I've used Firestarter in the past, but for obvious reasons I'd rather stick to current software. I've messed around with gufw a bit, but it seems gufw does little in the outgoing lane. Is this specific to gufw, or is it inherent in ufw?

At any rate, a little lesson in iptables might be interesting :) .

---

### Post by superprash2003 on 2009-08-19
you could try PROXY, read a bit on squid

---

### Post by thegammaray on 2009-08-19
I don't mean to be obtuse, but I've done some reading and I fail to see how this would help me. Squid isn't designed for anything even remotely similar to what I'm doing (as far as I can tell; perhaps I'm misunderstanding).

At bare minimum, all I really need is a bit of help constructing a script which would alter my iptables configuration, and another to reverse the changes.

---

### Post by dmizer on 2009-08-19
A proxy will do exactly what you want.

Send all internet traffic through a password protected proxy. If the password is not supplied, traffic will not be sent through the proxy. You can also set up user accounts and may other features.

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid)

---

### Post by thegammaray on 2009-08-20
Yeah..... so I understand the basic idea of the software, but I think implementing this is way over my head. I was hoping for a rather simpler method.

Obsolete though it may be, I guess I'll stick with Firestarter since it takes (literally) about 15 seconds to do what I'm trying to do.

---

