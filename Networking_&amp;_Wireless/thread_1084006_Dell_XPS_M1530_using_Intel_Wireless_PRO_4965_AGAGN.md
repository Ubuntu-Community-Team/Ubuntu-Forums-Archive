---
title: "Dell XPS M1530 using Intel Wireless PRO 4965 AG/AGN"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by matanlurey on 2009-03-01
Hi everyone. Long time lurker, first time poster.

I bought a new Dell XPS M1530 in late 2008. Up until this point I had 8.04 LTS installed, and everything (well, pretty much everything) worked great out-of-the-box.

I installed 8.10 yesterday, everything seemed to work, but I had tons of issues connecting to my WPA2 wireless network. After reading probably 500 threads concerning this (try Wicd, try this, try that) nothing worked.

I tried Fedora core 10 and Linux mint 6, both had the same WPA issue.

**Anyway, to the current problem:**

I finally made my wireless network unsecured, figuring it would give me more time to find the WPA problem, but at least let me use the internet directly.

It works, albeit horribly. Actual download and upload speed is horrendous (booting into Vista, I can download at about 1mb/s), something like 15 kb/s down and 3 kb/s up. On top of that, the internet stalls out and stops working entirely at random intervals. I either have to put the WLAN interface up/down or wait a little while for it to work again.

I'm using a Netgear Wireless N Extreme router.

**What should I do?**

I've read to try installing the compat-wireless package for bleeding-edge wlan drivers, but I'm really up to trying anything. At this point I'm running 9.04a5, with the same issues.

[EDIT]:

lshw -C network says I am using the "iwlagn" driver, while Intel's site says the "iwlwifi" would be the appropriate one to use for a 4965.

I've tried installing the backports as specified in [http://ubuntuforums.org/showthread.php?t=1041492&highlight=4965](http://ubuntuforums.org/showthread.php?t=1041492&highlight=4965)

---

### Post by Jason_077 on 2009-03-02
Hi.

Many people are having problems with Intel 4965 (included me).
Can you please post the dmesg output after your internet stalls?

Thx.

J77

---

