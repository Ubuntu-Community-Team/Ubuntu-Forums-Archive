---
title: "Sounds stops working at random"
date: 2006-03-10
forum: Multimedia &amp; Video
---

### Post by rorschach on 2006-03-10
I am having a problem where my sound stops working not too long after I bring up the system. Upon boot, everything works fine. However, afer a while, sound stops responding. I checked lspci and it sees my sound card (Multimedia audio controller: Creative Labs SB Audigy (rev 04).) I went through a few of the troubleshooting options listed for sound, the hoary, alsamixer, esd, and /dev/dsp fixes listed did not fix the problem.
I did find that when I go to the Multimedia Systems Selector, and try and run the default sink through OSS, I hear the test tone from my center speaker, however if I put the default source to OSS, I get nothing. By the same token, when Default Sink is set to ALSA (or ESD for that matter), I get Failed to construct test pipeline for ALSA - Advanced Linux Sound Architecture.

Ideas?

---

### Post by Ubuntist on 2006-03-10
I've had lots of problems with sound going away.  One thing I finally figured out was that at least sometimes the problem was that the analog/digital output jack on my Audigy 2 sound card was getting turned off.  So I open the volume control and go to the Switches tab and make sure that Audigy Analog/Digital Output Jack is checked.  If that check box doesn't appear, then  select Edit | Preferences (still within the volume control) and check the box of the same name in that menu.

I don't know if this will work for you, but it's an idea.

---

### Post by rorschach on 2006-03-10
I'll keep an eye out for that, I just checked, and it is on, but then again, sound is working at the moment.

Any other thoughts on where to look?

---

### Post by Ubuntist on 2006-03-20
No, sorry.  Right now I've re-awakened a hibernated session and have no sound.    The Analog/Digital Output Jack has come unticked.  I've ticked it again, but still no sound.  Based on past experience, though, I'm pretty confident that when I start a completely new session, sound will be back.

---

