---
title: "[SOLVED] Amarok cannot read from #2 CD drive"
date: 2008-07-02
forum: Multimedia Software
---

### Post by jimbob on 2008-07-02
How do I get Amarok to play from my 2nd CD drive?  It plays fine from the combo DVD/CD drive but not the second.

---

### Post by mc4man on 2008-07-02
If your using 8.04 then I believe you'll have to manually switch the default device in settings.  (settings -> configure amarok -> engine)
And like with kaffeine _your better off using /dev/scdx_ vs. /dev/cdrom or /dev/cdrom1,  /dev/dvd or /dev/dvd1, ect.
What should happen if you've chosen amarok to play audio cd's is when the cd is inserted amarok should be called (which it is), and the default device should be set for the device the cd is in (which doesn't happen). It stays at the device which has been orig. set in settings.
I never used kubuntu 7.10 but in Ubuntu 7.10 Amarok works perfectly with 2 drives. (default device is dynamically changed to the one the cd has been inserted in.)

---

### Post by jimbob on 2008-07-03
Thanks man.  After much fooling around I finally got it to work.  I would think that a mature product like Amarok would have code that automatically takes care of this by this time.  Even the lowly Rhythmbox in Gnome has no problem with either drive.

---

