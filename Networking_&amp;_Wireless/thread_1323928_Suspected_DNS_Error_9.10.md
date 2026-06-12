---
title: "Suspected DNS Error 9.10"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by Alphajuno on 2009-11-12
Hi,

While I've been using Ubuntu a while I'm still a novice, so please bear with me.

Since I upgraded to 9.10 my Internet connection hasn't worked correctly. Websites take ages to load, but once loaded I can generally move around within the sites OK.

Does anybody have any ideas for the fainthearted?

---

### Post by hal10000 on 2009-11-12
Sometimes it helps if you disable IPv6. Look [here for a short description.]("http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html")

---

### Post by Alphajuno on 2009-11-12
Yes!

That fixed it. Thanks a bunch. :D

---

### Post by Logan1985 on 2009-11-12
I also had this issue but it was due to the primary DNS server issued by DHCP being unreachable (which never made a difference in Windows, but had a severe impact in Ubuntu)

A short term fix is to comment out or remove the offending IP from /etc/resolv.conf (sudo gedit /etc/resolv.conf)

But I just altered the DHCP scope to remove the server entirely.

---

