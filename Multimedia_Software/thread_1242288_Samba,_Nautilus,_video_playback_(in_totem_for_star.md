---
title: "Samba, Nautilus, video playback (in totem for starters)"
date: 2009-08-17
forum: Multimedia Software
---

### Post by NaOH on 2009-08-17
I would like to offer a resolution to a situation I know many others are have found: Maybe you loaded up 9.04 (Gnome), connected to a Samba share, double-clicked a video and blushed as the video just played.  No custom smbfs scripts, no touching your fstab, just that logical behavior you'd expect out of any file manager.  Then, you might have found you longed to return to the comfort and stability of 8.04LTS (for me VMWare running like junk among a few other nagging bugs was enough), so back you went, and no more simple video playback from your samba shares.

Not a ground breaking solution, and I can't promise it will be the fix for you, but my solution was this:

Add Intrepid repositories, apt-get update, to synaptic, upgrade Nautilus, remove Intrepid repositories, restart to ensure stability.

Rinse and repeat, this time adding Jaunty repositories instead.

So you should now be sitting with Nautilus 2.26.2 (and a stock sources.list, meaning no jaunty or intrepid repos).  This alone wasn't enough to get that out-of-the-box network playback I was after.  The finishing touch was reinstalling Totem.  After that all worked as described:  No scripts, just navigation to samba share, credentials, launch video, voila!

Hope this works for you, and remember, messing around with Nautilus may wind up being a bigger headache than its worth, so try this at your own discretion.

---

