---
title: "Sound Card Woes"
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by Synival on 2007-08-22
Hello,

I've already RTFM a few times, but I'm still stumped.  After a few days of headache, I was finally able to get audio input working.  Everything's on in alsamixer, and in SOME programs, things are working okay.  But now I have two problems:

1) I've fiddled around with all the mixer settings, but I can't get microphone loopback to turn off.  Is there some setting I missed somewhere?

2) After upgrading to Feisty, my sound card shows up as several devices, not just one.  For output, I have these devices in ALSA:
YMFPCI: (hw:0,0)
YMFPCI: (hw:0,1)
YMFPCI: (hw:0,2)

...and for input:
YMFPCI: (hw: 0,0)
YMFPCI: (hw: 0,3)

I really don't know much about what this means, but what I do know is that input is only captured for (hw: 0,3).  The problem is, there are a lot of programs that only give me the option of reading from YMFPCI without the (hw: x,x), and it doesn't work.  My microphone IS plugged into the correct port, unless my eyes lie to me.

Linux sound always gives me a headache, especially when considering that there's both OSS and ALSA :-/  Am I correct in saying that the /dev/dsp device is OSS? (this device also doesn't appear to be reading microphone input.)  In applications where YMFPCI (hw: 0,3) isn't an option as an audio input device, does this mean it supports OSS but not ALSA?

Any help or explanation of how all this works would really help me out.  I'm feeling a bit lost :-/

-- Simon

---

