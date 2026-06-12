---
title: "Audacity not recording"
date: 2013-03-27
forum: Multimedia Software
---

### Post by kernalkorn on 2013-03-27
v12.10 Gbyte FM1 AMD A4 APU

My sound system analog out  works fine.  I can play CDs with banshee, MP3s with VLC  and FF flash video no problem. Stereo output goes to AV Rec for room speakers.  HDMI surr sound also works.  Audacity cannot "hear" internet audio.  Sound settings are analog output built-in audio. Audacity settings are: ALSA, PULSE, DEFAULT, 2(stereo). I noticed almost al the "audacity not recording" posts are pre 2010, so the linux sound system must have been greatly simplified and improved in the last couple of years.  However I have an odd APU chipset combination. All I had to do to get Audacity to record from WinXP was set it to StereoMix. Any obvious hints?

---

### Post by ajgreeny on 2013-03-27
Run ```
alsamixer
``` in terminal and check that the levels of inputs from your mic(s) are not set too low or muted.
Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
In capture page use spacebar to enable the different input devices (mic, line, CD, video).
Esc will save yur settings and exit.

You should also open pulseaudio volume control from the menu (or dash if using unity) to check the input tab device and level, with audacity running and recording.

---

