---
title: "acidrip/handbrake"
date: 2020-07-11
forum: Multimedia Software
---

### Post by jmax123 on 2020-07-11
Bought a new dvd - "Death on the Nile" and found that updating ubuntu from19.04 to 20.04, Handbrake stubbornly refused to work. So tried AcidRip. 
First go, could not get rid of the sub-titles. Annoying but found that if Sub-File was clicked no worries - no more sub-titles. Then found AcidRip would not
record the whole DVD. More annoying but found that I should have changed the File Size from its default "700" to the File Size of the main VOB file of
my new ancient DVD [ Peter Ustinov as Poirot is best ] all worked well. Bit of a Homer Simpson moment I know to change the File Size to the actual FileSize
shown on the disk but there you are. 

This post is just info for those who find that Handbrake won't work on 20.04 and want to try AcidRip.

---

### Post by TheFu on 2020-07-12
> Handbrake won't work on 20.04

That's a blanket statement. Is it really true?

I can believe that ripping DVDs isn't currently working using XYZ install of Handbrake (.deb or snap) on your 20.04 system and that you've installed libdvdcss2 (did you?).  If the handbrake installed is a snap, then access to locations and mounts outside HOME being blocked is to be expected. That's part of how snaps work.  If using the software center for the install, it is quite possible the snap was chosen.

I'm also confused by the use of "File Size" with "700" above.  Perhaps you meant File Permissions?

---

