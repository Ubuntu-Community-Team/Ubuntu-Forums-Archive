---
title: "Jack wont start with specified sample rate, defaults to 48kHz"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by capsid on 2006-10-10
Hey there, I was wondering if anybody could help me figure this one out.  All my stuff is recorded at 16-bit 41kHz stereo, which is fine for my needs.  I specify in Qjackctl (and I checked in .jackdrc) that jackd is supposed to start at 41kHz sample rate.  As soon as it starts, however, it defaults to 48kHz.  I'm wondering if my sound card just doesn't support 41 because i *vaguely* remember an error message from manually starting jackd back before I knew what I was doing with all this stuff.  Qjack message window isnt telling me anything useful.  Any idea how I could find out if this is a hardware limitation or a software misconfiguration??  Could it have anything to do with my other Qjack settings, like frames/period, periods/buffer? etc...

I'm trying to figure this out so I can record the linux equivalent of Windows' "stereo mix".  I like to hit record on audacity and mix my sequences and samples live.  I'm getting terrible performance when I try to do this, and I'd like to see if it has to do with realtime sample rate conversions or sample rate being too high or something...It's times like these I wish Linux had a unified sound system ;P  *not complaining*.  I can always run the headphone out to another computer, but it picks up a lot of line noise, and I can't even imagine how you'd balance a stereo miniplug (keeping stereo intact).  Audacity's noise redux works well, but a clean signal is always better than using noise reduction. 

As always, thanks for your help..

---

