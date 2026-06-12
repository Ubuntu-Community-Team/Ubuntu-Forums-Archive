---
title: "ffmpeg from subversion"
date: 2010-06-20
forum: Multimedia Software
---

### Post by Tasha Richardson on 2010-06-20
I am trying to install ffmpeg from subversion SVN-r23652 the lastest.FFmpeg installs fine but when i try to convert a youtube to a mp3 it just sets there is there any updates to any of the libs or maybe something i am doing wrong.Thanks

---

### Post by Tasha Richardson on 2010-06-20
now with 23659 it's giving this error at the configure
Unknown option "--enable-libfaad
I looked and i think I'm running the latest libfaad i have 2.7.4 installed.

---

### Post by ron999 on 2010-06-20
There's a pretty good tutorial over on another thread, maybe it will help.
Here:-[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095")
Good luck.
:guitar:

---

### Post by Tasha Richardson on 2010-06-20
well i guess they removed it when i do a ./configure --help and they don't even show it in the list of options.Question is what did they replace it with?

---

### Post by Tasha Richardson on 2010-06-20
Well yet 2 more error's from ffmpeg when i try to encode a you tube to a mp3.
Here is the error's.Going to take someone smarter then me to work this out.

[NULL @ 0x9d9e830][Eval @ 0xbfe3df0c]Invalid chars 'b' at the end of expression '160kb'

[NULL @ 0x9d9e830]Unable to parse option value "160kb"

---

### Post by ron999 on 2010-06-20
Please paste the command that you used.

---

### Post by Tasha Richardson on 2010-06-21
i used winff to encode the you tube file.I looked in the change log here is what it says

> Entries are sorted chronologically from oldest to youngest within each release,
releases are sorted from youngest to oldest.


version <next>:

- WebM support in Matroska de/muxer
- low overhead Ogg muxing
- MMS-TCP support
- VP8 de/encoding via libvpx
- CODEC_CAP_EXPERIMENTAL added
- Demuxer for On2's IVF format
- Pictor/PC Paint decoder
- HE-AAC v2 decoder
- libfaad2 wrapper removed


version 0.6:

I downloaded this version after ffmpeg 0.6 was released so i quess libfaad2 was removed.would this cause my problem?I have version SVN-r23626 and it works fine i was just seeing if they added any new feature's and codec.

thank you

---

### Post by FakeOutdoorsman on 2010-06-23
libfaad support was removed from FFmpeg because the native AAC decoder in FFmpeg can now support HE-AAC v2 making libfaad redundant.

> **Tasha Richardson said:**
> Well yet 2 more error's from ffmpeg when i try to encode a you tube to a mp3.
Here is the error's.Going to take someone smarter then me to work this out.

[NULL @ 0x9d9e830][Eval @ 0xbfe3df0c]Invalid chars 'b' at the end of expression '160kb'

[NULL @ 0x9d9e830]Unable to parse option value "160kb"

I'm not sure what your command looks like, but try it without the "b", so for example, instead of *-ab 160kb*, try *-ab 160k*. Or you could use FFmpeg directly instead of WinFF:
```
ffmpeg -i input.flv -acodec libmp3lame -aq 4 output.mp3
```
or
```
ffmpeg -i input.flv -acodec libmp3lame -ab 160k output.mp3
```

---

### Post by Tasha Richardson on 2010-06-24
Thank you so so much FakeOutdoorsman 

I have been fighting with this for days.Winff has not updated there preset commands I'm guessing.Ubuntu is so new to me sometimes i get turned around.But I'm learning.

---

### Post by FakeOutdoorsman on 2010-06-25
> **Tasha Richardson said:**
> Thank you so so much FakeOutdoorsman 

I have been fighting with this for days.Winff has not updated there preset commands I'm guessing.Ubuntu is so new to me sometimes i get turned around.But I'm learning.

I'm glad it's working for you. FFmpeg development is so active that the WinFF presets may get stale once in a while...and then there are the multiple versions of Ubuntu to support with their various versions of FFmpeg.

---

