---
title: "Flash sound gone."
date: 2009-02-12
forum: Multimedia Software
---

### Post by ajgreeny on 2009-02-12
Ubuntu 8.04, fully updated.
Sempron 2400+
1GB ram
Sound preferences set on pulse, and had no problems with that.
ATI 9200SE graphics card - great ATI card for things I need with open source driver.

Suddenly yesterday I have lost all sound in any flash movies.  I have not changed my flash setup since I installed Adobe flash plugin 10.0.15.3 a long time ago, and until yesterday all was working brilliantly, but suddenly it's gone, absolute silence in flash, though all other sound apps (rhythmbox, mplayer, totem) are fine.

Yesterday's updates included an update of Firefox and xulrunner, and I winder if this has had some bearing on the problem.  I have made no changes to anything else related to sound so am baffled.

Anybody got any clues about what may be going on here.  I don't want to make too many changes without asking if anyone else has seen a similar problem, as it is possible I could make things worse.

---

### Post by johnjohn2 on 2009-02-12
A quick fix would mean removing Flash.

Sosearch for flash in synaptic and completely remove flash plugin non free.

Then i like to reboot and reinstall it via synaptic.

After that the problems should be history.


Regards John

---

### Post by ajgreeny on 2009-02-12
I have already just done more or less that.  I uninstalled the **adobe-flashplugin** v10, then installed the **flashplugin-nonfree** and **libflashsupport** again.  I then uninstalled the **flashplugin-nonfree**, and leaving **libfalshsupport** installed I reinstalled the **adobe-flashplugin v10**, and everything seems to be working again.  I thought the libflashsupport was only needed for flash 9 with pulse audio running, so I am baffled.  I didn't even have libflashsupport previously, and everything worked OK, so it all seems very strange.

My question remains, however, what on earth happened to cause this palaver to be needed.  I didn't do anything as far as I'm aware, and it caused me quite a lot of grief.

---

### Post by redroad55 on 2009-02-12
This has happened to me in weekly updates .. I still loathe adobe .. It seems we linux users are a secondary thought over there but at least we are secondary previously we were not even that but I see that changing as we gain more of the market share .. Its a kin to the browser wars .. I'm glad you got it sorted .. Best to you

---

### Post by ajgreeny on 2009-02-12
Thanks folks!!

---

### Post by johnjohn2 on 2009-02-12
good news

Regards John

---

