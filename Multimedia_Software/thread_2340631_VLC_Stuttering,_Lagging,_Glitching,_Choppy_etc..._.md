---
title: "VLC: Stuttering, Lagging, Glitching, Choppy etc... yadda... so on &amp; so forth..."
date: 2016-10-20
forum: Multimedia Software
---

### Post by neu5eeCh on 2016-10-20
I've Googled this and the internet is awash with out of date answers.

In previous incarnations VLC worked great playing DVDs and now, and on the same laptop with 16.04, they're unwatchable. I  don't blame Ubuntu. Sound is fine, but the video is choppy. Hardware is **not** the problem. SMPlayer plays the same DVDs like butter but navigating DVDs with SMPlayer is a PITA.

Have any of you recently fixed similar symptoms in your VLC player?

---

### Post by mc4man on 2016-10-20
vlc now sets hardware decoding and video output to "Automatic". In many cases it makes the wrong choice, particularly for video output.
So open vlc > Tools > Preferences
Under the Video tab > Output choose one from the dropdown depending on your hardware. OpenGl GLX is a good first choice, if still issues try XVideo

Under the Input/Codes tab > Hardware accel.. you could choose Disable or if using a recent Intel gpu pick  VA-API (X11

---

### Post by neu5eeCh on 2016-10-20
Hmmm... Just tried those various settings. The playback, the frames, still "freeze" every second and a half as the audio continues undisturbed. Frustrating. 

Quick question: Are changes in preference immediate or does one need to restart VLC?

---

### Post by mc4man on 2016-10-20
they are immediate assuming you clicked "save"
You could run vlc from a terminal with -vv option & look thru output for some clues 
-vv produces a lot of output, you could output to a log file & then attach to a post if easier
something like - 
```
vlc -vv /path/to/video 2>&1 | tee vlc.log
```
Due to attachment limits here if deciding to do above compress the vlc.log to a .gz before attaching..

---

### Post by neu5eeCh on 2016-10-21
Thank you for your offer. There's the pain of navigating with SMPlayer, which I know works, or the pain of debugging VLC, which might not work and might take all kinds of time (both yours and mine). I'm opting for SMPlayer and giving up on VLC. I've tried just about every switch, setting and dongle I can find in VLC. Nothing helps. But thank you. :)

---

### Post by neu5eeCh on 2016-10-21
Just a quick additional note: I downloaded and tried **KODI**:

[https://kodi.tv/](https://kodi.tv/)

Works _beautifully_. Can't stress that enough. Love VLC (when it works) but KODI is more finished and easier to use. Problem solved -- sort of.

---

