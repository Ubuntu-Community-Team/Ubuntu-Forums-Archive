---
title: "WMP600N Linksys by Cisco on Ubuntu 8.10 a good fit?"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by YMS_1975 on 2009-04-14
Hey all,

My son's 8th birthday just passed and he was given a hand-me down PC as a learner kit. It's an entry-level Pentium processor with 82 GB HD and 1 GB Ram.

Long story short, it has a network card in it however I wish to go wireless as I do not want to have wires running from my desktop PC in the basement to his bedroom (where his PC is).

I've been looking at networking cards and the [Linksys by Cisco model #: WMP600N]("http://www.linksysbycisco.com/CA/en/products/WMP600N") looks inviting. I was wondering if anybody know about how well this model will work with Ubuntu.

---

### Post by YMS_1975 on 2009-04-17
I guess nobody has had experience with this card. How about any cards that you would recommend?

---

### Post by abatcher on 2009-07-26
Still no one around that tried this card ?

---

### Post by zuzuzzzip on 2009-07-28
It works. Follow this guide: [http://ubuntuforums.org/showpost.php?p=5114684&postcount=41](http://ubuntuforums.org/showpost.php?p=5114684&postcount=41)

---

### Post by abatcher on 2009-08-03
I bought this card and it seems to work out of the box, with NetworkManager.

But not really.... I'm getting disconnects all the time, while my macbook doesn't have any troubles staying connected to the AP.

dmesg keeps outputting something like:
[41063.585442] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329

---

### Post by jeffyboz on 2009-08-28
> **abatcher said:**
> I bought this card and it seems to work out of the box, with NetworkManager.

But not really.... I'm getting disconnects all the time, while my macbook doesn't have any troubles staying connected to the AP.

dmesg keeps outputting something like:
[41063.585442] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329

Well, how's the card working out?  I'm going round and round with Netgear WN311B-100NAS; but, I'm thinking about trading out for WMP600N.  What do you think?

Thanks!

---

### Post by abatcher on 2010-01-12
Still disconnects all the time on 9.04, kernel built in rt2860sta driver (v1.8.0) and with the 2.2.0 driver (compiled it myself)

I'm reluctant to upgrade to 9.10, because the bug reports say it's even worse there.

---

### Post by abatcher on 2010-01-13
Actually, the 2.2.0 driver seems to stay connected more, but everytime
*rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329*
shows up in /var/log/messages, the connection is dropped for a few seconds.

---

### Post by srwilde on 2010-03-19
I got a LOT of disconnects with this card.  I'm on Ubuntu 9.10 with the default driver.  On the up side, it came right up at build time.

kernel: [52967.493271] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 201

---

