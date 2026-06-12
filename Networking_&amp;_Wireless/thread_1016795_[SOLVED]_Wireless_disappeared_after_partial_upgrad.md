---
title: "[SOLVED] Wireless disappeared after partial upgrade"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by maltman on 2008-12-20
I had already upgraded to 64bit Intrepid a couple weeks ago, and all went fine.
There since have been a few regular upgrades which I've also installed and went fine.
Up until today. It mentioned that there was a partial upgrade. I continued and there didn't seem to be any issues with it, until after I rebooted, and then my wireless disappeared.
I have a PCI Atheros 802.11g card which always worked fine right out of the box before. But now it's not even appearing to detect that the card exists.
What happened? How can I troubleshoot this and get my network working again.
(I'm typing this on my Windows PC since I can't even connect to the Internet with my Ubuntu box) :(

---

### Post by RobotJox on 2008-12-20
same here

---

### Post by wwusnobrdr on 2008-12-20
This happened to me on the 32 bit version as well and here is what I found out.

In my messages log file I saw that the ath5k module was no longer loading it was the ath9k.  I downloaded the compat wireless package from here [http://wireless.kernel.org/en/users/Download#Wheretodownload](http://wireless.kernel.org/en/users/Download#Wheretodownload) .  The instructions are on the page.  Once you make, make install, make unload, and make load...reboot.  Then the wireless should work.  Let me know if you have any questions.

EDIT:  The backports modules which contains the ath5k driver was not released until earlier today.  So if you do not want to go the manual installation way, this package should get the wireless working as well.

---

### Post by infiniband on 2008-12-20
Looks like they just pushed out the fix, at least my wireless appeared again after applying it.  Do an System -> Administration -> Update Manager and apply the driver update.

---

### Post by maltman on 2008-12-20
> **wwusnobrdr said:**
> This happened to me on the 32 bit version as well and here is what I found out.

In my messages log file I saw that the ath5k module was no longer loading it was the ath9k.  I downloaded the compat wireless package from here [http://wireless.kernel.org/en/users/Download#Wheretodownload](http://wireless.kernel.org/en/users/Download#Wheretodownload) .  The instructions are on the page.  Once you make, make install, make unload, and make load...reboot.  Then the wireless should work.  Let me know if you have any questions.

Absolutely perfect. Worked like a charm and now I'm back up and running.
Thank you so much.

---

### Post by maltman on 2008-12-20
> **infiniband said:**
> Looks like they just pushed out the fix, at least my wireless appeared again after applying it.  Do an System -> Administration -> Update Manager and apply the driver update.

How can I do an update if I don't have Internet connectivity?
The fix suggested by wwusnobrdr worked great.

---

### Post by infiniband on 2008-12-20
Plug into a wired port? The other solution mentioned a download from the Internet, I don't see now that does not require Internet connectivity.

In any case, I would consider that a temporary solution, since it is not under package management.

Good luck.

---

### Post by maddielu on 2008-12-21
thank you!!!! my wireless works again!

---

