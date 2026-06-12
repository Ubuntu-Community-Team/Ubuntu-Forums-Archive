---
title: "Stubborn Codec"
date: 2009-03-07
forum: Multimedia Software
---

### Post by charlie-foxtrot on 2009-03-07
I'm having some issues playing a wave file, and I'm not sure where to get a codec for "audio format 0x42". This file came from a VoIP system. I've been doing some research, and it might be the a form of the G.723 (42) codec, but I can't find anywhere to download that. 

The file plays fine on my Windows computer, but it won't play on any other platform. Windows refers to the codec as Intel G.723 (42). 

> Player SVN-r28871-4.0.1 (C) 2000-2009 MPlayer Team

Playing file.wav.
Audio only file format detected.
==========================================================================
Cannot find codec for audio format 0x42.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video


Exiting... (End of file)


I'd really appreciate help with this.

---

### Post by wolfen69 on 2009-03-07
have you installed w32codecs?

---

### Post by charlie-foxtrot on 2009-05-28
w32codecs was installed, but even they were unable to do the trick. 

UPDATE: The codec was G.723.1, which is used mostly in VoIP systems. There is no way to play it on non-Windows operating systems. According to [Wikipedia]("http://en.wikipedia.org/wiki/G.723.1"), the codec is protected by patent laws until 2014. I'm sure that ffmpegx and the other major packages will support this codec once the patents expire. 

For now, my solution is to move the VoIP system to the more standard G.711 codec. 

Hope this helps anyone else having this problem.

---

### Post by hannounest on 2010-05-11
hi
thanks for you
me i have to use G711 but there is no install for it

---

