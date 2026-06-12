---
title: "mp3blaster &quot;Failed to open sound device&quot;"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by gekkehenkie on 2008-01-13
Hi all,

I'm using mp3blaster, but quite often it outputs that it has failed to open the sound device. I guess it is busy or sth. Anybody who has a clue on how to prevent this?

I saw another post with the same problem from somewhere in 2006, but nobody replied to that one. I hope I have more luck :)

Thanks in advance!

---

### Post by baryonyx on 2008-02-24
MP3blaster started giving me this error recently as well.  Specifying the path to the audio device solved it for me.  Try mp3blaster -s /dev/dsp.

---

### Post by gekkehenkie on 2008-03-13
Thank you very much! It does work, though it's dsp1 in my case

Cheers!

---

