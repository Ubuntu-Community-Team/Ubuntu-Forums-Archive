---
title: "No Internet on Dell Inspiron 1501 with Ubuntu 12.04"
date: 2013-08-07
forum: Networking &amp; Wireless
---

### Post by James_Michael_Bell on 2013-08-07
I recently loaded Ubuntu 12.04 onto my girlfriend's Dell Inspiron 1501 and everything seemed to work fine... until I rebooted after the install. Now there is no internet access at all (wired or wireless).

I've tried nearly everything I can think of, from loading drivers through a live USB, downloading more recent drivers from the internet on my computer and installing them on her laptop, etc, but with no luck. I've also attempted to blacklist certain native drivers so the Dell drivers (such as b43) would have a chance to run over those provided by Ubuntu (ssb). This didn't work either. Since I cannot connect to the intetnet, I can't run an update through the terminal, nor can I install packages from the apt-get repositories. I'm stuck.

Any suggestions?

Cheers!

---

### Post by chili555 on 2013-08-07
Please tell us more; from a terminal, run and post:```
lspci -nn | grep 0280
```Thanks.

---

