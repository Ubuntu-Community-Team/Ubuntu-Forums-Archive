---
title: "How to play videos in a terminal with mplayer?"
date: 2010-12-19
forum: Multimedia Software
---

### Post by dillandriskell on 2010-12-19
I've Googled this extensively but all I get are guides on how to watch videos in the terminal with ASCII, which I don't want. I know it can be done with mplayer on a tty with relatively decent quality, as I've done it before, but I lost and forgot the code :( (should have backed up my .bashrc). I've tried a lot of the -vo options but to no avail, the audio works fine, but the only one I tried that at least attempted to play the video was svga, but that just messed with the resolution and made the text really big. Here's the code I used:

```
mplayer -vo svga video.flv
```

If anybody knows how to help me get this running it would be massively appreciated, I've been digging through the man pages of mplayer all night to no avail. And if anybody has any solutions that don't use mplayer I'd be open to that as well.

---

### Post by syntheticowls on 2011-10-01
I used...

```
mplayer -vo caca video.avi

```
to good effect...

or you could use
```
[COLOR=#C20CB9]****[/COLOR]mplayer [COLOR=#660033]-vo[/COLOR] aa movie.avi
```

depending on if you have libcaca or aalib installed.

---

### Post by syntheticowls on 2011-10-01
oh... sorry to necromance a thread. I didn't realize it was almost a year old. But maybe someone else will find it of use. :p

---

### Post by syntheticowls on 2011-10-01
darn. now that I reread the original post, it seems he did Not want to view it in ASCII. Oh well.

---

### Post by nothingspecial on 2011-10-01
That's ok, but try not to in the future. :D

And you can use the framebuffer.

Closed.

---

