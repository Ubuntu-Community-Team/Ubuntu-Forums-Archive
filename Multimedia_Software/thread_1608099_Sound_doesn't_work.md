---
title: "Sound doesn't work"
date: 2010-10-28
forum: Multimedia Software
---

### Post by guest100 on 2010-10-28
Hello,

Please bear with me, I'm very new to Linux (about 1 hour now).  I just installed Ubuntu 10.10 and everything seems to be working Ok, except my sound.  It's an onboard sound card (ASUS P5Q motherboard). I have absolutely no idea how to start troubleshooting in Linux.

Any help would be wonderful...

Thanks,
eb

---

### Post by ajgreeny on 2010-10-28
This may or may not help, but is certainly worth a try.

Run ```
alsamixer
``` in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

Also check **Pulseaudio Volume Control** in the sound and video menu, (you may need to install **pavucontrol** to do that).

---

