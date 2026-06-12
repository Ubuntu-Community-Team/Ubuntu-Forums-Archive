---
title: "Wifi driver"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by objc on 2010-01-20
Hey, so, I recently started dual booting my iMac with OSX and Ubuntu. The thing is, the wifi isn't working. I spent a couple hours searching around today, and it seems that Ubuntu doesn't have the necessary drivers to support my card.

My card is a BCM4321      14e4:4328.

I can't find any drivers online for it either. Any ideas?

---

### Post by teward on 2010-01-20
lspci in terminal to show us exactly what networking card is being detected by Ubuntu, please.

---

### Post by PRC09 on 2010-01-20
For broadcom cards......

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by objc on 2010-01-20
> **PRC09 said:**
> For broadcom cards......

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

That did the trick! Awesome!

---

