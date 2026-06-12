---
title: "corrupt recordings after upgrading to weekly 0.21-fixes"
date: 2009-01-31
forum: Mythbuntu
---

### Post by nryan on 2009-01-31
Hello,

I recently upgraded my MythTV installation from the version of 0.21-fixes which comes with Ubuntu, to the latest and greatest weekly build of 0.21-fixes from [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) 

But now I sometimes have a corrupt picture, it looks like some interlaced ghosting at half a frame offset, see the screen capture here:
[http://img220.imageshack.us/img220/9598/mythtvbadpictureeo1.jpg]("http://img220.imageshack.us/img220/9598/mythtvbadpictureeo1.jpg")

It comes and goes, and seems to depend on what is being displayed at the time. Text or solid color areas seem to make it worse, other times it will be fine. I've tried changing the deinterlacing options with no success. Old recordings play back fine, only recordings made since the upgrade have the problem. Does anyone recognize this and have a solution?

Thanks,
Niall.

---

### Post by nryan on 2009-02-01
This is now resolved: the resolution in the recording profile needed to be changed to 768x576 since I have a PVR-150 capture card. After the upgrade it had been reset to 480x576 for some reason.

Thanks,
Niall.

---

