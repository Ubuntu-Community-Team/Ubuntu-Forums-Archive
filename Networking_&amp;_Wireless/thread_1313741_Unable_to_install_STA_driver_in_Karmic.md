---
title: "Unable to install STA driver in Karmic"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by unmole on 2009-11-04
I have a Broadcom wireless card. I, along with a friend of mine, just installed karmic beside jaunty on our respective laptops. He tried installing  the STA driver in his laptop (which also has a Broadcom card), it took longer than usual but finally installed. But after restarting, the laptop shows A kernel panic. 
[code] [  1.942783] Kernel panic - not syncing: VFS Unable to mount root fs on unknown-block(0,0).  [\code]

So, I tried installing th B43 driver but the installation would not start i.e. the progress bar remains at 0% and finally crashes. Is there any way to fix this...?

---

### Post by unmole on 2009-11-04
Ok I solved it by bcmwl-kernel-source manually. 


BTW My friend re-installed karmic

---

