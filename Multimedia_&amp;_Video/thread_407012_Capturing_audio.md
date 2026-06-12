---
title: "Capturing audio"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by Swab on 2007-04-11
I'm looking for a way to record sound that is playing on my PC.  I don't mean externally sourced sound.. for instance I want to record the audio that is playing in a flash file.

Is there a program to do this?  Or, is there a device I can use the cat command on the capture the audio?

Thanks.

---

### Post by smbm on 2007-04-11
I always used Audacity to do this. Just pressed record while whatever I wanted to record was playing (if that makes sense).

It should be in the repos.

Good luck

---

### Post by Swab on 2007-04-11
Yeah, audacity doesn't seem to work for me.

---

### Post by smbm on 2007-04-11
Fair enough.

There is another way to do it (that I know of with my limited knowledge) and that would be to take it out of the headphone/speaker/line out socket on your soundcard and pipe it back in again. Not very elegant and you would lose some quality but it would work.

I guess there must be a way of piping out the raw sound bitstream thingy before it gets converted to analogue but that's way beyond my knowledge.

On that note I'll wish you luck again and bow out of this thread.

---

### Post by Swab on 2007-04-11
> **smbm said:**
> Fair enough.

There is another way to do it (that I know of with my limited knowledge) and that would be to take it out of the headphone/speaker/line out socket on your soundcard and pipe it back in again. Not very elegant and you would lose some quality but it would work.

I guess there must be a way of piping out the raw sound bitstream thingy before it gets converted to analogue but that's way beyond my knowledge.

On that note I'll wish you luck again and bow out of this thread.

Thanks for your help. 

I'm sure there is a very simple way to cat the audio to a file, but I just don't know what it is!

---

### Post by Swab on 2007-04-11
Something along the lines of..

cat /dev/dsp > audio.wav  

Doesn't work, should it?

---

