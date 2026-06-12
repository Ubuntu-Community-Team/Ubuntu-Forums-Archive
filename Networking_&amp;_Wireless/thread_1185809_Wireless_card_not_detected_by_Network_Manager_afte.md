---
title: "Wireless card not detected by Network Manager after kernel update"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by neogarv on 2009-06-12
I own a Dynex Enhanced G Wireless Card. I had to use the Broadcom drivers (which I had to install by carrying these files over in a flash drive: [http://www.omattos.com/broadcom/](http://www.omattos.com/broadcom/)) to activate my wireless.

After activation of my Internet, I updated my software, which included a newer Linux kernel. Previous to the update, I had 2.6.28-11-generic. After the update, I got 2.6.28-13-generic (I know, not a very large update). But, after the kernel was updated, I was not able to use my wireless card. Network Manager does not detect my card for some reason, but lspci still shows it. If I boot into the older kernel, my wireless card still works.

Is there any way that I can use Network Manager and have it detect my wireless card in the newer kernel? I'd prefer not rolling back to the older kernel. Thanks!

---

### Post by neogarv on 2009-06-12
I need help quickly. It'd be really nice if someone responded. Soon. :D

---

### Post by neogarv on 2009-06-13
Bump.

---

### Post by neogarv on 2009-06-23
I finally figured this out! I used the guide here: [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560). Switching my drivers over to ndiswrapper solved all my problems.

---

