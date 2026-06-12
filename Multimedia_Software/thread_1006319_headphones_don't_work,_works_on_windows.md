---
title: "headphones don't work, works on windows"
date: 2008-12-09
forum: Multimedia Software
---

### Post by Bas1234567 on 2008-12-09
Hello,

When I play music on my laptop, the sound comes out of the speakers of the laptop, also when I plug in my headphones (or the cable to my music set). There's no sound on the headphones, and still sound from the laptopspeakers.

I tried to a adjust volumes in volume control, but that doesn't help. On windows (on the same laptop, dualboot) the music automatically switched from the laptopspeakers to the headphones at the moment I plug them in.

Any ideas ?

Thanks in advance!

---

### Post by philetus on 2008-12-09
The "  Comprehensive Sound Problem Solutions Guide" at the top of the page
helped me out.
Also, go into "configure local sound server/simultaneous output and checkmark it.
Go into System/preferences/sound and set it to Autodetect/Autodetect/Autodetect/PulseAudio Sound Server/Simultaneous output to ALSA  PCM on 
front:0............
Then go to PulseAudio volume control and set playback to:
/Autodetect/PulseAudio Sound Server/Simultaneous output to ALSA  PCM on 
front:0.........

This works for me.

---

### Post by philetus on 2008-12-09
P.S. I set mine up for USB audio/USB headphones.

---

