---
title: "Totem won't play unencrypted/region-free DVD's in 9.10"
date: 2009-11-04
forum: Multimedia Software
---

### Post by MarkiusLanzius on 2009-11-04
Totem (gstreamer and xine) just hangs when trying to play unencrypted region-free DVDs in 9.10 (Karmic) with a fresh install.

VLC is ok with unencrypted discs, disc is mounted ok, commercial discs are ok in both VLC and Totem.

If opened in Nautilus the files are visible but no thumbnails are created. If the VOBs are double-clicked it plays very slowly whilst thrashing the DVD drive. if you then 'Force Quit' to stop Totem, whenever you try to play an unecrypted disc afterwards you get a non-descriptive permissions error. In VLC you get this:

 Your input can't be opened:
 VLC is unable to open the MRL 'dvd:///dev/sr0'.
 Check the log for details.

Can't find the log file (looked EVERYWHERE)

Commercial discs in both are still ok.

Tried a new user, same thing.

Need to restart without disc in the drive to restore unencrypted disc playback in VLC. Leave disc in during restart and VLC still errors as above.

Never had this before (since 7.10)

(Also, 'disc tray' button only works if the tray is empty, or if you unmount first. Only in Karmic, fine in all since 7.10 [Toshiba U200])

Anyone else getting this problem?

Anyone know a fix? Workaround would do.

I like Totem, but defaulting to VLC for now.

---

