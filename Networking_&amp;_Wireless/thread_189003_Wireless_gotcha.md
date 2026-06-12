---
title: "Wireless gotcha"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by joncheyne on 2006-06-04
HI all

Installing Ubuntu (and then Xubuntu) on an old laptop with a belkin 54g card.

Not working blah blah, read a million posts, try all manner of commands etc etc.

You've been there ...

Anyhoo, finally, tried another .inf file with the old ndiswrapper thing - aha.

Still no joy. Then I though, why not bring up the router interface? - Bingo!

OMG - so, it was all a lack of DNS? Sure - checked my main box which has been unchanged config wise for years - and sure enough I had had to manually enter the router as the DNS

Did the same thing on the laptop and Bob's yer uncle.

Now - I had followed the latest "no-ndiswrapper" threads with apparently no joy but now I am wondering whethr, all along, it was a DNS gotcha.

heh, well I am just gonna enjoy some wireless connectivity before I start experimenting again :) 

anyhoo, just for those of you are following the instructions and are hitting the same old brick walls - check that you have a DNS server listed!

Jon

ps - Question - is running ndiswrapper worse than the autodetected way?

---

