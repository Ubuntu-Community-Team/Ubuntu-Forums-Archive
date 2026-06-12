---
title: "Video Playback problem on Xubuntu 15.04 (not on Lubuntu 15.04)"
date: 2015-05-03
forum: Multimedia Software
---

### Post by malch2 on 2015-05-03
Setup:
Intel NUC5i5RYH with latest BIOS 0247
HDMI to Sony Bravia TV
Xubuntu 15.04

Problem:
When watching video/movies with Kodi or VLC I see horrible artifacts on fast motion.

I tried a different display, port, cable etc. but the issue was still present. It even shows up on a VNC link. I disabled hardware acceleration (decoding and rendering) tweaked video modes, and more, without any improvement.

After a couple of days messing around and performing a clean install the issue was still present. It was present even with a minimal installation and no adjustments.

So then I restored a system image from a month ago. This was based on Lubuntu 15.04 Beta1 (dist-upgraded as of 4/8/2015). This exhibited no video playback issues. I dist-upgraded the system to make it current as of today, rebooted, and all was still fine.

Next I performed a clean install of the Lubuntu 15.04 release. That works fine too.

Bottom Line:
There is some kind of video playback problem (at least with my hardware) under Xubuntu 15.04 that is not present on Lubuntu 15.04.

I plan to file a bug report but would like to try and narrow this down and see what additional information should be included. Any advice or suggestions greatly appreciated.

---

### Post by malch2 on 2015-05-03
Found a hint in the Kodi forums.

The solution was to disable Xfce Compositing in Window Manager Tweaks.

---

