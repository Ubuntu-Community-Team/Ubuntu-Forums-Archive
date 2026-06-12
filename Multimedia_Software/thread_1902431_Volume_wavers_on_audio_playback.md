---
title: "Volume wavers on audio playback"
date: 2011-12-30
forum: Multimedia Software
---

### Post by Zachs Kappler on 2011-12-30
I have begun to notice that whenever I play audio files of any file format or with any media player that the audio will dip and rise in volume at a regular intervals. I'm not sure if I inadvertently installed something that is causing this but it only seems to happen with audio files and nothing else. What can I do to fix it or narrow down the possible suspects?

---

### Post by inobe on 2011-12-30
sounds like your audio files have DRM Digital Restrictive/ rights Management.

if it's not that, it may mean you have surround sound set on your receiver, but you are only using two speakers.

if that's the case, it needs to be set to stereo.

---

### Post by Zachs Kappler on 2011-12-30
I know it's not DRM because my stuff is in FLAC and OGG with some MP3 files from UbuntuOne, so I can rule that one out. I'll poke at the sound settings because I'm using a 5.1 speaker set and it should be set accordingly.

Edit: I have everything set to 5.1 output with stereo input for my main audio device. I also set it on some media players such as Totem that had a option for it.

---

### Post by lidex on 2011-12-31
It does the same in Totem and VLC? Audio in video files is not affected?

---

### Post by Zachs Kappler on 2011-12-31
I might have narrowed it down. I went to OCRemix to grab a random song to experiment on and the only time the volume started wavering was after passing it through QtGain like I have for the rest of my music collection. It must be related to how ReplayGain ID3 tags are interpeted.

---

### Post by Zachs Kappler on 2012-02-03
Okay, upon further testing when I had the time, it seems it's doing this wavering for everything. I tried setting everything back to 2.0 or 2.1 analog duplex but it still occurs.

EDIT: I have the Logitech x-540 speaker set if that helps eleminate anything hardware wise because it only has two buttons, power and matrix. I don't use the matrix button though.

---

