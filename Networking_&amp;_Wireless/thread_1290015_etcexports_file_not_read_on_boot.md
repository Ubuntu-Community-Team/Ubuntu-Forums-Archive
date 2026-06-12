---
title: "/etc/exports file not read on boot"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by netimen on 2009-10-13
I added some entries into my /etc/exports file. But when I boot my system, the file is not read. I check it by ```
sudo exportfs
``` &#8212; it returns nothing

Then I run ```
sudo expotfs -a
``` and then again ```
sudo exportfs
``` &#8212; and now all my exported folders are listed.

---

