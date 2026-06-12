---
title: "FLAC or Vorbis, and what's the quality setting?"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by Aleksandersen on 2007-01-10
Hi,

I am just currios about the "quality" parameter in FLAC and Vorbis. What is it and what should I have it set on to get the best audio with the smallest files in both formats?

I see FLAC goes between 0 and 8, and Vorbis between -1 and 10. What quality in FLAC equals 7 in Vorbis, and what quality equals 3 in FLAC? (just so I can get some perspective)

---

### Post by whatever on 2007-01-10
as FLAC is lossless compression, you will always get perfect (!) quality. the settings only affect the compression time and filesize.
Vorbis is lossy, so smaller filesize is achieved by lower quality. i suggest you use 6 or higher for good quality.

---

### Post by kd7swh on 2007-01-10
Well Vorbis is a lossy format and FLAC is a "loss-less" format so comparing their scales doesn't really work well. 

It has been a long time since I have worked with flac files so I can't really anwser your question without looking around for some more information but if I recall correctly flac has pretty high bitrates 500 - 2000kbps. These are much higher quality than most Vorbis files. 

When I work with Vorbis I use set ABR bitrates, I don't use the VBR scale that you referred to.
So I set the encoder to 128, 192, 256, or 320kbps for example, making these files smaller than flac but lossy in quality.

For some people, a 320kbps Vorbis sounds the same as a 400 - 500kbps flac file. Telling the difference can be hard without good speakers. 


Check out this link:
[http://www.hydrogenaudio.org/forums/lofiversion/index.php/t37990.html](http://www.hydrogenaudio.org/forums/lofiversion/index.php/t37990.html)

They are talking about this comparison.

Involarius says:
> 
"Vorbis -q 10 gives you a nominal bit rate of 500 kbit/s, scratching the lower regions of what you get with FLAC."

This sounds about right.

---

### Post by Aleksandersen on 2007-01-10
OK, thanks a lot! :)

But one thing I do not understand is the FLAC "compression level", or sometimes refereed to as just "quality"... I cannot make heads or tails of it (literally!)

---

### Post by yabbadabbadont on 2007-01-10
As stated above, FLAC is a lossless format, so when it is played back, it will sound identical to the original CD.  The quality parameter only affects how long it takes to create the flac file in the first place.  Higher settings mean that it will take longer to create the flac file, but the final file will be smaller.  Playback of the file will be the same regardless of the setting used.

```
/home/bubba $ flac
===============================================================================
flac - Command-line FLAC encoder/decoder version 1.1.2
Copyright (C) 2000,2001,2002,2003,2004,2005  Josh Coalson

This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.
===============================================================================

This is the short help; for all options use 'flac --help'; for even more
instructions use 'flac --explain'

To encode:
  flac [-#] [INPUTFILE [...]]

  -# is -0 (fastest compression) to -8 (highest compression); -5 is the default

To decode:
  flac -d [INPUTFILE [...]]

To test:
  flac -t [INPUTFILE [...]]

```

---

### Post by em3raldxiii on 2007-01-10
Just to hammer it all home, one more time, milk it to death, all the clichés, brief summary:

OGG:  Lossy compression, which means you lose some quality.  The higher the compression, the more you lose, but the smaller the file will be.  So an OGG of 10 will be highest OGG quality, largest file, quickest to encode.  OGG of -1 will be UBER small, take a little longer to encode, and be the lowest quality.

FLAC:  Is *always* perfect quality.  The numbers *only* refer to how long it will take the file to be packed, and how small the final file will be.  The smallest possible FLAC file will still probably be much larger than an OGG file, but it's usually worth it.  As far as I know, there is no reason NOT to use FLAC except for the slight increase in time it takes to squish 'em.

---

### Post by Aleksandersen on 2007-01-10
A album encoded with FLACK -8 ended up being a little over 500 MB, but the same album in Vorbis -9 where a little under 200 MB. I think I will do just fine with Vorbis! ^^ I do not think I could hold my CD collection in FLACK.

---

### Post by Enverex on 2007-01-10
FLAC. No K.

It's for audiophiles like me that want to keep everything in archival quality or are paranoid that "that sound" is caused by compression. It's also useful if you need something to make copies from (transcoding to use on mobile devices or something) as Lossy to Lossy tends to degrade very quickly.

---

### Post by Aleksandersen on 2007-01-10
It does get a little out of perspective when each song is about 25 MB... You really cannot store that on most "mobilde devices" anyways.

---

### Post by yabbadabbadont on 2007-01-10
> **Aleksandersen said:**
> It does get a little out of perspective when each song is about 25 MB... You really cannot store that on most "mobilde devices" anyways.

I think you misunderstood, (or I misunderstood your response).  He, like me, has a perfect copy of his music on his desktop machine in flac format.  (some compression, but perfect quality)  When he (or I) needs to copy it onto a mobile device, it is converted from flac to a lossy format (ogg, mp3, ...) that is supported by the device.  As long as you start with a perfect copy (flac), you can convert it to whatever format/quality settings you like for your portable device and it will be the same as if you had created that copy from the original CD.  You won't get quite as good results if you do the same from a high quality ogg or mp3 file as they are not perfect copies of the original CD.

(I guess that horse has been bludgeoned to death... :D)

---

