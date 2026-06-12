---
title: "Need help with LIRC loading at bootup!"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by danman862 on 2007-03-21
Hello,
I have followed the LIRC HOWTO a few times...
I have almost everything working except LIRCMD (I posted yesterday)

I found out what the problem is, my lircd/lircmd loads AFTER X starts.
When my xorg.conf loads it can not find /dev/lircm and won't load the LIRC-Mouse.
How do I promote my lircd and lircmd to load first?  I am learning ubuntu, and
I just can't find out where to look.  Thanks in advance.

---

### Post by bdogg64 on 2007-03-21
add your module to /etc/modules (I added lirc_i2c) 

I hope this helps

---

