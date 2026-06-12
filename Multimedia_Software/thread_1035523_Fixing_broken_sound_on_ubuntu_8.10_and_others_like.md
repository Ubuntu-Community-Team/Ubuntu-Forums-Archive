---
title: "Fixing broken sound on ubuntu 8.10 and others likely"
date: 2009-01-09
forum: Multimedia Software
---

### Post by budgallant on 2009-01-09
I was playing a YouTube video through opera when the window seemed to freeze up. It came back a few seconds later, but my sound went crazy then completely stopped...  after trying numerous things, except for a restart because that to me, is a last resort, and I had important apps going, I discovered a fix.

I don't know where this is from originally, but it is a script to restart your sound drivers, or some such thing.  Anyway, I am sure someone else can vouch for it's legitimacy. All you do is put it into a file and change it's permissions to be executable.  I hope this works for anyone having similar problems with their sound suddenly failing.

#!/bin/bash
# fix for PulseAudio auto-start broken

sleep 8
killall -9 pulseaudio
sleep 5 pulseaudio&
sleep 5
paplay
/usr/lib/openoffice/share/gallery/sounds/space.wav


I am using ubuntu 8.10. This fix was for an earlier version, but still worked like a charm for me. Give it 20 seconds or so, and then test your sound.

Hopefully ubuntu will fix this issue, as it has been several years since it was reported.

---

### Post by markbuntu on 2009-01-09
What version of flash are you using, and what version of Ubuntu?

---

### Post by budgallant on 2009-01-10
> **markbuntu said:**
> What version of flash are you using, and what version of Ubuntu?

I installed ubuntu 8.10 last week. I am not sure what version of flash, but it must be the most recent one, as everything was installed just days ago. I am still very new to ubuntu, so I can not say specific version, but if you need to know, I will check if you can direct me.

---

