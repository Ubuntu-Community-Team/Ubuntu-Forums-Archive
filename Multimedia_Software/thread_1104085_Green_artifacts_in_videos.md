---
title: "Green artifacts in videos"
date: 2009-03-23
forum: Multimedia Software
---

### Post by beachdaze on 2009-03-23
When watching any videos (usually avi in divx or xvid, but also mpg) I get green artifacts running all through the movie.  Looks similar to the old "the matrix" screensaver.  I have tried every version of the Nvidia driver from the open NV to 180.11, no changes.  Everything else looks great! I'm not sure if it's a driver or codec issue.  Any advice please?

SYSTEM:
Mythbuntu 8.10 AMD64
Video:  Nvidia 6600GT (256MB)
Asus 8AN-SLI Deluxe Motherboard
AMD 64x2 3800+ CPU
4GB RAM.

---

### Post by DeusEx on 2009-03-26
hello, you might want to look into your codecs, especially Xvid!

---

### Post by 3rdalbum on 2009-03-26
To rule out the video card driver (older Nvidia drivers are known to have problems with video), try changing your video player's "video output module" to X11. You can usually do this in the player's preferences, or otherwise in Gconf-editor if it's a Gnome program.

Otherwise, it could be a data rate problem (too high a bitrate to stream across a network or from your media).

---

