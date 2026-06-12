---
title: "Help installing bcwml kernel source/Broadcom BCM4312 drivers"
date: 2013-02-11
forum: Networking &amp; Wireless
---

### Post by fubarator on 2013-02-11
OK, So I have another post asking about my Broadcom card and connectivity issues. I am almost done with that problem, but in order to fix that problem I need the drivers for my card, which I have been told can be found through the bcwml kernel source. This is my problem... I don't have any access to the internet because my internet connection is through a mobile hotspot with no ethernet connection, so I have no way of downloading the source file from Ubuntu. Is there ANY other way of installing these drivers? I do have an internet connection that is accessible through windows on this same computer and I have thumb drives of various sizes that I can install on. Can I not get these files somewhere where I can save them on the thumb drive, or save them somewhere on my computer that I can access through Ubuntu? I am not a complete Linux noob, but I'm also not an expert. I can follow instructions really well though ;). I am at my wits end here as this has been a three day process of trying to rid myself of Windows Vista. Please if anyone has any ideas or suggestions I am open to all. Thanks

---

### Post by chili555 on 2013-02-11
If you really have a 4312, then bcmwl-kernel-source is probably incorrect. Good thing you didn't succeed to install the wrong driver, eh?

Please open a terminal and run and post:```
lspci -nn | grep 0280
dmesg | grep b43
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by fubarator on 2013-02-11
Actually it was the correct drivers I just didnt have a way to download them. I went to a friends house that had a router and ran the file from the LiveUSB I had made to install Ubu from. I accessed the files through /media/username/LiveUSB Drive/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_i386.deb of course changing the "username" and "LiveUSB Drive" parts to the appropriate for your system file names. Anyway, I ran that file and then activated the driver through system settings, software sources, aditional folders, clicked the dot and hit apply changes. *poof* there was my internet like it should be. Thanks for eveyones help. The Ultimate solution in my kerfafel here was to connect via a wired connection through a friends router, download the correct drivers and everything worked as it should.

---

