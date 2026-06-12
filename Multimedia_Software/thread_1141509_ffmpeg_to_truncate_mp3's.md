---
title: "ffmpeg to truncate mp3's"
date: 2009-04-28
forum: Multimedia Software
---

### Post by benf101 on 2009-04-28
First of all, is there a complete listing of all ffmpeg capabilities and options?

Here is what I want to do...

I have a slew of mp3s of a podcast in a directory.  Commercials are at the exact point in every show.  I want ffmpeg to clip out the commercials.  In other words, tell it to remove content between 5minutes and 8 minutes, 15 minutes and 19 minutes... etc.

Or possibly break up the file into sections at certain points... then I could reassemble the non-commercial sections.

Any help is appreciated, especially if someone knows where the complete ffmpeg how-to's exist.

Thanks.

---

### Post by logos34 on 2009-04-28
there's [Mp3splt]("http://mp3splt.sourceforge.net/mp3splt_page/documentation/man.html")

maybe after splitting you could use cat to join the 3 non-commercial parts of each track

---

### Post by benf101 on 2009-05-05
mp3splt is great!  The next trick is to get it installed on a server that I don't have root permissions on...

---

### Post by benf101 on 2009-05-05
Oh, one more thing, mp3wrap rejoins the split sections of the mp3.  Their website tells you about that.

---

### Post by logos34 on 2009-05-05
yeah, forgot about mp3wrap, hardly use the app myself.  

But the mp3splt-gtk gui is pretty darn nice.  Too bad it doesn't handle lossless format (flac and ape files)

---

