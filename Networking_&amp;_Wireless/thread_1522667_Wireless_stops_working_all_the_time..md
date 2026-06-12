---
title: "Wireless stops working all the time."
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by kakarotman on 2010-07-02
So i am running ubuntu 10.04 and everything worked great untill i updated. Now pretty consistently 20 minutes to 2 hours after i turn my computer on my wireless will stop working and i have to reboot for it to work again. When it stops working it says it is searching for an access point and cant find any. As if my wireless doesnt exist. This only happens however when i am on it. If i start downloading something and lock it when i go to bed at night, when i wake up it is still working. Can some one please help? It drives me nuts to have to restart my computer ever half hour. Thanks!

---

### Post by Iowan on 2010-07-02
I presume you've checked your BIOS to see if any power-saving scheme shuts off the wireless?

---

### Post by kakarotman on 2010-07-02
I did not know that the bios handled any sort of power saving even if that was so i always have my computer plugged in so i cant see how that could be relevant.

---

### Post by kakarotman on 2010-07-03
bump

---

### Post by kakarotman on 2010-07-04
bump again

---

### Post by owise1 on 2010-07-04
Mate not sure what is going on but you should not have to restart your PC to get the wireless running again.  Just restart the network service

from the command prompt - sudo /etc/init.d/network restart

that should shut down the interface and bring them up again.

also just a thought - did you have connect automatically set for your conenction?

Cheers

---

### Post by Roasted on 2010-07-04
What wireless card are you using?

---

