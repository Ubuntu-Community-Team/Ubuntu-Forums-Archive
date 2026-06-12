---
title: "No audio after AC3/DTS Passthrough"
date: 2012-01-07
forum: Multimedia Software
---

### Post by Programie on 2012-01-07
I recently switched to Kubuntu 11.10. Today I tried to play videos containing AC3 or DTS audio streams using XBMC. The passthrough device is set to iec958 (ALSA). The systems default audio output for music, event sounds, ... should also be iec958.
I can play music until I start to play a video in XBMC and the sound is passed through iec958. It seems that ALSA does not reuse the device if the playback in XBMC was stopped. Only applications witch force the use of iec958 were able to play audio.

Is there any way to resolve that problem?

---

### Post by pricinosus on 2012-01-08
Same here
Ubuntu 10.04 
Xbmc Dharma

If I set my audio hardware output to analog in ubuntu sound preferences...
[IMG]http://img46.imageshack.us/img46/1967/screenshotydx.png[/IMG]
and play firstly a 5.1 DTS (from XBMC) passed through iec958...
[IMG]http://img441.imageshack.us/img441/1337/screenshot1ges.png[/IMG]

 I have sound corectly decoded by receiver. Secondly if I play another 5.1 DTS file I have again sound corectly decoded by receiver.

The tricky part came now, If I play now an 5.1 AC3 file, my receiver see this as a 2.0 (stereo). And from now on, every type of audio (DTS, AC3, AAC, MP3, 2.0 5.1 6.1 7.1 maybe others) I try to play, results in the lack of sound.

Is this a Linux or XBMC issue?
and also
Is there any way to resolve that problem?

---

