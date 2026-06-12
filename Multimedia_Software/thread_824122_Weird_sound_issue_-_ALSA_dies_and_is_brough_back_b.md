---
title: "Weird sound issue - ALSA dies and is brough back but why?"
date: 2008-06-09
forum: Multimedia Software
---

### Post by IvanKMN on 2008-06-09
I haven't worked with Linux in a while but recently got the itch to create a HTPC for my living room.  I'm running 8.04 and have a motherboard with onboard Realtek ALC889A audio.  It's currently recognizing as an ALC882/885 even after updating to the 1.0.17rc1 ALSA module following [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and [http://ubuntuforums.org/showthread.php?p=5134422]("http://ubuntuforums.org/showthread.php?p=5134422") and confirmed by:

```
xbox@Toaster:/etc/init.d$ alsactl -v
alsactl version 1.0.17rc1
```

Basically audio out of optical seems to work for the most part until I hit a landmine (doesn't seem to like Dolby Digital 5.1).  At this point no audio works.  I can recover by copying /etc/init.d/alsa-utils to a backup file, rebooting, and then copying it back and running alsamixer to unmute all of my channels.  But... this is becoming very tedious.  Mostly I just want to be able to watch media files, etc.  So... my questions are:

1. I updated to the latest 1.0.17rc1 ALSA module.  Should I expect to see the audio devices recognized as an 889A or still 882/885?  I just wonder if the update didn't take.

2. What's the underlying reason (or how can I get enough information to determine the underlying reason) for my audio stopping to work?

3. Would OSS better support my hardware?

4. Are there any good, reliable cards (half-height, preferrably, to fit into my HTPC case) that will ouput to optical audio?

Any advice/assistance you could provide would be fantastic.  Thanks!  :)

---

