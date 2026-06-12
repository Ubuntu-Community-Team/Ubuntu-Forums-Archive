---
title: "&quot;radio off&quot;... despite all efforts"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by kripkenstein on 2006-06-09
Well, I just installed Ubuntu for a friend, on his laptop, a fairly-new Fujitsu Amilo Pro V2040, which is Centrino. Everything works fine, except for wireless, which I personally have little experience with. The hardware is identified ok, "Intel Corporation PRO/Wireless 2200BG", and the interface exists correctly, the driver is set up fine. The issue is that it says "radio off" in iwconfig... so it can't connect to anything (it fails at the DHCP stage, because the radio simply isn't up).

Hours of scanning forums, HOWTOs (on the wiki), etc., and still no idea how to turn the radio on... People just say "you need to turn the radio on, it's different for each laptop model"... we tried the keys that did it in Windows, no luck.

Any idea how to get the radio to turn on, or how I can continue to investigate this problem?

Thanks.

---

### Post by wofritz on 2006-06-09
Hi kripkenstein,

you may want to give "acerhk" a try. It's a driver to make special functions work on a number of laptops (not only acers as the name could imply). An Amilo Pro V2000 is mentioned as supported. The homepage of the driver is at

[http://www2.informatik.hu-berlin.de/~tauber/acerhk/](http://www2.informatik.hu-berlin.de/~tauber/acerhk/)

It made the radio switch and the special keys work on my Acer 292LMi. It must be compiled from source though.

Regards,

Wolfgang

---

### Post by kripkenstein on 2006-06-09
That looks interesting, wofritz, thanks. I'll check it out now.

---

