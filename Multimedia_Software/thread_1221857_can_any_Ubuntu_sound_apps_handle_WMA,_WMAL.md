---
title: "can any Ubuntu sound apps handle WMA, WMAL?"
date: 2009-07-24
forum: Multimedia Software
---

### Post by raymondvillain on 2009-07-24
Jaunty (64 bit).  Sound works fine, just can't play music files from NTFS partition (dual boot machine).

If I boot to windows, I can play FLAC files (after having installed the right CODEC).

Is it possible for Rythmbox, Amarok, etc. (running in Jaunty) to be able to handle WMA and WMAL audio files?

---

### Post by igorzwx on 2009-07-24
**[COLOR=#980101][B][ubuntu]**[/COLOR] Cannot Play DVDs  [/B]
[http://ubuntuforums.org/showthread.php?t=1220584](http://ubuntuforums.org/showthread.php?t=1220584)

---

### Post by raymondvillain on 2009-07-24
I tried all the suggestions in your post, igorzwx, but nothing worked for WMA or WMAL.

---

### Post by igorzwx on 2009-07-24
Some wma are problem indeed.
Perhaps, wma9

---

### Post by igorzwx on 2009-07-24
type on terminal:

ffmpeg -formats

---

### Post by raymondvillain on 2009-07-24
Thanks, igorzwx.

~$ffmpeg -formats

and I get a long list, and down near the bottom are

>  DEA    wmav1           Windows Media Audio 1
 DEA    wmav2           Windows Media Audio 2

Are either of these (wmav1, wmav2) really WMA, or WMAL, by chance?

---

### Post by igorzwx on 2009-07-24
Not, of course.
These ones are very old formats.

Perhaps, you should ask Andrew

---

### Post by igorzwx on 2009-07-24
wma is Windows Media Audio (many different versions)
wmv is Windows Media Video (many different versions)
[http://www.google.com/search?q=ubuntu%20wma%20problem&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=ubuntu%20wma%20problem&ie=UTF-8&oe=UTF-8)

---

### Post by gillmt on 2009-07-24
Would Ogg Convert work?

---

### Post by raymondvillain on 2009-07-24
Thanks for the suggestion, gillmt.  I will give it a try in the next day or so.

---

### Post by martinbaselier on 2009-07-24
according to:
[http://en.wikipedia.org/wiki/Windows_Media_Audio](http://en.wikipedia.org/wiki/Windows_Media_Audio)

The first version of the codec released in 1999 is regarded as WMA 1. In the same year, the bit stream syntax, or compression algorithm, was altered in minor ways and became WMA 2.[12] Since then, newer versions of the codec were released, but the decoding process remained the same, ensuring compatibility between codec version

So you have both wma codecs installed. Only if there's DRM on it, you could have problems. 

For a better multimedia experience I'd advice:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

About wma-losless:
You might have some luck with vlc. It has it's own codecs. As far I could find no linux application has support for it though.

---

### Post by mc4man on 2009-07-24
In a **64 bit ubuntu install** (8.04 thru 9.04 you can playback in several fashions with some possible limitations

wma1, wma2 should be no problem 

wmal (lossless) 
Thru gstreamer apps only with purchase of fluendo windows media pack

Install a 32 bit player and w32codecs

run a 32 bit windows mplayer thru wine

wma3(pro)(wmap)
build and install a wmapro patched mplayer

build a wmapro patched ffmpeg with shared libs and build 0.9x, 1.0.0, or 1.1 vlc patched to decode wma3 thru avcodec (libavcodec

have done all except the fluendo on 8.04 thru 9.04 amd_64 installs (live cds because I actually use i386 hardy

There's a couple of posts about this from a month or so ago
(will edit in if interested, have to run

---

### Post by andrew.46 on 2009-07-24
Hi martinbaselier,

> **martinbaselier said:**
> About wma-losless:
You might have some luck with vlc. It has it's own codecs. As far I could find no linux application has support for it though.

This is not entirely true as the *32bit* svn MPlayer will play these files by using its external windows codecs. For example my favourite wma lossless file:

```
wget http://samples.mplayerhq.hu/A-codecs/lossless/luckynight.wma
```

plays flawlessly under MPlayer:

```

andrew@skamandros~/samples$ mplayer luckynight.wma
MPlayer SVN-r29438-4.2.4 (C) 2000-2009 MPlayer Team

Playing luckynight.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: Lucky Night
 author: Jody Marie Gnant
 copyright: 1995 Sirius Publishing
 comments: 1-minute song sample demonstrating Windows Media lossless audio compression
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 44100 Hz, 2 ch, s16le, 868.7 kbit/61.55% (ratio: 108583->176400)
**[COLOR="Red"]Selected audio codec: [wma9dmo] afm: dmo (Windows Media Audio 9 DMO)[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  22.4 (22.3) of 63.0 (01:03.0)  5.9% 
Exiting... (Quit)

```

But of course the 64bit mplayer does not have easy access to these codecs.

Andrew

---

