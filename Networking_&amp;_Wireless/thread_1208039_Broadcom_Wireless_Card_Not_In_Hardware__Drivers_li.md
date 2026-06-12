---
title: "Broadcom Wireless Card Not In Hardware  Drivers list"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by GreenBowlPacker_3 on 2009-07-08
I just install Ubuntu on a Gateway PC with a Broadcom 802.1g wireless card.  When I go to System -> Hardware Drivers and search to activate my card nothing shows up.  I have Ubuntu installed on my Dell (using it now)  and the driver for my wireless card was detected and works fine.

Am I missing something or doing something wrong?  Or is it a problem with Gateway?

---

### Post by t0mppa on 2009-07-08
The hardware drivers list is simply a way of activating secondary drivers, in case the default one doesn't work. If your driver works and is recognized, no need to enable anything there.

---

### Post by GreenBowlPacker_3 on 2009-07-08
It doesn't recognize it, and it doesn't work.

---

### Post by t0mppa on 2009-07-09
Ah sorry, mixed up the Dell with Gateway PC, my bad. Ok, if you can't see anything on the Hardware Drivers, you might have to do it by hand then.

Open up a terminal and run **lshw -C network** and post back with the output to see what type of a chipset you have and what's the current state of your card.

---

### Post by superprash2003 on 2009-07-09
check this link [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

