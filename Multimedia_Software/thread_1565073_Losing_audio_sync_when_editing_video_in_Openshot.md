---
title: "Losing audio sync when editing video in Openshot"
date: 2010-08-31
forum: Multimedia Software
---

### Post by bakelitedoorbell on 2010-08-31
Did some forum searching but didn't find an answer so here goes:

My goal is to record video using a Canon Powershot camera, edit the AVI file on my Ubuntu 10.04 computer, then upload the rendered file to Youtube.

Problem is that when I cut the video, the audio is no longer in sync with the video, it's off by about 1-2 seconds.  This happens with both Openshot and Pitivi, so I suspect that it's caused by a bug with the codec.  (files are AVI with MJPEG codec).  After searching launchpad, this is apparently a "known issue".  That's great but for now I need a workaround.

I do have an old G4 Powerbook with iMovie HD v6 on it that I can use, but I'd prefer not to because:

1. the PowerPC Mac is much slower than my new dual core laptop
2. iMovie compresses my videos too much so the rendered file is lower quality
3. I simply prefer Openshot to iMovie

Any ideas?  I was thinking of preprocessing my AVI files by converting them to another format with a non-buggy codec on linux.  I downloaded ffmpeg, but not sure how to use it and what format to use.  Would mpeg2 be a safe one to use?

---

### Post by bakelitedoorbell on 2010-09-01
The workaround I found was to use WinFF to convert the camera's files before importing them into Openshot.  I set it to convert to "Raw DV for NTSC fullscreen".  This generated files much bigger than the source AVI files, but it preserves the image quality and lets me edit them without messing up the audio.  Then I export them as mpeg4 for youtube.

Hope this helps anyone else with this issue.

---

### Post by bakelitedoorbell on 2011-09-04
Currently using Ubuntu 10.10, and the latest version of Openshot, and I still have this problem of audio de-syncing after making a cut in the editor.  I have a 2.1 Gigabyte AVI source file - if I have to convert to DV it will be HUGE.  

Has anyone heard about any progress with this bug or a workaround?

---

### Post by BicyclerBoy on 2011-09-05
Can you change the container used by the camera ?

AFAIK The avi container is totally inadequate for modern video compression. It does not allow out-off-order packets, variable rate, B frames, proper timing information. AVI dates from the era when video & audio packets were direct one for one constant rate.
It has been hacked to work by using packed B frames etc..

MJPEG is an format that uses all I or key frames (slideshow of JPEGs very primitive), so you could find that just using a different container will fix the AV problem.
Use WInFF to change the container (re-mux) of the original avi file.

The DV file format will be huge but will edit very fast & least loss.
I would think that MJPEG would cut/edit very fast as well.

---

### Post by bakelitedoorbell on 2011-09-09
> **BicyclerBoy said:**
> Can you change the container used by the camera ?



No - I looked through the menus and the only thing I can change on video is NTSC or PAL.  I'm going to look for a newer camera, so that may solve my problem.

---

### Post by BicyclerBoy on 2011-09-09
Have you tried 
AviDemux (in the *buntu repos)
That project has a particular historic interest in avi ..
You may be able to re-index demux-remux into another container type.

Expect more trouble:
Modern cameras/camcorders would be using m2ts (based on mpeg2-ts) or AVCHD.
AVCHD is a varying non-standard standard because consumer electronics manufacturers were responsible..

---

