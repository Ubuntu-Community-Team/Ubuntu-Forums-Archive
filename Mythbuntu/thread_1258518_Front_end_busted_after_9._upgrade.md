---
title: "Front end busted after 9. upgrade"
date: 2009-09-05
forum: Mythbuntu
---

### Post by nunrgguy on 2009-09-05
Something strange here - I could have sworn I upgraded my back-end (also with front end) a couple of weeks ago to 9.04 and everything went fine apart from display resolution being changed so I couldn't see anything on the monitor - fixed by VNCing in and changing the res to one that could be displayed.

Since then the only problem has been something different w.r.t. Vuze upgrade being in a constant loop - update, go through process, restart, get prompted to update again ad infinitum.

Last night I noticed synaptic saying a dist upgrade to 9. was available...w.t.f? I've already done it??? 
I let the system perform the upgrade, keeping my conf settings etc. came to it this morning with the resolution messed up again.
VNC'd in but this time the front end display was messed up - only 2 sides of a box are shown and nothing else. Changed the resolution so can now see all on monitor but front end is still screwy. 
Backend is working OK and can access from remote front ends OK.

Does this just sound like a corrupted skin (I'm about to try changing to a skin if I can get to settings again) or something else? Anyone else had this?

---

### Post by williammanda on 2009-09-06
If it were me....at this point...I would re-install. It seems you have spent more time trying to correct your issue than it would have taken to do the re-install. I decided to re-install after spending several days on an issue. It took me 3 hours to re-install ubuntu + mythbuntu. Now everything is fine.
Thanks

---

### Post by nunrgguy on 2009-09-06
That's really not a solution considering what else is on the box, plus I would have to make sure my 3 other front ends will work with it. Would need to back everything up, all XMLTV stuff which took an age to get working right, redo lvm across 3 drives re set up Samba (not a big deal I know) etc etc. It's not just a simple rebuild on a single box.
I've also found that every time I reboot the screen resolution changes to default as per another thread - have to VNC in and change every time.

This is about the 3rd distro upgrade I've done on this box and it falls over every time, there's absolutely nothing unusual about the machine itself as the hardware is very old and the thing round A-OK when all set up and working.

---

### Post by nunrgguy on 2009-09-06
Right - it turns out the front end problem is from bug 341898 with the work around 
XLIB_SKIP_ARGB_VISUALS="1" mythfrontend - running that from terminal launches the front end OK. Still have the resolution changing by itsel though.

---

### Post by nunrgguy on 2009-09-06
Right - it turns out the front end problem is from bug 341898 with the work around 
XLIB_SKIP_ARGB_VISUALS="1" mythfrontend - running that from terminal launches the front end OK. Still have the resolution changing by itself
though.

---

