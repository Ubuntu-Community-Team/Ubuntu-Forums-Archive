---
title: "No sound in SMPlayer, but fine in MPlayer."
date: 2009-04-13
forum: Multimedia Software
---

### Post by Sarteck on 2009-04-13
When trying to play a MPEG file in SMPlayer, I get the following error (from the logs):

[18:37:54] MplayerProcess::parseLine: 'Forced audio codec: wma9dmo'
[18:37:54] MplayerProcess::parseLine: 'Cannot find codec for audio format 0x50.'
[18:37:54] MplayerProcess::parseLine: 'Read DOCS/HTML/en/codecs.html!'
[18:37:54] MplayerProcess::parseLine: 'Audio: no sound'

And no sound is produced (but video is fine).


Playing it in MPlayer from the terminal yields this:

Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 224.0 kbit/15.87% (ratio: 28000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)

And the video/audio is fine.



Naturally, I assumed that the audio codec was the problem, but it seems like no matter how I change it, it doesn't seem to move from 'wma9dmo'.  I even tried to add (in the Advanced Options under the Audio bit), "ac alsa,oss,mp3,mp3lib" (just trying to cover all bases before I posted here), and it didn't seem to consider them at all.  I'm sure it's something I'm doing wrong (after all, it works fine in regular MPlayer), but I don't know what.

Halp, plz?

---

### Post by rvm4000 on 2009-04-13
Uncheck the option "Remember settings for all files" in Preferences -> General and see if it works then.

---

### Post by Sarteck on 2009-04-13
Hey, thanks!  I feel dumb, but at least I can use SMPlayer now.  XD  It worked. :)

---

### Post by inobe on 2009-04-13
xine makes an exceptional kde backend !

xine

xine mozzilla plugin

[IMG]http://wiki.zenwalk.org/images/thumb/1/16/Xine.png/300px-Xine.png[/IMG]

---

### Post by Gallaecio on 2009-12-17
Uncheking that doesn't work for me now.

---

### Post by akshar26 on 2010-05-09
In Smplayer go to Preferences > Audio
and change output driver. 
I am sure this will work.
:)

---

