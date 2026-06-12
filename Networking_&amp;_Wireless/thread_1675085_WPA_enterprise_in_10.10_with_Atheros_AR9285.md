---
title: "WPA enterprise in 10.10 with Atheros AR9285"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by 22namphcar on 2011-01-24
My laptop uses an Atheros AR9285 wireless card, and I often have trouble connecting to the WPA enterprise networks at my university. I'll enter my credentials, and the NetworkManager applet will remain in the first stage animation (the first stage consists of rapid sweeps of the lighted arc, the second stage has the lighted arc moving more slowly, and the final stage is establishment of connection). Eventually it'll prompt me for my credentials again, and the cycle repeats a couple times before NetworkManager gives up. I have installed the linux-backports-modules-wireless-maverick-generic package, but to no effect. The fault is not with the wireless network -- my Win7 installation connects just fine.

Any suggestions?

When using Fedora 14 on the same computer, I never have trouble connecting to WPA enterprise networks. Moreover, NetworkManager seems to start reconnecting bit faster when resuming from suspend than in Ubuntu. 
In fact, this has been true for the past few releases -- Fedora always connects to WPA enterprise, while the corresponding version of Ubuntu will often have problems doing so. Why is this? Does Fedora just consistently use a less buggy kernel or NetworkManager or wireless driver? Or might this have something to do with the use of traditional glibc in Fedora and eglibc in Ubuntu and Debian? Mind you, I have also observed similar WPA-enterprise problems in Debian Squeeze on the same computer.

---

### Post by avaldi on 2011-03-25
up!

---

