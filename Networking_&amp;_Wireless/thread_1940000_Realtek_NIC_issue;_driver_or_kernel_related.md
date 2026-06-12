---
title: "Realtek NIC issue; driver or kernel related?"
date: 2012-03-12
forum: Networking &amp; Wireless
---

### Post by caffeinated blood on 2012-03-12
I've been using Ubuntu 10.04 for a couple years now and decided to try some newer distros(Ubuntu 11.10, Kubuntu, Xubuntu and Linux Mint 12). I'm currently running a dual-boot Xubuntu/Windows 7 desktop. Trying all the stated distros, I notice that when i shutdown the computer, which is connected to a router via ethernet, that the LAN activity light/connection at the router, remains on. This did not happen with Lucid Lynx and does not happen if I shutdown through Windows 7.

I've removed the r8169 driver for my Realtek NIC and replaced it with r8168. No change whatsoever. So, does this seem to still be driver related or more likely to be kernel related? Also, is there any system file(s) that can be configured to shut this connection down?

---

### Post by caffeinated blood on 2012-03-28
Thanks to anyone who took time to read this post. Unfortunately, I don't think I explained it well enough for a proper response. Anyway, I've found the solution: the LAN activity light on my router would remain on after I shut down my computer, yet the LAN activity lights on the NIC on my desktop were off. The solution was to change my BIOS setting for WLAN from BIOS controlled to Operating System controlled. 

Digging around a bit more I've also found the solution for a previous post I had about my NIC activity lights remaining on after disabling networking via Network Manager.  This too was related to WLAN. I installed ethtool and disabled WOL on the NIC itself. Hoping that maybe this solution(s) might help someone else having the same issue(s).

---

