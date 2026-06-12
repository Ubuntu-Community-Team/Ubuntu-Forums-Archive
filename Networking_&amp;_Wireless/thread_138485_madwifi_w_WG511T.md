---
title: "madwifi /w WG511T"
date: 2006-03-02
forum: Networking &amp; Wireless
---

### Post by pbransford on 2006-03-02
Well, i have a WG511T revision C (version 3 in other words, I assume). it is known compatible with madwifi.

Poped in my ubuntu 5.04 install CD, installed, no problems, everything working PERFECTLY*. Later on, borked the system (my own fault, unrelated to issue).

Now, upon reinstalling (multiple times now) using the same disks and same options, etc.... i get no ath0 device and dmesg reports:
"HAL status 13" relating to the ath_pci ath_hal modules. Apparently this means "unknown device" or somesuch.

Well, it aparently works, and I can not understand why it would decide to stop working out-of-the-box. It works in SuSE, but with a crappy signal, using madwifi as well.


Any suggestions? Is it possible to cram a particular card version/chipset name down the ath_* modules' throats?


(note that I am posting through windows and do not currently have a working linux system now)


* Excellent signals, speeds, all modes working (including the holy monitor mode). I didn't need to do anything besides "iwconfig ath0 essid SSIDNAME" and running dhcp to get it up.

---

### Post by pbransford on 2006-03-02
Oi! I'm a moron.

I had actually installed Breezy (5.10) the first time round. Apparently 5.04 comes with a slightly older (and uncompatible) madwifi version.



Dur! don't even need to try again to know this will fix the problem. :rolleyes:

---

