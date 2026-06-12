---
title: "Interesting wireless stuff"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by Zlatan on 2011-05-17
Hello, have Broadcom wirelss on my Lenovo notebook and Ubuntu has to install some additional drivers to make it work.
But! GNOME3 latest ISO (suppose it is Fedora?) recognizes it and wireless works even from live USB. How can this be? Free drivers work better than Ubuntu ones?

---

### Post by TBABill on 2011-05-17
If your card can use the b43 driver (or brcm80211?) then it is an open source and should work fine. Regardless which you use (b43 or proprietary), firmware is still necessary. I assume the live session connected via ethernet and got the firmware for you? Or did the live media contain the firmware?

---

### Post by Zlatan on 2011-05-17
> **TBABill said:**
> If your card can use the b43 driver (or brcm80211?) then it is an open source and should work fine. Regardless which you use (b43 or proprietary), firmware is still necessary. I assume the live session connected via ethernet and got the firmware for you? Or did the live media contain the firmware?

Live media did not show anything similar to connecting and getting any kind of firmware. It just worked. Different story with Ubuntu- wireless is not even shown as available until additional drivers are installed. That's the most interesting part- how it just works under GNOME3latest ISO live media...

---

### Post by TBABill on 2011-05-18
When I installed Ubuntu 11.04, I never did connect to a router. I simply ran the live session, installed the proprietary driver when it told me one was available, then instead of doing the reboot it said I needed to do, I simply did a: ```
sudo modprobe wl
``` and I was connected via wireless. It is possible to enable it from the liveCD if you know all the steps necessary to do so. For the b43 the steps would be just like what I did, only instead of what I did as the modprobe command you would ```
sudo modprobe b43
```

---

### Post by lizzycaplon on 2011-05-18
i am new on this forum, but i like this forum.

---

