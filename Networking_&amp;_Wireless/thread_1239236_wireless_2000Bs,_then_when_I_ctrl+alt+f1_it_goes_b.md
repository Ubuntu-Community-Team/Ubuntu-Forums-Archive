---
title: "wireless 2000B/s, then when I ctrl+alt+f1 it goes back up to 54Mbps"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by linuxtomac on 2009-08-13
I have an Atheros card, and I'm currently using the ar242x drivers in 8.10. I've also tried 8.04 and 9.04. In a fresh 8.04 and 8.10 the wireless works just fine (using the madwifi hal drivers), but I installed some upgrades that seem to suddenly make my wireless perform really slow. HOWEVER, if I ctrl+alt+f1 to the tty shell in 8.10 (what I currently have installed) my wireless will suddenly start working full speed again. I'll start a few updates, they'll go really slow/not download at all, then I'll ctrl+alt+f1 wait a couple minutes and then ctrl+alt+f7 and suddenly all the packages are almost done download at full 54Mbps speed. So I was hoping maybe someone knew what exactly happens when you ctrl+alt+f1 so I can track down the update that broke my wireless and fix the problem.

---

### Post by rayver on 2009-08-13
Try changing your screen resolution to something lower and report back what happens.

---

### Post by linuxtomac on 2009-08-13
Amazing! It works again. Must be a out of memory issue.

---

