---
title: "Going nuts trying to find just one decent video player for MPEG-2"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by Kensey on 2006-12-20
Does a good video player exist for MPEG-2 content?  Here are the players I've tried on my Dapper system and the issues with each:

**totem-xine:** can't correctly identify the length of the clip.  Shows clips as being 1/4 the length they actually are +/- a few seconds, e.g. a 31:00 clip shows up as 7:42 long.  Doesn't dynamically show the clip as you drag the slider, so it's hard to skim around and know where you are.  Despite these faults, it's currently my default player of choice. (I have libxine 1.1.1 installed.)

**totem-gstreamer:** Dragging the slider is basically useless as it appears to be trying and miserably failing to dynamically calculate the correct length of the clip (it gets in the right ballpark but can't decide exactly what the length actually is).  What the time index says when you release is likely to be minutes away from where it actually starts playing from.  Also starts up in the wrong aspect ratio (1:1 instead of the 4:3 that's encoded in the clip) but accepts the correct AR when I set it manually.  (I have gstreamer 0.8 and 0.10 installed.)

**VLC:** Wrong aspect ratio on startup, wrong clip length on the time bar.  Close but still not quite there.

**Gmplayer:** Seems to do its own thing.  Refuses to play the file in anything but a 1:1 aspect ratio, regardless of it being encoded in the file, specified on the command-line, or chosen manually after startup.  Shows the right clip length.

**Xine/Gxine/Kaffeine:** Wrong clip length.  (Also the default Xine GUI still makes me want to beat up small children just to take my mind off the horror, though it's a little better than it was 5 years ago.)

Is there a way to fix either the xine install or the gstreamer install so I can get all of the following?

[LIST]
[*] Correct clip length, so I can usefully skip forward/back by 10-, 15- or 30-second increments
[*] Proper aspect-ratio detection
[*] Dynamic display of the video as I drag back and forth -- I can really do without it, but hey, wouldn't it be nice?
[/LIST]

---

