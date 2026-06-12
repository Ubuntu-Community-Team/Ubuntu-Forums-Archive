---
title: "How can I authenticate Ubuntu additional drivers offline? (Or how do Broadcom 440x?)"
date: 2012-08-08
forum: Networking &amp; Wireless
---

### Post by Kenny95 on 2012-08-08
I've got an unlucky combination, I guess. I've got a Broadcom 440x Integrated Controller for the ethernet, and a Dell Wireless 1395 WLAN Mini-Card. That means no connection to the internet from Ubuntu Startup. Ndiswrapper and b43 didn't work, and it takes a very long time to install additional applications that I don't even understand when I have to switch back to Vista to use the internet.

I've only been using linux for a day here, but since this is user-friendly Ubuntu, I should be able to install the drivers as long as I'm competent enough to learn and follow instructions. Unfortunately, I can't come up with any ideas regarding Linux myself.

My last hope seems to be Ubuntu's Additional Driver, Broadcom STA Driver for Linux, but Ubuntu authenticates online! If I can't authenticate what I need to connect to the internet or get a package that will help me with this, then I'll have to hang it up and go back to XP.

TL;DR:
-How can I authenticate additional drivers offline?
-What driver can I use to get my Broadcom 440x working?

---

### Post by chili555 on 2012-08-09
> My last hope seems to be Ubuntu's Additional Driver, Broadcom STA Driver for Linux,Perhaps and perhaps not. Typically, cards that work with b43 and firmware do not work with STA and vice-versa. Some additional details will help us greatly. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

