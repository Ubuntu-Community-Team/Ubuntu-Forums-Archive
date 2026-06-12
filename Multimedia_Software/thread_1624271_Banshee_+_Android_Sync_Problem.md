---
title: "Banshee + Android Sync Problem"
date: 2010-11-17
forum: Multimedia Software
---

### Post by scotty32 on 2010-11-17
I used to be able to sync my music with HTC Hero and Banshee, but when I upgraded to 2.1 quite a while back banshee seems to crash.

I now have a Nexus One (Android 2.2) and that does the same. (no longer have the Hero)

They both seem to crash Banshee when it gets to syncing the playlists (every time), music syncs fine.


Does anyone else on 2.1 or 2.2 have this problem or is it just me?

(been doing searches every now and then since the Hero update but cant find anything)

---

### Post by adrian.ratnapala on 2011-01-31
I've had similar, but different, problems with my Motorola Milestone (Droid).  Syncinc with Rhythmbox might have worked onces, but now Banshee, Rhythmbox and mtp-tools all fail, giving different errors.  And yes, sometimes Banshee does crash.

The "solution" is to just mount the SD card on your phone (on the phone's USB management just select "SD card access" ubuntu should do the rest).  Then shove our songs straight into the "music/" directory.   **Then properly unmount the SD card**.   (It seems that just switching USB modes from the phone is as bad as unplugging the cable.)

The phone is smart enough to find the files, extract the album + artiest names.  It even works with Ogg Vorbis.

---

