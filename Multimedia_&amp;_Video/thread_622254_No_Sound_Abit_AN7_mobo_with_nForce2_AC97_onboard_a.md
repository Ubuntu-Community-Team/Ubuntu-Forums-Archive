---
title: "No Sound: Abit AN7 mobo with nForce2 AC97 onboard audio"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by brandonjp on 2007-11-24
I'm not getting any sound at all.  I've got this Abit AN7 motherboard, it has the onboard Nvidia nForce2 audio device.  I'm using Ubuntu 7.10,  under System > Preferences > Hardware Information it recognizes the audio device as:  nForce2 AC97 Audio Controler (MCP)

```
ls /proc/asound/
``` gives me this:
```
card0  cards  devices  modules  nForce2  oss  pcm  seq  timers  version
```
So it appears to at least correctly recognize the card, right?

I've tried a live cd with no luck and have also tried realtek-linux-audiopack-4.06a.tar.bz2 - that i got from somewhere - both with no luck.

Finally, I've tried a USB audio device - Tascam US-428 - but couldn't get any out of the box audio from it either.

I've followed on the recommended tutorials and troubleshooting procedures on as many message boards and guides as google could find.  Anyone use these particular components or have any other ideas?

Thanks
--bp

---

### Post by Yellow Pasque on 2007-11-24
If you've exhausted all your options with ALSA, try OSSv4. See my sig for details.

---

