---
title: "No option for &quot;enable wireless&quot;. Help please"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by JohneG on 2010-02-27
My wireless broadband connection was working fine until this morning. I am running UNR 9.04 on an acer aspire one. For some reason i have no option to enable wireless and i don't know what i have done. When i right click all that shows up is "enable networking" but there is no optiont to "enable wireless" anymore. I tried flicking the switch on my netbook to see if that had caused the problem but after doing it and rebooting its still the same. Anyone know what i could have done wrong?

---

### Post by gba3 on 2010-12-21
I have the same issue. Yesterday it was all fine, but this morning - no wireless and no choice to "enable wireless". I had some problems before I solved with "rfkill" but now it doesn't respond to the command at all. Probably for me the reason is "sudo lshw" doesn't list my wireless card...

Yes! Exactly the problem. The next time I switched on my laptop everything was fine. So that may be motherboard showing the last signs of life or something like that.

---

