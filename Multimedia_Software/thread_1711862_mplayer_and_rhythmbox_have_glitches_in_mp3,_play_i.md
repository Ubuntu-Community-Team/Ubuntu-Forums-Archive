---
title: "mplayer and rhythmbox have glitches in mp3, play is flawless"
date: 2011-03-21
forum: Multimedia Software
---

### Post by dev.null on 2011-03-21
I have a couple mp3s that play horrible in mplayer and rhythmbox - they have these sound glitches like back in the day when a cassette tape would go bad.

But when I play them from "play" (cmd line) they are flawless.

I've even tried using ffmpeg to convert them to wav or "re-tune" them as mp3, but the result is the same.

I know "play" uses sox, so I'm sure that's related.

I would stick w/ "play", but the problem is there aren't any keystrokes to pause, rewind, etc... and this is instructional audio and I often need to pause to write notes.

Ideas?

---

### Post by andrew.46 on 2011-04-02
Can you post one of these problematic mp3s online somewhere?

Andrew

---

### Post by dev.null on 2011-04-02
> **andrew.46 said:**
> Can you post one of these problematic mp3s online somewhere?

Andrew

It's copyrighted and a friend of mine... I don't feel 100% comfortable posting a public link to it, but I will give you the link in a PM (sent).

---

### Post by andrew.46 on 2011-04-02
Thanks for the link and yes I can hear the rather odd distortion which occurs periodically throughout this recording. One solution I have found with MPlayer is to use mpg123 rather than the default mp3lib to decode the sound. I am temporarily between Ubuntu installations at the moment so I am not sure if the repository MPlayer has this capability (perhaps it is a feature of later versions), it can be tested as follows:

```

andrew@skamandros~/Desktop$**[COLOR="Red"] mplayer -ac help | grep 'mpg123'[/COLOR]**
mpg123      mpg123    working   MPEG 1.0/2.0/2.5 layers I, II, III

```

and then automagically loaded by adding the following to ~/.mplayer/config:

```

[extension.mp3]
profile-desc="profile for .mp3 files"
ac=mpg123

```

Then you will see the following on playback:

```

andrew@skamandros~/Desktop$ mplayer kimroachtactics.mp3 
MPlayer SVN-r33187-4.5.2 (C) 2000-2011 MPlayer Team
**[COLOR="Red"]Loading extension-related profile 'extension.mp3'[/COLOR]**

Playing kimroachtactics.mp3.
Audio only file format detected.
Load subtitles in ./
==========================================================================
Forced audio codec: mpg123
Opening audio decoder: [mpg123] MPEG 1.0/2.0/2.5 layers I, II, III
AUDIO: 8000 Hz, 2 ch, s16le, 64.0 kbit/25.00% (ratio: 8000->32000)
**[COLOR="Red"]Selected audio codec: [mpg123] afm: mpg123 (MPEG 1.0/2.0/2.5 layers I, II, III)[/COLOR]**
==========================================================================
AO: [oss] 8000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  12.6 (12.5) of 3259.0 (54:19.0)  0.1% 

```

and the distorion is gone; or you can simply test from the commandline:

```
mplayer -ac mpg123 kimroachtactics.mp3 
```

If this is not possible you should be able to experience flawless playback with mpg123 itself which I believe is available from the repository, something like:

```
mpg123 --control kimroachtactics.mp3 
```

Very odd distortion in some players though, it could probably be cleaned out but this goes way beyond my skills :(.

Andrew

---

