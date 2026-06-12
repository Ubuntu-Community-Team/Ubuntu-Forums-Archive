---
title: "xine is sending sound to the wrong device."
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by Daniel Rehm on 2007-06-01
EDIT - IGNORE ME I had the wrong default card selected.

Still strange that the output was going to two separate places!

------------------------------------------------------------------------

The facts:

Following the comprehensive sound problem thread, I managed to get my Soundblaster Audigy working. Everything seemed to work just fine. Or so I thought. 

Turns out everything works except apps that use xine as their sound engine.

I originally thought it was an issue with Amarok. I was fiddling around with the settings and, on a whim, I yanked the speaker plug out of the jack on my sound card and plugged it into the jack on my motherboard. To my surprise, I could now hear my music... but nothing else.

After some experimentation, I discovered that xine was also sending sound to the on-board device instead of the soundcard.

All other apps (rythmbox, for example) appear to send sound output to the soundcard.

I was unable to find any obvious setting to send xine's output to the other sound device.

Any input would be greatly appreciated.

---

### Post by Daniel Rehm on 2007-06-01
After fooling around with my settings a little more it appears that the system sounds are also going to the motherboard.

---

