---
title: "Windows Media Audio"
date: 2010-03-15
forum: Multimedia Software
---

### Post by joachim10022 on 2010-03-15
Hi

does anybody know where to get a decoder for .wma files?
I have installed the restricted extras for ubuntu 9.10.
If I want to play a .wma file, it either does not play or it searches for a suitable codec but cannot find one.

Thanks

---

### Post by ron999 on 2010-03-15
Have you tried using VLC media player?

---

### Post by andrew.46 on 2010-03-15
Hi joachim,

> **joachim10022 said:**
> does anybody know where to get a decoder for .wma files?

There are a few varieties of wma all of which can now be played on linux, if not always on the stock offerings from the Ubuntu repositories and not always on 64bit Ubuntu. Do you have a link to this file or can you post it somewhere?

Andrew

---

### Post by basumarmi1510 on 2010-03-15
In this case, I used the VLC media player.......
And it was really beneficiary .

You can also try this one...............

---

### Post by mc4man on 2010-03-15
wma scorecard atm (or thereabouts

32 bit install
wma2 - all players, usually thru libavcodec or a ffmpeg plugin (gstreamer, libxine

wma3 (pro. 9.1, 10)
gstreamer players - technically possible thru w32codecs and gstreamer0.10-pitfdll, probably won't work in karmic though decoding available in lucid thru one of the gstreamer plugins
adding this ppa should enable wma3 in  karmic - *highly recommended*

[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

mplayer, vlc - thru w32codecs or libavcodec with native wmap decoding, no repo or ppa vlc can play atm, must be built.
xine based players - amarok, totem-xine ect. - thru w32codecs, xine-libs 1.18 and higher now provide native wmap decoding, most players will use without the need to rebuild

wma lossless
mplayer thru w32codecs, ( libavcodec should have in the future
vlc thru w32codecs - has limit of single play per vlc instance, will also be avail. thru libavcodec in the future - vlc has to be built 
xine-based - thru w32codecs

wmas (speech, voice
should work in all players thru the gstreamer plugins or w32codecs
vlc and mplayer can now also decode thru libavcodec - not available in repo versions, vlc must be built

64 bit
wma2 - all players

wma3 (ect.
mplayer thru libavcodec - only self built or ppa
vlc thru libbavcodec - must be self built
gstreamer players - in lucid or thru use of above ppa
xine based - with xine-libs 1.18 and higher

wma lossless
atm only with a 32 bit build of a player - mplayer best bet, thru w32codecs
vlc and mplayer (64bit) will benefit from future libavcodec support

wmas - same as above, probably not in xine-based

edit:
once lucid releases I'd ck. and add the above mentioned ppa to keep gstreamer up to date

---

### Post by joachim10022 on 2010-03-16
Thanks so far, but is there support for wma lossless or does anybody know how to convert them to mp3/ogg, etc.?

---

### Post by andrew.46 on 2010-03-16
Hi joachim,

> **joachim10022 said:**
> Thanks so far, but is there support for wma lossless or does anybody know how to convert them to mp3/ogg, etc.?

As mc4man has mentioned above MPlayer can play these files with the w32codecs available to Ubuntu from Medibuntu. So if you have a 32 bit installation of MPlayer you should be right as [this sample]("http://samples.mplayerhq.hu/A-codecs/lossless/luckynight.wma") demonstrates:

```

andrew@skamandros~/samples$ mplayer luckynight.wma 
MPlayer SVN-r30895-4.3.3 (C) 2000-2010 MPlayer Team

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
A:  63.1 (01:03.0) of 60.5 (01:00.4)  5.4% 

Exiting... (End of file)

```

Certainly MPlayer can also convert such a file to wav using syntax such as this:

```
mplayer luckynight.wma -ao pcm:fast:waveheader:file=output.wav
```

and then to mp3 or ogg as you wish, transcode can make this a little easier by using its mplayer import module...

All the best,

Andrew

---

