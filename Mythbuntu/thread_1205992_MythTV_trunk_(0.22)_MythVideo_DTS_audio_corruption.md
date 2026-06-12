---
title: "MythTV trunk (0.22) MythVideo DTS audio corruption"
date: 2009-07-06
forum: Mythbuntu
---

### Post by rtrevor on 2009-07-06
I'm getting some nasty audio corruption when playing video files (mkv or mp4) that use the "DTS audio" audio codec. It sounds like some very loud, harsh constant static / audio corruption, although I can just about make out the proper sound playing behind the static.

The files causing the problems play fine using both standard mplayer and Totem (gstreamer) from the Jaunty repository, and audio works fine for everything else - login sounds, other applications, and everything else in MythTV including live TV and all other files in MythVideo. There's nothing in the logs to suggest any problems when playing the files.

Does anyone have any ideas what the problem might be? Can't work out if it's something with my setup or if it's something to do with the internal video player / ffmpeg version in the latest build of MythTV... haven't managed to reproduce the problem outside of MythTV.


Exact version of MythTV installed is:
0.21.0+trunk20745-0ubuntu0+mythbuntu3

Sound card is onboard Intel HDA:
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)


Any ideas?

---

### Post by rtrevor on 2009-07-12
Ah... all working again now in 0.21.0+trunk20830.

---

