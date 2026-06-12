---
title: "can browse but not able to ping. . help"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by felixvah on 2009-10-18
I'm pretty new to Ubuntu and currently install and use Ubuntu 9.04.  What I'm try to accomplish is sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 1781bd45c4c3275a34bb6aec6e871c4a881574de.  I've an error:
gpg: requesting key 881574DE from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

I came a cross some thread and they referred to try it again later possible cause were the server might be down.  I've been trying for two three days and got no where.

I found that within my system itself, I can browse using firefox without an issue, but when I try to ping I've 0% accomplish.  Does any one have any idea what cause the issue?  I can't even ping google.com. .

---

### Post by hal10000 on 2009-10-18
Maybe your firewall blocks pings.

---

### Post by jward3010 on 2009-10-18
> **hal10000 said:**
> Maybe your firewall blocks pings.
Thats the most common cause. If you know how go into your routers configuration page, the option to switch it on or off might be under something called ICMP requests as well as ping requests. Thats tripped me up in the past.

---

