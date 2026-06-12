---
title: "atheros wifi woes, please help 64bit RT kernel"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by svtfmook on 2009-12-18
out of the box, kamic recognized my AR9285 wireless card.  which was good.  sometimes, i can open wifi radar and see a list of access points.  however, when i try to connect to any of them, it just sits at connecting.  if i cancel it, all of a sudden it's like my card is gone.  no more access points listed in wifi radar, and in network manager it disables wifi all together.

things i've tried was installing the backports, but they are not available for the RT kernel.

i've tried downloading and compiling the backports manually, but didn't work.

i was planning on booting the the generic kernel and trying the backports to see if that works.  and/or try ndiswrapper under the RT kernel.

this is my first time trying wifi with ubuntu, so i'm completely lost.  when i go into network manager, in order to enable wifi, i have to manually enter an SSID.  but i would rather use wifi radar or something similar so i can view and connect quickly to various access points.

please help if anyone knows of a solution to this.

---

### Post by Bucky Ball on 2009-12-20
Avoid ndiswrapper at all costs. Madwifi is for the Atheros anyhow so you might want to try that.

Have you looked in System->Administration->Hardware Drivers to see if there is a driver there and it is disabled? Have you plugged an ethernet cable in and gotten your updates? If not, do it now. There is a good chance that will pick up your card, inform there are drivers available and ask if you'd like to install.

---

