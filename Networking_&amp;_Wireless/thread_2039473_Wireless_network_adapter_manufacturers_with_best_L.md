---
title: "Wireless network adapter manufacturers with best Linux compatibility record?"
date: 2012-08-08
forum: Networking &amp; Wireless
---

### Post by yang on 2012-08-08
Just for my own knowledge (and also because we're going to make a local Fry's run soon for a bunch of adapters for various desktops), are there any wireless network adapter manufacturers that I should generally stick to for zero hassles?

I Googled and found a bunch of websites with (often outdated or conflicting) lists of specific cards, but I'm hoping for more general rules of thumb, so I'm not always trying to Google for sufficient evidence of a certain card working and sufficiently little evidence of that card not working.  (Or at the very least, which such website is most comprehensive, most accurate, and I should heed the most?)

[Just today, I wasted a bunch of time on getting this Trendnet TEW-423PI/A C1.2R working on an Ubuntu 10.04 box - Ubuntu loads rtl8180 drivers, which caused very weak signal and disconnections within 10 minutes.  I downloaded and built rtl8185 drivers, and while I have stronger signal, I still get disconnected, albeit less frequently.]

---

### Post by kurt18947 on 2012-08-09
I've had good success with two USB WiFi adapters.  They've been plug -n- play for me.

- Netgear WNA1100
- Trendnet TEW-649UB

These are both N150 adapters.  Trendnet also has a TEW-64**8**UB adapter which looks identical but uses a different chipset that is I believe problematic in Linux.

---

### Post by Bucky Ball on 2012-08-09
Broadcom, Realtek. It can be a little confusing as there are millions of brands but not millions of chips. The Netgear, for example, probably uses a Realtek chip. Maybe the Trendnet does, too. I have an Open Networks Wifi dongle. It has a Realtek chip.

So, it's the brand of chip that is the main concern. A totally unheard of Wifi dongle brand may work 'out of the box' as it has a supported wireless chip. ;)

---

### Post by kurt18947 on 2012-08-09
> **Bucky Ball said:**
> Broadcom, Realtek. It can be a little confusing as there are millions of brands but not millions of chips. The Netgear, for example, probably uses a Realtek chip. Maybe the Trendnet does, too. I have an Open Networks Wifi dongle. It has a Realtek chip.

So, it's the brand of chip that is the main concern. A totally unheard of Wifi dongle brand may work 'out of the box' as it has a supported wireless chip. ;)

You're correct about paying attention to the chipset not the brand of the adapter.  Even the version can matter;  I've seen model ABC use one chipset and model ABC v.2 use an entirely different chipset.  The Netgear uses an Atheros AR9271 driven by the ath9k module.  The TrendNet uses a RealTek 8192SU chip.  Broadcom and Ralink seem to generate more than their share of support requests.

---

### Post by yang on 2012-08-09
Yes, the TrendNet uses a RealTek chipset, but it still caused a bunch of mayhem for me (and others as well - e.g. my symptoms were similar to those mentioned in this thread, but his solution didn't solve my disconnections: [http://ubuntuforums.org/showthread.php?t=1514691](http://ubuntuforums.org/showthread.php?t=1514691)).

I really, really, really want to avoid dealing with this after buying these adapters.

I'm also skeptical of anecdotal evidence ('works for me!'), which is why I posted here to ask about track records etc.

---

### Post by kurt18947 on 2012-08-09
> **yang said:**
> Yes, the TrendNet uses a RealTek chipset, but it still caused a bunch of mayhem for me (and others as well - e.g. my symptoms were similar to those mentioned in this thread, but his solution didn't solve my disconnections: [http://ubuntuforums.org/showthread.php?t=1514691](http://ubuntuforums.org/showthread.php?t=1514691)).

I really, really, really want to avoid dealing with this after buying these adapters.

I'm also skeptical of anecdotal evidence ('works for me!'), which is why I posted here to ask about track records etc.

Not all Realtek chips work equally well.  That thread talks about the RealTek RTL-8185, not the RTL-8192SU.  That's why it's important to pay attention to chipset 'model number' as well as the manufacturer.  The RTL-8192SU chipset had issues initially; it required a firmware version that was not included in distros prior to 11.04.  Most Intel wifi chipsets work well but there's one that does not have Linux support at all.  It only works with NDISwrapper.

---

### Post by katsumodo on 2012-08-11
To add my experience with these (whatever it's worth). The Netgear N150 WNA1000M USB micro adapter works with the rtl8192cu chipset. It sure took some work and I eventually had to download the windows xp driver from realtek's website and install it using ndiswrapper. Removing the default network manager and using WICD instead is also a fix sometimes.

---

### Post by kurt18947 on 2012-08-12
> **katsumodo said:**
> To add my experience with these (whatever it's worth). The Netgear N150 WNA1000M USB micro adapter works with the rtl8192cu chipset. It sure took some work and I eventually had to download the windows xp driver from realtek's website and install it using ndiswrapper. Removing the default network manager and using WICD instead is also a fix sometimes.

If that chipset is the same as the Edimax 7811Un, the driver from Realtek (8188CUS) works well for me and the included install script worked perfectly.  It may or may not be necessary to disable the 'built-in' driver.  I personally have not had much luck using NDISwrapper.

---

### Post by Bucky Ball on 2012-08-12
> **kurt18947 said:**
>   I personally have not had much luck using NDISwrapper.

Avoid. Can be a world of pain and largely superseded. ;)

---

### Post by bakegoodz on 2012-08-12
You can't just go with a brand, you have to figure out a chipset in a specific adapter. Stay away from Linksys and Netgear they like to switch chipsets in the same model number. Newegg reviewers often report the chipset and Linux/Ubuntu compatibility. I love the website [http://www.wikidevi.com](http://www.wikidevi.com), were you can lookup adapters for identifying chipsets and Linux compatibility. I personally like Atheros 9000 series chipset, because you get plug and play compatibility, 80211n, Master mode, and AP Mode. Ralink is often good, but sometimes you have to hunt down a firmware file with some of there newer chipsets.

---

