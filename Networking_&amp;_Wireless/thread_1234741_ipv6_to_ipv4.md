---
title: "ipv6 to ipv4"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by cybernet on 2009-08-08
how can i switch them ?
I'm using Ubuntu 9.04 Desktop
 
i wan't to change this because in php
when i use the command to show my ip
it showing ::ffff:my.IP - instead of my.IP

help me:(

---

### Post by Brandon Williams on 2009-08-08
I'm not exactly certain what you're doing in PHP to get the address. In C, I would typically use gethostbyname(), with which it's possible to explicitly specify which address type you're looking for. From the [PHP manual](http://us3.php.net/manual/en/function.gethostbyname.php), it looks like you can use gethostbyname in PHP, too.

---

