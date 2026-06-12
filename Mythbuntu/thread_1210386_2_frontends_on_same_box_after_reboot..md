---
title: "2 frontends on same box after reboot."
date: 2009-07-11
forum: Mythbuntu
---

### Post by hellerite on 2009-07-11
Hi guys. Thanks for an excellent work. First, the hardware and software: Intel atom 330 board 2g ddr2 and PVR-250. For software I am using Mythbuntu 9.04 with xorg-edgers drivers for super video out.

The problem: When I reboot the system 2 frontends start at the same time. One of them displays the menu on the TV screen while the other one start Live TV on the background. You can hear the TV playing but only see the main menu on the screen. I have to VNC into the box and kill both instances then start a new instance. 

I welcome any Ideas. Please keep in mind that this was not happening with Mythbuntu's previous versions. I should also mention that this is a standalone (fronend and backend) system on the same box.

---

### Post by Verzweifler on 2009-07-11
I had a similar issue... That was caused by some session setting in the Desktop Main menue. IIRC I enabled some "automatic remember my current session on logout", afterwards the Frontend crashed... and after reboot I had "echoed sound" caused by two frontends slightly out of sync... 
I checked the list of autostarted programs and found two instances of the frontend sitting there, one from the original setup, and the second one "remembered on logout". 
I deleted that one and all was fine again.

---

