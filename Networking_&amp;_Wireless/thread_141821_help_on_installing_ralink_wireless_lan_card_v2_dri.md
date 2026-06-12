---
title: "help on installing ralink wireless lan card v2 driver"
date: 2006-03-09
forum: Networking &amp; Wireless
---

### Post by melquiades on 2006-03-09
guys,

      I have a compal fl31 laptop that has a ralink wifi card. The pic id for this
device is 1814:0302, which can't be found on the ndiswrapper list of drivers.
I tried installing the the rt2500 driver but it can't detect the wifi card. By the way, windows xp uses a driver by the name rt.sys ( one and only file ). Even tried using the rt.sys file but still nothing. I'm a linux newbie by the way and have tried everything I can do on this dilemma; from here I don't where to go. Please help, any help will be highly appreciated.

Thanks in advance,
melquiades

---

### Post by claes on 2006-03-09
I have done this at home but I have no access to that machine from here. I'll check when I get home and check what I did. By the way what output does this give you:
lspci | grep RaLink 

Claes

---

### Post by melquiades on 2006-03-10
This is the my linuxbox's sad reply to the 'lspci | grep RaLink' command

0000:01:02.0 Network controller: RaLink: Unknown device 0302

---

