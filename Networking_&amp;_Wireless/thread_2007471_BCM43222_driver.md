---
title: "BCM43222 driver"
date: 2012-06-20
forum: Networking &amp; Wireless
---

### Post by Mark Uhde on 2012-06-20
Hello, I purchased a BCM43222 mini-PCI card cheap on Ebay to replace an Atheros card in my mother's computer that was losing connection, a lot.

The seller did warn that the card didn't work on Linux in the item description, but I figured that wouldn't apply to Ubuntu because Ubuntu has always for other Broadcom systems just offered me the proprietary Broadcom-STA driver and "just worked" when I chose to install that.

Additional drivers shows nothing with this card, there's no wireless, it's like it doesn't exist. Any ideas what (if any) driver might get this card to work? I'm not incredibly Linux-savvy, what should be my first steps in getting it working, I can't find anything online at all.

---

### Post by chili555 on 2012-06-20
The first step is to tell us more details. Please open a terminal and run and post:```
lspci -nn | grep 0280
lsb_release -d
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Mark Uhde on 2012-06-26
> **chili555 said:**
> The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

LOL, okay I definitely understated my computer knowledge. I know my way around a keyboard :) I'm just not too familiar with debugging driver issues on Linux. 

Anyways, I didn't post back with the PCI ID because the Ubuntu forums were, as commonly happens, not working when I tried to (that's a common issue I have it's why I don't post more - I can't stay logged in very long. Normally like an hour or so which makes using the forums a hassle, but sometimes only a few seconds, which makes it impossible to post).

After trying everything I could find elsewhere, I gave up and decided to use ndiswrapper. Even that didn't work because the Windows driver the eBay seller offers doesn't even have this device ID! You have to force Windows to install it. Another driver I found with bcmwl6.inf shows as present, but does not actually work. If anyone else runs across this card, only the bcmwl5.inf driver found in this thread works: [http://www.linuxquestions.org/questions/linux-hardware-18/broadcom-bcm43222-slackware-13-37-doesnt-yet-work-944073/page3.html](http://www.linuxquestions.org/questions/linux-hardware-18/broadcom-bcm43222-slackware-13-37-doesnt-yet-work-944073/page3.html)

Note, that the first time I tried to download the driver referenced in that thread, the link was broken, but going back later it worked.

This driver works with ndiswrapper, this version of bcmwl5.inf.

Even once working the card is flakey, sometimes requiring wifi to be switched off and back on to make a connection. But it does work.

I advise listening to the eBay seller and NOT buying this card for Linux, however. It's much harder to get working than other Broadcom cards, which are already notoriously bad for Linux.

---

### Post by chili555 on 2012-06-26
> Anyways, I didn't post back with the PCI ID Sorry I couldn't have been more helpful. I'm sure Ebay was a great help.

---

### Post by Mark Uhde on 2012-06-27
> **chili555 said:**
> Sorry I couldn't have been more helpful. I'm sure Ebay was a great help.

Ugh, no, I thought you'd be very helpful. Sorry if I was offensive. The forums themselves don't work properly for me sometimes I can't stay logged in long enough to even post. I couldn't post back. A post on the Slackware forums I found ended up having the answer, but the point was thanks for the offer to help, sorry I wasn't able to get back on here because the forums didn't work and thanks for trying to help. The eBay point was simply that I should've listened to the seller and NOT got the card for linux... but I didn't...

Best wishes!

---

