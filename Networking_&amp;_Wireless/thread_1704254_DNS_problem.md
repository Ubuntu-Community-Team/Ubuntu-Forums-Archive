---
title: "DNS problem"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by oldfart101 on 2011-03-10
Ubuntu Desktop 10.04 LTS - the Lucid Lynx
I don't know what I did!
Can't browse the internet, or do a wget
If I ping [www.bbc.co.uk]("http://www.bbc.co.uk") - I get 'unknown host [www.bbc.co.uk]("http://www.bbc.co.uk")'
but if I ping 212.58.224.138 - Iget a response
think I might have a dns issue, there is a dns server in my system|preferences|network connections!
but I can access the machine on the local network

---

### Post by randumnumber on 2011-03-10
try changing your dns server? maybe the one you where using isn't in use or is broken.

---

### Post by timsdeepsky on 2011-03-10
Ubuntu 10.10
I ran into this over the last 2 weeks using Firefox....Now Firefox has became unusable to me(have even reinstalled firefox)....It takes minutes to simply load pages....I can ping ip addresses fine in terminal,,but not the domain name(it times out)....I have no problem though with Chromium....So mine remains unresolved also....

---

### Post by chili555 on 2011-03-10
@oldfart101--

Please post:```
cat /etc/resolv.conf
```

---

