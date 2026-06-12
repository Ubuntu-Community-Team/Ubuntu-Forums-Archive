---
title: "rosegarden on 7.10"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by temy on 2007-10-20
My Rosegarden worked fine on 7.04 Studio. Now I have upgraded to 7.10 and at startup it comes with the the error message "MIDI resolution too low" as if I did not have a lowlatency kernel. In fact I have and when I ignore the message it sort of works (sees the MIDI input) but does not see my sound card. If I use JACK server, it's even worse. Any suggestion? Thanks.:(

---

### Post by daverich on 2007-10-20
see my post about reaper.

Something is definately different in gutsy and it's not good for audio stuff.....

Kind regards

Dave Rich

---

### Post by Jadd on 2007-10-21
Don't the linux image rt and linux headers rt fix that?

---

### Post by andresv on 2007-10-30
I keep getting this message:

ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave

so, somehow, Jack seems to be running OK, timidity also - yet rosegarden cannot produce any sound. This is incredibly frustrating.

---

### Post by aonegodman on 2007-12-26
Got the same thing. Same old problems. Can't anybody find a fix to the audio/midi/sound problems on 7.10?

What's the best setup to get sounds working in all apt's?

You get one working and another one craps out.

Anyone got Rosegarden working in Gutsy 7.10 x386?

---

