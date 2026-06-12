---
title: "Occasional lockup opening jpeg photos"
date: 2014-01-01
forum: Multimedia Software
---

### Post by michael-piziak on 2014-01-01
I have a card reader and sd card from my camera.  I always open the images straight from the card reader.  On occassion, the system will lock up when opening the first jpg image.
Anyone else experience this with jpg images?

Alt+sysRQ and typing REISUB  gets me out of the lock up.

---

### Post by tgalati4 on 2014-01-01
Well, it forces a reboot, not exactly getting out of the lockup.  Open a terminal:

```
dmesg | tail -50
```  

Look for read errors.  My guess is that your card is failing causing long IOWaits.  Run *top* in another terminal and look at IO%  If it is non-zero, then your system is waiting for reads--probably from a failing SD card.

---

