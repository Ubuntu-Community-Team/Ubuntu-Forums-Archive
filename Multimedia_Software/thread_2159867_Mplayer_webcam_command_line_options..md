---
title: "Mplayer webcam command line options."
date: 2013-07-04
forum: Multimedia Software
---

### Post by Fenderian_Mayhew on 2013-07-04
I have been playing with direct webcam access via mplayer.
I use this command to view my camera.
```
mplayer tv:// -tv driver=v4l2:width=1024:height=720: device=/dev/video0 -vf screenshot
```

I am trying to understand the v4l2 options; how to find which options are available and which manuals , files, or program outputs can tell me which device can use or benifit from each option. so for example I know that to controll the brightness or contrast within this code you add ```
:brightness=<0-100>:
``` anywhere, but what other commands/options can be added this way and which manuals should i read, or is there a type of "list all options for device" command? I Have already googled' my problem and came up confused, i dont know _what_ to ask about.

---

