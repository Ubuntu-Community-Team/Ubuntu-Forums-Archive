---
title: "Wireless connection is weak"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by WillDuquette on 2009-11-01
Howdy!

I'm using UNR 9.10 on an Asus EEE PC 1005 HA.  In general everything's working fine, except that the wireless network connection's signal strength is a lot weaker than it should be.  Even sitting six feet from the Airport Base Station I'm getting only about 68% signal strength; I do quite a lot better when booted into Windows XP.

I'm a Linux networking newbie--any suggestions as to where I should start looking to resolve this?

---

### Post by varanasi on 2009-11-01
Let me add ... in addition to appearing weak in the net manager applet, after a suspend, the wireless is intermittent.  It frequently disconnects itself.  It will reconnect but only with manual intervention.

---

### Post by WillDuquette on 2009-11-01
Pursuant to the above: I've installed ndiswrapper, and set it up to use the same driver that
Win XP is using, the Atheros AR9285 driver, version 7.7.0.259, which is what the Asus
download site has for the 1005HA. 

According to "lshw -C Network", it's using this driver in place of the ath9x driver it was using previously.  However, it doesn't seem to have made a lot of difference.

 I've also seen a (later?) version of the same driver (7.7.0.329) that also targets Win XP; should I be using that?

Or is ath9x adequate on this box?

---

### Post by WillDuquette on 2009-11-01
I tried removing the Windows driver in ndiswrapper, to restore the ath9x driver, and was told that the wireless interface is UNCLAIMED.  How can I put ath9x back?

---

### Post by bkratz on 2009-11-01
> **WillDuquette said:**
> Pursuant to the above: I've installed ndiswrapper, and set it up to use the same driver that
Win XP is using, the Atheros AR9285 driver, version 7.7.0.259, which is what the Asus
download site has for the 1005HA. 

According to "lshw -C Network", it's using this driver in place of the ath9x driver it was using previously.  However, it doesn't seem to have made a lot of difference.

 I've also seen a (later?) version of the same driver (7.7.0.329) that also targets Win XP; should I be using that?

Or is ath9x adequate on this box?

You might want to check out this thread, especially post 2

[http://ubuntuforums.org/showthread.php?t=1286503&highlight=AR9285](http://ubuntuforums.org/showthread.php?t=1286503&highlight=AR9285)

---

### Post by WillDuquette on 2009-11-01
I have found that I can get ath9k (not ath9x, as I mistakenly said above) back in place by
doing

   sudo modprobe -a ath9k

As soon as I do this, the wireless if is no longer UNCLAIMED, and in fact it connects to the wireless lan almost immediately.  But when I reboot, it's gone again.  I've repeated this about five times in a row...each time, it's gone and I have to add it back in.  How can I make it stick?

(As for the reference to the other thread--those instructions were for 9.04.  Do they still apply for 9.10?)

---

