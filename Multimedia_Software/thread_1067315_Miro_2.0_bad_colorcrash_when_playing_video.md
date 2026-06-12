---
title: "Miro 2.0 bad color/crash when playing video"
date: 2009-02-11
forum: Multimedia Software
---

### Post by lordbah on 2009-02-11
Hadn't had problems with the previous version of Miro until today. Playing a video from Loaded HD and it was all blue and green. A search found that someone else had the problem months ago but no one had any answers. I knew there was Miro 2.0 pending so I went to the web site and looks like it's released! So I updated. 

The interface looks very nice. Tried to play that Loaded HD video and it showed one frame but wouldn't show anything else. Tried to play a video from Wired Gadget Lab and Miro crashed. Can't see anything fatal in the miro-log file. I then switched the video playback from gstreamer to xine. The Wired Gadget Lab video still crashes Miro. The Loaded HD now plays but is still all blue/green.

This is all on Ubuntu 8.04.2.

Any suggestions? Uninstalling every video-related program and then reinstalling is a last resort.

---

### Post by lordbah on 2009-02-12
I don't think the blue video was a Miro issue. It was happening in external players running known good video files. I found a bug on it [here]("https://bugs.launchpad.net/debian/+source/linux-restricted-modules-2.6.24/+bug/184440"). Solution was either go into video players and make sure they aren't using "xv" for video output, or run "xvattr -a XV_HUE -v 0".

---

