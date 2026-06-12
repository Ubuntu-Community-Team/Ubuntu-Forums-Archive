---
title: "What's the best tool for my video editing project?"
date: 2011-02-17
forum: Multimedia Software
---

### Post by hreichgott on 2011-02-17
Hello all,

I'm making a video file out of approximately 20 clips I took with my camera.
I am using Ubuntu Studio, have no Windows or Mac machine.

I need to do the following:
- import the clips (currently .avi)
- cut out some excerpts from clips and arrange them in order
- remove audio from a couple of clips and replace it with new audio
- add a couple of title cards that appear on top of the video (like subtitles, but only a couple of them)
- render as a .mp4, flash or some other non-huge file format (some loss of quality is ok)

Kdenlive seems to have all the features I need. But every time I play my video in the preview window, the audio falls farther and farther behind the video. The discrepancy then occurs in the rendered file, not just the preview. This is a dance video so audio/video sync is very important. I checked the Kdenlive forums and it seems audio/video sync is a big problem.

Right now my workflow is to start in Pitivi, do all the editing except for the title cards, render as .avi, open the .avi in Kino (which involves waiting for it to open a non-.dv file--I tried rendering as .dv in Pitivi but it crashes), make the title cards, render as .mp4.

This is okay, but there are more file conversions than I'd like, and it would be nice to use a single program if possible. Anyone know of a better way?

thanks

---

### Post by Tom Collier on 2011-02-17
I've had great success with [OpenShot]("http://www.openshotvideo.com"). It's nonlinear with all the capabilities you outline in your msg. You can set up as many tracks, video or audio, as you need. OpenShot works with ffmpeg, so you'll need to make sure that's also installed, also. Do yourself a favor and do go through the ENTIRE tutorial before you start editing.

---

### Post by hreichgott on 2011-02-18
Hi Tom,
Thanks for the advice. Unfortunately Openshot seems to give me the same problem as Kdenlive: audio lags behind video, by a greater amount every time I preview the clip.
The title editor also appears buggy--the basic version of the editor shows only greyed-out buttons and a blank window once I click "create new title", and the advanced editor does not save its output properly back to the clip library.
I was able to create titles in Gimp and import them into Openshot, but the audio/video sync problem makes this editor unusable for my project.
Openshot is also a lot slower on my computer than Pitivi or Kino.
Let me know if you have suggestions on how to address these problems though.

---

### Post by no2498 on 2011-02-18
you may try traGtor for the sound
its a gui for ffmpeg for audio and video-conversion
i know its hard to find at times

---

### Post by Tom Collier on 2011-02-18
> **hreichgott said:**
> Hi Tom,
Thanks for the advice. Unfortunately Openshot seems to give me the same problem as Kdenlive: audio lags behind video, by a greater amount every time I preview the clip.
The title editor also appears buggy--the basic version of the editor shows only greyed-out buttons and a blank window once I click "create new title", and the advanced editor does not save its output properly back to the clip library.
I was able to create titles in Gimp and import them into Openshot, but the audio/video sync problem makes this editor unusable for my project.
Openshot is also a lot slower on my computer than Pitivi or Kino.
Let me know if you have suggestions on how to address these problems though.

I use OpenShot 1.3.0 on an eeePC 1000HD/Atom with 1 Gig of RAM and while it's not blazing fast, it's not unacceptably slow either. I run Ubuntu 9.10.

Like you, I quit Kdenlive because of the vid/aud lag problem. However, video and audio remain in sync when I use OpenShot with my current netbook and setup. (I did have to load the unabridged version of ffmpeg without the crimps that exist in the repositories version, but that was to get stuff needed to render to some other formats I needed.)

Some users suggest upgrading to Ubuntu versions 10.4 or 10.10 has resolved the sync problem. 

Go figure; as they say, YMMV...your mileage may vary.

---

### Post by LuridCinema on 2011-02-18
Make sure you have the frame rate settings correct  before adding the clips to the timeline..that will make synch issues

---

