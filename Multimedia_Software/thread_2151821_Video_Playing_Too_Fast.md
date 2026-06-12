---
title: "Video Playing Too Fast"
date: 2013-06-05
forum: Multimedia Software
---

### Post by elfin8er on 2013-06-05
Every time I watch Youtube, the video goes faster than it's supposed to. It's not much, but it's enough to notice people's voices are higher than normal. I especially notice this when I play music on Youtube. Does anybody know what could be the problem, and if there are any known fixes? I haven't tried this on offline video, but I'll be sure to do so shortly.

---

### Post by MadmanRB on 2013-06-06
Do you have HDMI?

If you do switch to analog audio, this is a bug with the current Flash

What version of Ubuntu are you using?

---

### Post by elfin8er on 2013-06-06
I'm using VGA

Pretty sure I'm using analog audio (That's what you'd plug headphones, or a stereo into, correct?)

Version 13.04

---

### Post by MadmanRB on 2013-06-07
Just double check, this seems to be a bug in chrome.

---

### Post by DJWYMAN on 2013-06-07
I have been having the same issue the past few days...I thought I was loosing my mind.  a restart clears it up for me for a bit but then it comes back.

---

### Post by MadmanRB on 2013-06-07
I have pretty much pinned it down to pulse

---

### Post by DJWYMAN on 2013-06-07
so is pulse and flash not playing well together at the moment?  I tried other media formats on my 2 systems that are both having the issue (one running 13.04 ubuntu and the other lubuntu 13.04) and the sound is fine in those other formats ie avi, mp3 and mp4.  I have not yet tried other browsers yet however it is a problem with pepper flash it will not change on chromium for my ubuntu system because I have it settup to run pepper flash as well.  the Lubuntu system would have regular old 11.2 or what ever it is.

---

### Post by MadmanRB on 2013-06-07
Yes it seems to be the case, ther issue stems from pepperflash and pulse.
I say remove or edit pulse and replace it with Alsa.

---

### Post by DJWYMAN on 2013-06-07
after searching around the interwebs I found this bug report and work around :

[https://code.google.com/p/chromium/issues/detail?id=229918](https://code.google.com/p/chromium/issues/detail?id=229918)

the short of it you are changing your default-sample-rate = from 44100 to 48000 this can be found in /etc/pulse/daemon.conf

but chromium/chrome seem to be trying to fix the issue and are working with pulse devs.

---

