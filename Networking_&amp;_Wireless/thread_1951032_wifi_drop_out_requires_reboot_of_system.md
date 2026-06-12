---
title: "wifi drop out requires reboot of system"
date: 2012-04-01
forum: Networking &amp; Wireless
---

### Post by Kevin McCready on 2012-04-01
I've checked many forum posts on this problem. It seems it occurs regardless of Linux operating system or wifi card or whatever.

Could someone please write a sticky on this for us all. When I searched titles for "Sticky wifi" nothing came up.

I'm getting sick of rebooting the computer while other people on my home network running the old bloated legacy system don't have a problem.

Meantime, if someone can help, that would be great.

---

### Post by nothingspecial on 2012-04-03
*Thread moved to **Networking & Wireless**.*

---

### Post by alex.nucleo on 2012-04-03
If I understand you correctly, you mean when your PC looses connection, you have to reboot your system to make it working again.

If so, I can suggest a workaround that could be less painful than rebooting:
> gksudo killall NetworkManagerThis will stop default network manager, then it will automatically restart and try to reconnect. Sometimes it helps. I personally have a script on my desktop that contains above line and I run it very often.

Unfortunately, I suffer from similar problems: NetworkManager in Ubuntu is big bloated piece of sh*t and it never works stable for me, even when I setup the latest drivers in my system. Every new version of NM is worse than previous ones. I don't understand, why they spend so much time to polish UI, but cannot fix NM for ages. When I install new version of Ubuntu I ALWAYS get problems with NM, can't remember any time I didn't. It looses connection to Wi-Fi, it cannot connect to wired network. The last thing: in 12.04 it simply ignores all Wi-Fi connections and doesn't even show them in the list, though I've installed proprietary drivers "Tested by Ubuntu team" and they were working on previous version of the system on the same hardware. It's such a shame, Ubuntu team.

UPDATE: I've managed to install working drivers. I just had to remove what had been installed with "Additional drivers", then search Software Center for "b43", which is the name for driver for my Broadcom wi-fi card, install that and after reboot everything works. Still I don't understand why they say "Tested by Ubuntu team", when it's completely not working. How do they test?..

---

### Post by praseodym on 2012-04-03
Because the firmware for the b43 driver is proprietary, not open source ;-)

---

### Post by alex.nucleo on 2012-04-03
> **praseodym said:**
> Because the firmware for the b43 driver is proprietary, not open source ;-)

Cool. But why Ubuntu suggests me to install this proprietary driver, saying that is "tested" and safe to install, I do install it via wired connection and after that NetworkManager not only fails to connect to wi-fi, it even stops showing wi-fi section in the menu at all. Do you think this behavior is correct? Do you think it shouldn't say something like "sorry, but your driver is not appropriate, please try another one"? Is it user friendly to ignore errors and hide them from user? Is it user friendly to say that something is tested, when it is not? And please, don't tell me it is Broadcom who stops Ubuntu team from fixing NM, which is broken in all possible ways for ages ;)

---

