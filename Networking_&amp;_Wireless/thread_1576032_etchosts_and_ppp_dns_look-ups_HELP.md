---
title: "/etc/hosts and ppp dns look-ups HELP"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by Thameslink on 2010-09-16
I've set up a custom entry in/etc/hosts to point to a sub-domain I'm working on that isn't yet registered with any DNS.

When I try to connect via mobile broadband it ignores that and resolves the address without my change in /etc/hosts.

I presume that some ppp config file has a list of DNS addresses it uses. Do I need to specify that it should look in /etc/hosts?

Many Thanks
Jake

---

### Post by DirtDart on 2010-09-17
It sounds like, when connected to the mobile broadband, it is using DNS before hosts, which is the opposite of the default action.

While connected to your mobile broadband, get the output of:

```
sudo grep hosts /etc/nsswitch.conf
```

```
cat /etc/hosts
```

---

