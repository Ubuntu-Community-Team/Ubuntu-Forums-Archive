---
title: "Audacity problem- windows recorded wav files sound OK, linux recordings scratchy"
date: 2008-04-26
forum: Multimedia Software
---

### Post by Anaphylaxis on 2008-04-26
Hey y'all.

Recording through my senheiser headset works fine in windows, but when I try to record stuff with audacity in ubuntu, the sound is very noisy. Windows recorded files play back normally in audacity, but my own recordings don't. I'd say they sound like I am screaming into the microphone, but I ain't no sound xpert. 

Any ideas?

EDIT:
Audacity has this caption on reducing noise in its documentation:
> If you hear crackles, pops, or distortion when the recording is loud, or if the waveform is clearly touching the top and bottom edges of the track, you probably have clipping. Try lowering the record level using Audacity's I/O Sliders, or lower the volume of the input source (like the tape player or microphone, whatever is producing the sound, if it has its own volume control)

That is exactly my situation, but I am unable to use the I/O sliders. (not supported by my soundcard?) I have tried the alsamixer, but it doesn't seem to help.

---

### Post by Anaphylaxis on 2008-04-26
Bump. Where do I change the input settings of my mic so that voice recording in Audacity will sound less noisy?

---

### Post by hurtstotalktoyou on 2008-04-28
Open terminal and run alsamixer.  You can adjust the mic input volume from there.

Also, you can lower the input volume in Audacity (the slide bar is in the upper right corner).

---

