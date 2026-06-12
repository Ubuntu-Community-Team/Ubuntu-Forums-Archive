---
title: "Internet connection problem, probably dns"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by konrad.g on 2010-09-06
When i try connect to any web page on Firefox or Opera i have 404 error, but when I launched chromium all web pages loads normally.
On google I found that, I should disable ipv6 in firefox - its work for firefox, but still on Opera I have errors. On opera I tried connect using only ip and it's work. Also I noticed that some apps  have problem with connection (for example: playonlinux), but apps like skype or update manager are working. I have no idea how to fix problem ;(

---

### Post by lovinglinux on 2010-09-07
Disable ipv6 through grub instead of Firefox preferences. See [http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html)

---

### Post by konrad.g on 2010-09-07
Thanks for reply ;)

When I changed /etc/default/grub file and then I updated grub I had error:

/etc/default/grub: 9: quiet: not found

I'm using Ubuntu 10.04 LTS

---

### Post by lovinglinux on 2010-09-07
> **konrad.g said:**
> Thanks for reply ;)

When I changed /etc/default/grub file and then I updated grub I had error:

/etc/default/grub: 9: quiet: not found

I'm using Ubuntu 10.04 LTS

This is the second time I see such error. Unfortunately, I don't know how to solve it.

---

