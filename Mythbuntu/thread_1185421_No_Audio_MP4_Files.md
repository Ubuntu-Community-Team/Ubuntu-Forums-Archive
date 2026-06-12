---
title: "No Audio MP4 Files"
date: 2009-06-12
forum: Mythbuntu
---

### Post by Dragonflyoh on 2009-06-12
When using the default Mythtv player AVI files play fine. When I play a MP4 file the video gets choppy every 5 to 10 seconds. I tried using Xine, Vlc and Mplayer and all three do well with the video however there is no audio.
I am running a front end machine with Mythbuntu 9.04, my audio output is ALSA with spdif to my external amplifier. I had a bit of a time getting ALSA set up with the default player and did not want to do that again unless that is where the problem would be. I looked at the settings for the audio from each of the players and saw nothing that I understood. Any help would be appreciated.

I found this for Mplayer:
mplayer -fs -zoom -ao alsa:device=spdif

Under Video Settings/File Types I added mp4 with the mplayer settings and everything is working fine.

---

