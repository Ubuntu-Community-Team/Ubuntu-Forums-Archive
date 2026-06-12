---
title: "Yay Wireless/Madwifi Issues!"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by jeffrey296 on 2010-04-14
Ok, so I know a billion people out there have wireless issues when it comes to linux and I know there are about a billion solutions, but I've been browsing around for hours (actually months if you include the down time when I gave up hope) and still have found no solution.

So here I am! Coming to you, the gurus of the internet in the form of Ubuntu Forums with my problem (and relevant information):

I have a **Compaq Presario C700**. My chipset is an **AR5001** from **Atheros** (gathered from [FONT=Courier New]lspci[/FONT]). My wireless *used* to work with madwifi drivers, but at random boots the computer would not recognize the modules and the wireless would not work at all. Eventually, it stopped working for good. I just recently (today) downloaded the madwifi-0.9.4-r4126-20100324.tar.gz from Madwifi and used [FONT=Courier New]make[/FONT] and [FONT=Courier New]make install[/FONT] (and [FONT=Courier New]modprobe ath_pci[/FONT]) -- still no wlan0, wifi0 or ath0 in [FONT=Courier New]ifconfig[/FONT].

Kernel version: **[FONT=Courier New]2.6.31-20-generic[/FONT]**
Ubuntu distro: **9.10** (**Karmic Koala**, I think)

Before trying the above steps, I ran [FONT=Courier New]aptitude update[/FONT] and [FONT=Courier New]aptitude install build-essential[/FONT].

One more note: whenever I run [FONT=Courier New]make install[/FONT], I get a warning somewhere that says something like WARNING: -e needs -E or -F.

Any help would be appreciated, and I can provide more information on request.
Thanks all.

---

