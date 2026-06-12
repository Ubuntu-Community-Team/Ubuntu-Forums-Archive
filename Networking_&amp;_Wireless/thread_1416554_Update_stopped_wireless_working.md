---
title: "Update stopped wireless working"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by vegesm on 2010-02-26
I've 9.04 and a bcm4312. When I installed ubuntu half a year ago the wireless didn't worked of course. I've found a solution and I was happy with it. It was a modified broadcom sta driver.
Then with the latest update something was installed and now I can't get my wireless get to work again. The modified driver simply doesn't work, produces the same error as the original unmodified broadcom STA driver. So i need to revert that update somehow.

I found out that there are other *.ko files in the /lib/kernel-name/volatile directory which weren't there before the update.
Booting in to older kernel doesn't help.

---

