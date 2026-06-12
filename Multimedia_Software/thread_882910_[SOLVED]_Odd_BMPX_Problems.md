---
title: "[SOLVED] Odd BMPX Problems"
date: 2008-08-07
forum: Multimedia Software
---

### Post by Precipitous on 2008-08-07
I use the BMPX player (build 0.40.13) to listen to Last.fm and am experiencing some odd problems:

1.  In the program preferences, if the audio source is set to Automatic, the sound quality is bad. I get random splashes of static/distortion every few seconds.

2. If the audio source is set to Pulse Audio the sound quality is good, but if I go back to the preferences window, the source changes to Jack (although sound is still good)

3. No matter what the audio source is set to, the program completely closes (even from the tray) after listening for about 30 minutes or so.

The BMPX player is awsome when it is working. I just wish I could get mine stable. Does anyone have suggestions?

---

### Post by Precipitous on 2008-08-19
All of these issues were solved by following the instructions posted at [PulseAudio Fixes & System-Wide Equalizer Support (Hardy Heron)]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472"), then setting the Audio Source for BMPX to Automatic.

---

