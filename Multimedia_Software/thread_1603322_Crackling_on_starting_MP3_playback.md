---
title: "Crackling on starting MP3 playback"
date: 2010-10-22
forum: Multimedia Software
---

### Post by LaptopU on 2010-10-22
On Maverick, I noticed a couple of days ago when I started an MP3 of a single tone recording it had a 'crackle' for about a quarter of a second at the start of playback.  I initially thought there was a problem with the recording but I have noticed it is universal and I now pick up it is happening on some songs too (particularly if they start on a single note, not all songs seem affected).

This is a problem if I double-click a sound file which I open in Totem, it's also a problem if I start playing an affected track on Rhythmbox, it also happens if I just hover the mouse to start playback, but interestingly any problematic file if I load into Audacity there is no problem at all and the file plays correctly.

I doubt anyone else will have noticed this bug as it is so small and I wouldn't have picked up on it had I not been playing a single tone recording, but now I have picked up on it I can detect it all the time which is annoying.  Has anyone else noticed at all?

---

### Post by lidex on 2010-10-23
> **LaptopU said:**
> On Maverick, I noticed a couple of days ago when I started an MP3 of a single tone recording it had a 'crackle' for about a quarter of a second at the start of playback.  I initially thought there was a problem with the recording but I have noticed it is universal and I now pick up it is happening on some songs too (particularly if they start on a single note, not all songs seem affected).

This is a problem if I double-click a sound file which I open in Totem, it's also a problem if I start playing an affected track on Rhythmbox, it also happens if I just hover the mouse to start playback, but interestingly any problematic file if I load into Audacity there is no problem at all and the file plays correctly.

I doubt anyone else will have noticed this bug as it is so small and I wouldn't have picked up on it had I not been playing a single tone recording, but now I have picked up on it I can detect it all the time which is annoying.  Has anyone else noticed at all?

Have seen this off and on. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

