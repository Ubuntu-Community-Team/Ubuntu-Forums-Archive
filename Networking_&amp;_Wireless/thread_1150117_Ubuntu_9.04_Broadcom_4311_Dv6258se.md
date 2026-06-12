---
title: "Ubuntu 9.04 Broadcom 4311 Dv6258se"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by supernova457 on 2009-05-05
Hello Ubuntu users, I've been having problems and researching this for over a couple of weeks, I'm quite new to Ubuntu and don't know much about Linux in general, anyhow.

I've been swapping distros for a while now, from Ubuntu 8.10 to Opensuse 11.1, then I tried Mint 6 Felicia, then a friend convinced me to try Ubuntu 9.04 again.

I had the BCM4311 working for a while in 8.10 (about a month) then for some reason one day it decided to stop. I could never get it working again (re-install, ndiswrapper, b43, b43legacy) so I switched to Opensuse. After much toil in that, I got it to work. Success I thought. After I rebooted, it stopped working, so I went to Mint 6 to try that, no luck. Now I'm back in Ubuntu 9.04 and still trying to get this working.

I do lspci (in 9.04) and I find no Broadcom extension, though I am sure my system has a BCM4311 card.
Iwconfig returns me with
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```And when I click on the little network icon in the top right, it only shows Wired Connection, and no Wireless connection arrow.
From sources that I've read, Linux simply does not cope well with BCM4311 cards or any BCM 43-- cards for that matter.

I suppose my final question would be what do I do next, or should I simply try another approach? (USB card, or switch back to the dreaded Windows)

---

### Post by supernova457 on 2009-05-06
Bump, I really need an answer.

---

### Post by wheredidrealitygo on 2009-05-06
Are you able to get on the internet through an ethernet cable? If so, install the "b43-fwcutter" utility through synaptic (or apt on the command line). 

It will automatically extract the firmware and configure your wireless card, you should then be able to use it properly.

---

