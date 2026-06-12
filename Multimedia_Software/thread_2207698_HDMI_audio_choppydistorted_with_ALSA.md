---
title: "HDMI audio choppy/distorted with ALSA"
date: 2014-02-24
forum: Multimedia Software
---

### Post by uttaranduutta2 on 2014-02-24
[COLOR=#000000][FONT=Verdana]Hi, [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I have ATI AMD video card HD7770 with HDMI o/p i use. I am able to get sound but its very very choppy/distorted. [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]**The strange fact is output works perfectly with default Pulse audio settings (no distortion/choppiness)**[/FONT][/COLOR][COLOR=#000000][FONT=Verdana] . Since ALSA sounds better has better support for bit streaming i am very interested to get native ALSA running. Things i have already tried [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]1. Completely removing/stopping pulse audio the alsa choppiness/distortion still remains [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]2. I have tried both fglrx & opensource radeon driver with same result [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]3. So basically when a stream plays through default pulse audio its perfect but when directly through ALSA its distorted. to see the difference i recorded the info in [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]**cat /proc/asound/card1/pcm3p/sub0/***[/FONT][/COLOR][COLOR=#000000][FONT=Verdana] in both the cases the major difference in o/p was [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]access: MMAP_INTERLEAVED >>>pluse audio [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]access: RW_INTERLEAVED >>> native alsa [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Is there a way to force mmap mode in native alsa or any other idea ?? [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]If you can suggest a better place to pose this query please ??[/FONT][/COLOR]

---

### Post by wildmanne39 on 2014-02-24
*Thread moved to **Multimedia & Video**.*

---

