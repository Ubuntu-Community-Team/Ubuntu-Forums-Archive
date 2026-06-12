---
title: "PiTiVi Loses Audio/Video Sync"
date: 2010-05-23
forum: Multimedia Software
---

### Post by gerowen on 2010-05-23
I have tried to make a couple of custom videos with PiTiVi, fade-ins, fade-outs, title/end screens that I drew in GIMP myself, and within PiTiVi, the video plays perfectly.  Once rendered however, the video plays really fast so that the video is done way before the audio is.  I tried checking the framerate of the source video and changed the render settings to match that framerate, thinking that was the reason the video played fast, but that still didn't fix it.  Inside the PiTiVi preview box the video plays fine, it's only after rendering it that the video gets messed up, even using just the default settings.  Help?

---

### Post by SteveDee on 2010-07-10
I have a similar problem.

I can take an audio-visual clip, drag it onto the timeline, render to Vorbis, and the AV sync is preserved. But if I add a simple title screen (in the form of a .jpg file) without changing the video to audio track relationship (i.e. I fade down the clip based on the graphic, while bringing up the video from fully faded) the rendered video then lags a few seconds behind the audio.

What seems to work is to stretch the title screen into a clip the same length as the main video on the timeline. The title clip is then faded down and remains "off" for the rest of the video. A/V sync is then preserved.

The other thing I seemed to have to do is bring up the video track fully before the title screen clip was completely faded. Otherwise I tend to get a few blank frames.

I can't believe PiTiVi has been added to Ubuntu as a standard app, considering how flakey it is.

---

