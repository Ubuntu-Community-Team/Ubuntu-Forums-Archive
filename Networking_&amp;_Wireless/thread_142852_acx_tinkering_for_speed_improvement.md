---
title: "acx tinkering for speed improvement"
date: 2006-03-11
forum: Networking &amp; Wireless
---

### Post by MrCheese on 2006-03-11
I recently discovered the acx module in Dapper Flight 4 actually works with my cheap'n'cheerful SafeCom 54108 cardbus wifi card. It was however a bit flaky & prone to dropping out or running v-e-r-y s-l-o-w-l-y. I decided to experiment bu substituting the firmware (in /lib/firmware/acx/default) with that supplied with the card as part of the XP drivers (well, they do work, and reliably!).

So, I copied over the firmware files into /usr/lib/firmware/acx then symlinked each entry for my card (acx111 chipset) to the relevant file - FwRad16.bin_2.3.1.31 in my case. Like magic, the card is now both faster & way more reliable, and now runs quite happily away from my access point.

Hope this is of help to those of you still fighting with variants of the acx1xx.

---

