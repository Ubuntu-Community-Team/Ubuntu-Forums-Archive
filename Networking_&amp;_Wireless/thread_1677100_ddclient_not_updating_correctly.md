---
title: "ddclient not updating correctly?"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by Hawkoon on 2011-01-28
I am using ddclient with DynDNS to keep track of my IP and it has been working fine...until today. I found my IP out-of-sync, and forced an update
```
sudo ddclient -force
SUCCESS:  updating ALIAS: good: IP address set to xxx.xxx.xxx.xxx
```However, my server is still not available under ALIAS, and nslookup confirms this:
```
nslookup ALIAS
Server:        192.168.2.1
Address:    192.168.2.1#53

Non-authoritative answer:
Name:    ALIAS
Address: yyy.yyy.yyy.yyy

```So, the update seems successful at first, but nslookup shows that my alias is not pointing at the right IP. I tried forcing another update, but ddclient tells me it is not necessary because IP is up-to-date. Well, it isn't! Anyone knows what is going on?

---

### Post by gohsthb on 2011-02-04
I understand that sometimes DNS takes time to update.  I have read that sometimes it can take a couple of days even.

---

### Post by Hawkoon on 2011-02-05
Well, after my forced IP update things are back to normal, automatic IP updating and DNS translation are working as they should, but it took one or two two hours to take effect.

The strange thing was that according to my DynDNS account, my server alias was pointing at the correct IP, yet when entering it into Firefox or checking it with nslookup, it was translated to the old IP.

> **gohsthb said:**
> I understand that sometimes DNS takes time to update.  I have read that sometimes it can take a couple of days even.

Do you still have any links or references on that?

Thanks,
Hawkoon

---

