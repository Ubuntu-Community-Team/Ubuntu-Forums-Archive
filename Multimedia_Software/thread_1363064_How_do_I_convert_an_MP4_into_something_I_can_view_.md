---
title: "How do I convert an MP4 into something I can view on my DVD player?"
date: 2009-12-23
forum: Multimedia Software
---

### Post by kevinwmiller on 2009-12-23
I have an MP4 that I need to convert to a file format that I can burn to a DVD, that will be recognizable to my DVD player.

Thanks

---

### Post by aok on 2009-12-24
I recently had to do the same thing so I made a little note of it:

[LIST=1]
[*][FONT="Courier New"]ffmpeg -i source.mp4 -target ntsc-dvd target.mpg[/FONT]
[*][FONT="Courier New"]dvdauthor -t -o target.dvd -c 0,0:20:00,0:40:00,1:00:00 -f target.mpg[/FONT]
[*][FONT="Courier New"]dvdauthor -T -o target.dvd[/FONT]
[*][FONT="Courier New"]mkisofs -dvd-video -o 01.img 01.dvd/[/FONT]
[*]Burn the 01.img to a DVD
[/LIST]

I hope this helps!

---

### Post by kevinwmiller on 2009-12-24
Ok, where it says target.mpg, you mean my mp4 file, right?

Sorry, kind of a noob. lol

---

### Post by ThaDoctor99 on 2009-12-24
Yeah he meant that.
However there is also websites who do all the work for you....
I know of [www.media-convert.com](www.media-convert.com) I think else it is something similiar.
You choose input and output, then they do all the converting it is however a little bit slow.
But I  have used it a couple of times. Oh yeah and it is a free service.

Greetings from Denmark

---

### Post by ron999 on 2009-12-24
> **kevinwmiller said:**
> Ok, where it says target.mpg, you mean my mp4 file, right?

Sorry, kind of a noob. lol

NO
It's **source.mp4** that is your mp4 file.
Put your own mp4 file name instead of source.mp4.
:)

---

