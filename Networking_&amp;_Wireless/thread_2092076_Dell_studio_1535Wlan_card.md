---
title: "Dell studio 1535Wlan card"
date: 2012-12-06
forum: Networking &amp; Wireless
---

### Post by Ryaniskira on 2012-12-06
I have a Dell Studio 1535 Laptop with Ubuntu 12.10. When I installed Ubuntu the wireless card worked and I updated a few packages that required a reboot. When the computer booted up the wireless card isn't even visible. I had a wireless card issue on other Dells and the card at least came up as firmware missing and I was able to use the 3rd party driver tool and a script I wrote to get the card working. Well I installed the 3rd party driver tool and It doesn't show up even though Software center says its installed. FwCutter wont do it either.  I need to get this card working for my friend. HELP! I think its a Broadcom I don't know. If someone has a script that can fix it please contact me.

It is a Broadcom BCM4322

---

### Post by chili555 on 2012-12-06
Please run and post:```
lspci -nn | grep 0280
```The pipe symbol is on the same key with \ on the right side of my US keyboard. Thanks.

---

