---
title: "extracting information from media stream"
date: 2009-01-08
forum: Multimedia Software
---

### Post by alxlabs on 2009-01-08
I need to extract information (like station name, bitrate etc) from the media stream ie [http://www.z1035.com/z1035.asx](http://www.z1035.com/z1035.asx) in the console, some kind of command line based tool. Any suggestions?

---

### Post by andrew.46 on 2009-01-09
Hi alxlabs,

> **alxlabs said:**
> I need to extract information (like station name, bitrate etc) from the media stream ie [http://www.z1035.com/z1035.asx](http://www.z1035.com/z1035.asx) in the console, some kind of command line based tool. Any suggestions?

You mean this info:

```

[asfheader] Audio stream found, -aid 1
Clip info:
 name: Z103.5 FM, Toronto
ID_CLIP_INFO_NAME0=name
ID_CLIP_INFO_VALUE0=Z103.5 FM, Toronto
 author: Today's HIT Music
ID_CLIP_INFO_NAME1=author
ID_CLIP_INFO_VALUE1=Today's HIT Music
 copyright: (c) 2008 Evanov Radio Group
ID_CLIP_INFO_NAME2=copyright
ID_CLIP_INFO_VALUE2=(c) 2008 Evanov Radio Group
ID_CLIP_INFO_N=3
ID_FILENAME=http://69.90.16.42:81/z103.5_fm
ID_DEMUXER=asf
ID_AUDIO_FORMAT=353
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=2133437386.00
ID_SEEKABLE=0
ID_CHAPTERS=0

```

This was extracted from mplayer:

```
$ mplayer -identify -playlist http://www.z1035.com/z1035.asx
```

If you wanted to use this in a script you could block actual playback and still get the required information by using something like:

```
$ mplayer -vo null -ao null -frames 0 -identify -playlist http://www.z1035.com/z1035.asx

```

Hope this is what you were after? There may very well be better tools to gain more information but I have not looked at this before.

Andrew

---

