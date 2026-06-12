---
title: "Anyone know of a program that can reencode a video to a smaller resolution?"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by brim4brim on 2007-06-18
I'm looking for a program that can make the resolution smaller on a movie and change the codecs used to Xvid and MP3 in one go.

Even something that does them separately would do.  At the moment, I have a program that will encode to Xvid and MP3 but when I use it on my Archo's player, it says image size too big.

---

### Post by flossgeek on 2007-06-18
Try [URL="http://avidemux.berlios.de/"]Avidemux 
[/URL]
If that doesn't do the trick you can try [DVD:Rip]("http://www.exit1.org/dvdrip/").

They are both in the repositories I thinks ;-)...

---

### Post by ComplexNumber on 2007-06-18
you could try LiVes([click]("http://lives.sourceforge.net/")). the program is fairly hefty, though.

---

### Post by timcredible on 2007-06-18
ffmpeg will do it

---

### Post by brim4brim on 2007-06-25
Thanks, for the replies.  I didn't realise I had gotten replies.

I was using AVIdemux as it turns out, not sure if it has the options to change resolutions.  Couldn't find them anyway but I'll have another look.

Tried DVD:rip aswell.  I'll try Lives and if that fails, I'll use ffmpeg (presumably the command line can do all this and the user interfaces just have not implemented it or something).

Actually ffmpeg has a list of programs using it on their page so I can check it out.
[http://ffmpeg.mplayerhq.hu/projects.html](http://ffmpeg.mplayerhq.hu/projects.html)
^If anyone else arrives here, that's the link.

Some of those are Windows based so they won't all work but hopefully, one will do the job.  Actually a lot of them aren't for encoding to other formats.  Should of known since ffmpeg is used for so many different tasks.

---

### Post by Major_Kong on 2007-06-25
You have to use the avidemux filters, and in the process reencode the file.

After opening the file choose a encoder (e.g. xvid4) and then click on filters. Then you just have to select the resize filters.

---

