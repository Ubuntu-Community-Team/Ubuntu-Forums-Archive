---
title: "m4v not playing"
date: 2009-07-22
forum: Multimedia Software
---

### Post by Uinluan on 2009-07-22
The question I have is that I have an m4v file that I would like to play on my Ubuntu 9.04 install.  The first time I tried to play it VLC actually started playing it and the crashed.  Every attempt after that using VLC it doesn't even start playing.  I also have tried mplayer and helix and gxine.  These players come up with an error that states "Could not determine type of stream"  Is it possible to play this file?  If so what do I not have installed that is keeping me from enjoying this video.

Thanks

---

### Post by andrew.46 on 2009-07-22
Hi Uinluan,

> **Uinluan said:**
> I also have tried mplayer and helix and gxine.  These players come up with an error that states "Could not determine type of stream" 

Could you run the file from the commandline with the following syntax:

```
mplayer -v *myfile*.m4v
```

and post the command + full terminal output here?

Andrew

---

### Post by Uinluan on 2009-07-22
Here it is I piped it to a text file and attached the file because the output was very verbose. Thanks for looking at this.

---

### Post by HappyFeet on 2009-07-22
Have you tried to play it on another computer? What codecs have you installed?

---

### Post by shirilover on 2009-07-22
Three suggestions:

Use mediainfo ([http://mediainfo.sourceforge.net](http://mediainfo.sourceforge.net)) to find out what codecs the video file actually uses.

Try changing the extension to mp4 and play the file again.

Use mkvtoolnix to create a duplicate of the file in a matroska container, then try playing the file again.

---

### Post by andrew.46 on 2009-07-24
Hi Uinluan,

> **Uinluan said:**
> Here it is I piped it to a text file and attached the file because the output was very verbose. Thanks for looking at this.

Unfortunately the output is not terribly helpful. Can you post this file somewhere?

Andrew

---

