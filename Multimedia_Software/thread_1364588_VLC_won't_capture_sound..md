---
title: "VLC won't capture sound."
date: 2009-12-26
forum: Multimedia Software
---

### Post by LordHawke on 2009-12-26
I just got a Logitech C250 Webcam for Christmas. I think I've just about got everything perfect. I've had fun messin' with VLC Player and streamin' and capturin' video and junk, but there's one problem: I've noticed that no matter what I do, VLC Player won't capture sound when playing or saving a stream.

The webcam has a built-in Mic. It works on everything else. I've used it with Sound Recorder and shot a test quick-vid on YouTube and the Mic has worked perfectly. I've been to Sound Preferences; the cam's Mic is enabled and turned up and responsive. However, in VLC, when playing or saving a "Capture Device Stream", there is never any sound.

This got me curious, so I tried streaming and saving my Desktop as a capture device and when there was sound, VLC failed to capture it in the stream. I'd really love to get VLC working. Please help me.

---

### Post by Leo Damascus on 2009-12-30
I have the same problem using the built-in webcam in my Dell Inspiron i1535.  It won't capture any sound if I'm using alsa, and the sound will be choppy if I'm using pulse.  If I try to edit the sound settings in any way, v4l2 breaks (it doesn't seem to care how I edit it, or even if I change it back after-words).  It's an annoying bug, and it seems only to affect VLC (Cheese, Audacity and gtk-recordmydesktop are all I've tested, but they all capture audio fine).
Anybody know what's going on here, and how we can get VLC to capture alsa and pulse audio?

---

### Post by Leo Damascus on 2010-01-12
New Development:  VLC apparently will capture audio for me so long as I capture the audio separate of the webcam footage.  In other words, I get audio playback if I run the command "vlc alsa://plughw:0,0" but not if I run "vlc v4l2:// :input-slave=alsa://plughw:0,0".

Curiouser and curiouser.

---

