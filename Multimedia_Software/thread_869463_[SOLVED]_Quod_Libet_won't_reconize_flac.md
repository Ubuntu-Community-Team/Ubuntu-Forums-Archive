---
title: "[SOLVED] Quod Libet won't reconize flac"
date: 2008-07-24
forum: Multimedia Software
---

### Post by krelverehan on 2008-07-24
I have been using Quod Libet for quite some time now, and have been happy with it so far.

But I won't recognize flac files. Other files I use work fine... ogg, mp3, etc.

When trying to open a flac file (which I can open w/ totem) I get this error.
 
IOError: file type could not be determined

I have seen is complaint from a few people, yet I can't seem to find a solution for me. Any ideas?

---

### Post by hugmenot on 2008-07-25
Try to run mutagen-inspect on the file:

```
mutagen-inspect xyz.flac
```

If it says that your FLAC file contains ID3 tags, then it is broken.

---

### Post by krelverehan on 2008-07-26
> **hugmenot said:**
> Try to run mutagen-inspect on the file:

```
mutagen-inspect xyz.flac
```

If it says that your FLAC file contains ID3 tags, then it is broken.

This is what I get if I check one of the files not recognized:
```

krel@namcle ~ $ mutagen-inspect Music/completed/Biosphere\ -\ Substrata/01\ -\ As\ The\ Sun\ Kissed\ The\ Horizon.flac 
-- Music/completed/Biosphere - Substrata/01 - As The Sun Kissed The Horizon.flac
- MPEG 1 layer 1, 128000 bps, 44100 Hz, 421.54 seconds (sketchy) (audio/mp3)
TDRC=2001
TIT2=as the sun kissed the horizon
COMM=='eng'=Track 1
TENC=Exact Audio Copy   (Secure mode)
TRCK=01/11
TPE1=biosphere
TALB=substrata
TCON=Ambient
```

I am still stumped. I hope this helps!

---

### Post by hugmenot on 2008-07-26
Yes, it helps. Easytag? Known problem.

[Look here, old thread]("http://ubuntuforums.org/showthread.php?t=209371&highlight=flac+mutagen-inspect")

---

### Post by krelverehan on 2008-07-26
Well, I actually use kid3-qt to edit tags... But it seems as they were broken right from the download.

Anyway, I fixed the problem by using easytag to remove the tags from the files, and redoing the tags using ex falso, which is the tag editor that comes with quod libet.

Thanks for your help!

---

### Post by hugmenot on 2008-07-26
Hm, maybe I should have re-iterated the solution from the old thread: The guy just toggled "off" the "write ID3 to FLAC" option, and then hit "re-tag", or somesuch.

So it was a big automatic batch, no need for re-tagging. 

BTW: [http://flac.sourceforge.net/faq.html#general__tagging](http://flac.sourceforge.net/faq.html#general__tagging)

---

### Post by krelverehan on 2008-07-26
I suppose I could have done that... It is just that I am not all too familiar with easytag (I couldn't find a re-tag button) but I am very comfortable with ex falso, and all my tag information I use is stored in the directory/filename anyway, so retagging wasn't an issue.

---

