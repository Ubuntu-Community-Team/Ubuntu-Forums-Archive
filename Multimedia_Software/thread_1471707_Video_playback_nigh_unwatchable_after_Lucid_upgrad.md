---
title: "Video playback nigh unwatchable after Lucid upgrade"
date: 2010-05-03
forum: Multimedia Software
---

### Post by WinstonChurchill on 2010-05-03
I have an old, decapitated (the screen died) MacBook G4 that acts as a somewhat badly-endowed HTPC for my HDTV downstairs. This (somewhat surprisingly) worked well - it can't play 720p or greater content, but it could render 480p stuff at 1920x1080 resolution. However, once I upgraded to 10.04, I see large vertical distortions during video playback (much like when you stretch a picture in MS Paint). I've tried several different "Output" options in the Video pane of the VLC Settings, with the following results:

[LIST]
[*]X11: The bands disappear, but I get like 1 frame every 2 seconds when I set it to fullscreen
[*]XVideo Extension Output: Smooth video, but the bands are there...
[*]OpenGL: Looks better than X11, but I get 1 frame every 10 seconds with this setting
[/LIST]
The ASCII Art setting works great, but obviously leaves something to be desired visually... The specs for the laptop so far as I can tell from dmesg are:

[LIST]
[*]1.33 Ghz single-core processor
[*]512 MB of RAM
[*]The video processor uses the driver "radeonfb" (I don't know the exact model); core clock is 210 Mhz, memory clock is 183 Mhz - does not say how much video memory it has.
[/LIST]
So far as I can tell, the video card is somewhat irrelevant anyway - I never got any different results weather or not hardware acceleration was enabled in VLC, so I'm thinking there's not any happening at all. The exact same issues show up in the Movie Player application as well.

Any ideas? I'll reinstall 9.10 if I have to, but I'd really rather not... Thanks for your help!

---

