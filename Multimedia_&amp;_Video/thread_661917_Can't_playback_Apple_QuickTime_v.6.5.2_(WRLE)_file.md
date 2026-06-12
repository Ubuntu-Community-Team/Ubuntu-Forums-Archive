---
title: "Can't playback Apple QuickTime v.6.5.2 (WRLE) file"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by Major_Kong on 2008-01-08
I'm having some trouble playing back a .mov file, if i open it with totem, i get the "plugin video/x-gst-fourcc-WRLE decoder" missing error. If i open it with mplayer i get a "Don't know how to decode depth 24." error.

Any ideas ? 


PS: I'm running Ubuntu 7.10 64bit

---

### Post by Major_Kong on 2008-01-08
No ideas ?

---

### Post by philc on 2008-01-09
> **Major_Kong said:**
> No ideas ?

My only idea is that you're missing codecs to play this file. I don't specifically know if this will fix your problem, as I don't have a QT 6.5 WRLE file to test, but you could try enabling all the Gstreamer plugins - good, bad and ugly. I believe they're in the Universe repository.

---

### Post by Major_Kong on 2008-01-09
They're already installed.

---

### Post by philc on 2008-01-09
OK, so from what I can figure out, WRLE files use the QuickTime Bitmap codec.

I believe FFmpeg will supports bmp codec.

While FFmpeg is in the repositories, I have [installed from source]("http://slashdot.org/~PhillC/journal/190344") and enabled a number of external libraries.

By typing > ffmpeg -formats at the command prompt you will be returned a long list of containers and codecs supported by the version of FFmpeg you have installed.

One line of my version says:

> DEV bmp

D = decode
E = encode
V = video

So, hopefully FFmpeg will be able to decode your WRLE file. Unfortunately I don't see a WRLE extension in the list of supported containers. Maybe try changing the file extension to MOV.

Anyway, you might try using FFmpeg to convert your file to something else that you can view. Or I know GStreamer now has an FFmpeg plugin. You could try installing this and then attempt playback with Totem.

I'm really just guessing here and trying to come up with some ideas for you.....

---

### Post by Major_Kong on 2008-01-09
Tried ffmpeg, got the same error that mplayer gave me (which makes sense considering mplayer uses libavcodec too).

And i already had installed the gstreamer-ffmpeg plugin.

Thanks for the help, anyway.

---

