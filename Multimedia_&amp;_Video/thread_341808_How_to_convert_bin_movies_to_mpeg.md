---
title: "How to convert bin movies to mpeg?"
date: 2007-01-19
forum: Multimedia &amp; Video
---

### Post by robertoneto123 on 2007-01-19
Hello,

I got a movie stored on .bin format. I can read it on MPLAYER, but I want to transform it on mpeg (DIVX) or AVI. What tool can do this?

Thanks!

---

### Post by lukew on 2007-01-19
> **robertoneto123 said:**
> Hello,

I got a movie stored on .bin format. I can read it on MPLAYER, but I want to transform it on mpeg (DIVX) or AVI. What tool can do this?

Thanks!

You can use the file command to find out what it really is and then take it from there.

Alternatively you can find out what it is from the description in MPlayer!

bin file as a movie file..... very strange!!

file

---

### Post by david_2001 on 2007-01-19
If mplayer can play this strange .bin file then mencoder should be able to transcode it to mpeg4 (avi is just a container file format for audit and video).  Take a look at the mencoder documentation [[COLOR="Blue"]_here_[/COLOR]]("http://www.mplayerhq.hu/DOCS/HTML/en/mencoder.html").

---

### Post by halitech on 2007-01-19
it's probably part of a cue/bin combo that some torrent sites use for distribution. windows users can use something isobuster to extract it but I haven't found anything that works in linux yet.

---

### Post by taurus on 2007-01-19
You can burn cue/bin directly with k3b.

---

### Post by halitech on 2007-02-20
I know this is an older thread but I was looking on the WINE site and ISOBuster will run under WINE. I've actually installed it and and it works like a charm, just as good as it does in windows.

---

### Post by dannyboy79 on 2007-02-20
why wouldn't you be able to mount this just like you mount an iso? then simply copy the contents out and do what you want with them. convert them, encode them, decode them. whatever.,

what about giving this a try [http://linux.softpedia.com/get/Desktop-Environment/Tools/Mount-ISO-image-2216.shtml](http://linux.softpedia.com/get/Desktop-Environment/Tools/Mount-ISO-image-2216.shtml)

unless you already have wine configured to work of course.

---

### Post by halitech on 2007-02-20
I tried the mount ISO and couldn't get it to work. Also with a cue/bin, it is a dat fileso copying it out doesn't seem to work.

and I have WINE setup and running fine :)

---

