---
title: "Dell Inspiron 6000 Ubuntu 11.04 Wireless not working"
date: 2012-12-23
forum: Networking &amp; Wireless
---

### Post by shan2812 on 2012-12-23
Hi,

I installed Ubuntu 11.04 on Dell Inspiron 600 today, but wireless isn't working.

I tried following the instructions given on some of the similar threads, but I could not get through,possibly because I am quite new to Ubuntu.

It would be of great help if someone could help me out. 

Thank you.

Cheers
Shan

---

### Post by Hadaka on 2012-12-23
Hi please post the output of.

```
lspci -nn | grep 0280
```

thanks.

---

### Post by Bucky Ball on 2012-12-23
Welcome to the forums.

11.04 is no longer supported. Try the latest, stable, LTS release, 12.04 LTS, long-term support until April 2017 and a much better place to start.

Even if you did manage to get 11.04 working, your security will be compromised.

---

### Post by shan2812 on 2012-12-24
Thank you, switched to 12.04 and wireless did work out of the box.

Thanks for the support..

---

### Post by Bucky Ball on 2012-12-24
Great news. I had a feeling that might happen. You're set for the next four and a half years, but you may want to install a newer version on another partition to play around with once you're confident. I always have a stable LTS , production install that I can rely on and a couple of others which are my playthings. 

Please mark the thread as 'Solved' from Thread Tools at the top right of this page to help others ...

Enjoy the OS, the learning curve and the forums ... ;)

---

