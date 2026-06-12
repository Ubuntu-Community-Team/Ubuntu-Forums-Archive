---
title: "Help needed: I broke my graphics drivers"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by brokerjoker on 2006-11-07
Hi,

I run Dapper with an ATI x1300 and usually the ATI drivers V8.29.6. I tested to configure dual head with Xinerama, but I the mouse cursor seems to be garbled on screen 1 due to a bug.

The idea was to reuse the opensource ati-driver, I was told that it does not have this problem. So I changed the "fglrx" in xorg.conf to "ati". X does not start anymore, sais it didn't detect any devices.

Hm.

So I reinstalled the default kernel modules and removed fglrx and tried again. Nothing, no X.

Well OK, I could always run vesa. I thought that. Wrong. Vesa fails with a totally garbeld screen.

Please help me - what do I have to install to get X running again, favourable with the OS-ati-drivers?

OR

Being at that point - is it time to jump to Edgy using apt-get dist upgrade? Will this reconfigure the driver stuff at least so that I can work again?

Thanks for alle ideas in advance!

BJ

---

