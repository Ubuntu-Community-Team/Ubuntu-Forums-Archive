---
title: "Cannot play audio from multiple programs at once"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by Bluecircle on 2007-05-22
I seem to be having a problem where only one program can play audio at a time. ex. if xmms is playing, open arena won't play sound, or a youtube video won't play audio etc...

Is there an easy fix for this? I tried changing from ALSA to OSS and ESD but it doesn't seem to make a difference.

---

### Post by Steveway on 2007-05-22
This is not a bug, this behaviour is prefectly correct.
> Q: When I play something and I try to play something other the second attempt
   will not fail but instead it hangs waiting for the completion of the first
   sound.
A: This is definitely the standard behaviour as described in many official
   documents that now ALSA follows. There is no reasons to complain about that
   for the following reasons:
   - it's the right (standard) way
   - the application that want a different behaviour can open the device in 
     O_NONBLOCK mode
   - all modern OSS drivers in mainstream kernel (cmpci, es1370, es1371,
     esssolo1, maestro, sonicvibes, vwsnd) works in the same ways and the 
     others have to be intended buggy
   - we want you ask to broken applications author to fix them ;-)


---

### Post by Bluecircle on 2007-05-22
so is there any way to change this?

---

