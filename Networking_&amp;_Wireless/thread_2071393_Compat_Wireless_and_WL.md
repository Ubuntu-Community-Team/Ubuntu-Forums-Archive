---
title: "Compat Wireless and WL"
date: 2012-10-15
forum: Networking &amp; Wireless
---

### Post by ninocass on 2012-10-15
Hi All

I have a Mac Book Air which is running 12.04

The onboard wifi card is a  BCM43224 802.11a/b/g/n which means either the closed source WL drivers or the open source B43.

I have the need to use the card with injection mode for wireless testing so the B43 is the answer however I have found it to be unstable with my wireless N network and the WL module performs much better.

I have installed the B43 drivers by using the compat wireless packages from the ubuntu repos however when I install these WL fails to load properly whilst B43 works perfectly.

dmesg reports issues WL has issues with cfg80211 and refuses to load.

At the minute I have installed 2 kernels, one with compat and the other with WL.  This seems to work however it is a pain to have to restart every time (tho the MBA does it in 10 seconds) has anyone managed to get WL and compat to happily coexist?

---

