---
title: "Getting Video/Audio to Sync"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by troy1of2 on 2007-10-16
After much tinkering around, searching the forums, etc. I finally came up with some options that covert an FLV to an AVI that my Samsung HT-Q45 Home Theater system will play without giving me the Unsupported Codec error. The only problem is, the audio and video is way out of sync. Now I'm a newbie at this stuff so please bear with me but can anybody tell me what I might be able to do to get the audio and video better synced?

Here's what I am converting with:

mencoder -idx input.flv -ovc xvid -xvidencopts bitrate=4500 -oac mp3lame -srate 44100 -o output.avi

---

### Post by yabbies on 2007-10-16
From Larry Grover with a few tweaks of my own.

you'll need: mplayer, mjpegtools, ffmpeg, tovid.

convert your avi to mpeg workable dvd

```
tovid -wide -in ORIGINAL AVI.avi -out NEW NAME
```

You need to get the audio from your original video file

```
mplayer -ao pcm -vo null -vc ORIGINAL AVI.avi
```

The result will be a new file called "audiodump.wav" the next
command will convert it to MP2 format
```

ffmpeg -ab 224 -ac 2 -ar 48000 -i audiodump.wav audiodump.mp2
```

NOTE: you should be able to substitute "mp3enc" for "ffmpeg", but I
haven't tested it, so I can't verify that it works; mp3enc is part of
the mjpegtools package, and would allow you to avoid installing an
extra package (the ffmpeg package).

Finally, multiplex the new video and audio files:

```
mplex -f 8 -o ready-to-master.mpg out.m2v audiodump.mp2
```

Now to make a working DVD 

```
makexml ready-to-master.mpg -out NEWNAME
```

You'll now have a an xml of whatever name you chose.
Take that xml and you can burn to a DVD by using

```
makedvd -burn NEWNAMEXML.xml
```

hope that works for you, let me know

---

### Post by troy1of2 on 2007-10-16
Thank you yabbies. I don't have a DVD burner at the moment but later on if I decide to get one I'll definitely give this a try. Right now, all I am doing is putting a few short AVI files on a flash drive and playing them on the Home Theater for the kids.

---

### Post by GrouchoMarx on 2007-10-17
Although this doesn't solve the actual encoding problem, if you just want to re-sync the audio then you can try doing so with Avidemux in simple copy mode. It should be a trivial process of opening the file (I don't think you need to unpack it), setting the audio shift in milliseconds, and then saving the file.

[http://www.avidemux.org/admWiki/index.php?title=Audio_filters]("http://www.avidemux.org/admWiki/index.php?title=Audio_filters")

Note: "If you are editing a file with variable bitrate audio, run Audio->Build VBR Time Map before you do any editing. Otherwise your audio will be out of sync."

---

### Post by troy1of2 on 2007-10-17
> **GrouchoMarx said:**
> Although this doesn't solve the actual encoding problem, if you just want to re-sync the audio then you can try doing so with Avidemux in simple copy mode. It should be a trivial process of opening the file (I don't think you need to unpack it), setting the audio shift in milliseconds, and then saving the file.

[http://www.avidemux.org/admWiki/index.php?title=Audio_filters]("http://www.avidemux.org/admWiki/index.php?title=Audio_filters")

Note: "If you are editing a file with variable bitrate audio, run Audio->Build VBR Time Map before you do any editing. Otherwise your audio will be out of sync."

That looks pretty promising. I'll give it a try. Thanks Groucho. BTW, I love your movies!

:lolflag:

---

