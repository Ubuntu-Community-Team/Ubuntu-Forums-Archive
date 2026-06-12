---
title: "How can I play 3gp files?"
date: 2009-05-26
forum: Multimedia Software
---

### Post by mvalviar on 2009-05-26
I have win32 codecs installed but I can't play *.3pg files. I tried with totem (gstreamer) and mplayer. Any ideas or work arounds you can suggest?

---

### Post by .nedberg on 2009-05-26
RealPlayer should work

---

### Post by DJJo on 2009-05-26
VLC play all kind of file's
you can even open a you tube link

---

### Post by andrew.46 on 2009-05-26
Hi mvalviar,

> **mvalviar said:**
> I have win32 codecs installed but I can't play *.3pg files. I tried with totem (gstreamer) and mplayer. Any ideas or work arounds you can suggest?

The [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") version of MPlayer allows playback of these files. 

Andrew

---

### Post by mvalviar on 2009-05-27
> **DJJo said:**
> VLC play all kind of file's
you can even open a you tube link

I tried VLC. It plays but without audio. I'm getting an error notice when I play them.

---

### Post by ravind on 2009-07-23
andrew.46, you genius! You're right, it worked. medibuntu's mplayer does the trick.

I tried all sorts of things to get my 3gp files to play with audio but they all failed (including installing realplayer). I was using the standard mplayer from Ubuntu's repositories but that didn't bite either so i uninstalled it after reading your post and installed medibuntu's version of mplayer. Life is good again. :D

---

### Post by andrew.46 on 2009-07-23
Hi ravind,

> **ravind said:**
> andrew.46, you genius! You're right, it worked. medibuntu's mplayer does the trick.

Good to hear it is all working for you :-). Hopefully soon there will be less of an issue with finding media players compiled against the *non-free *amr libraries as the latest versions of FFmpeg and MPlayer now compile against a free library.

All the best,

Andrew

---

