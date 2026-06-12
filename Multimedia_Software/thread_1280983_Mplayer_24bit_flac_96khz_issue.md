---
title: "Mplayer 24bit flac 96khz issue"
date: 2009-10-02
forum: Multimedia Software
---

### Post by edwardecl on 2009-10-02
I was attempting to set up ps3mediaserver to serve some 24bit FLACs, but when played back the track played but skipped as if you are fast forwarding it... and only at loud/complex parts of the track which is strange the quieter bits don't skip?!?

So I then tried to play the flac in mplayer directly and it did the same thing... 16bit flacs decode and play fine however.

Does anyone know how to fix this, there is nothing wrong with the flacs as they playback on other players fine, and even on mplayer on windows. I need mplayer as ps3mediaserver uses it to decode the flac to transcode to PCM.

---

### Post by mc4man on 2009-10-02
I don't have any issue with mplayer playing hi-res flac's (96-192k, 2-6 ch
( am using karmic now with an -ao pulse, but also work fine on hardy with -ao alsa

Maybe play one with mplayer from the cli and use a -v option and see what shows up
mplayer -v /path/to/flac

---

### Post by edwardecl on 2009-10-02
Thanks for the reply, OK that helped a bit I get a billion errors

[flac @ 0x8972330]FRAME HEADER not here7.5%
[flac @ 0x8972330]decode_frame() failed
lavc_audio: error

I get loads of these...

But I know for a fact the FLAC files are fine... it's doing it on all the 24bit FLACs I have not just one. Like I say I can play the exact same thing from the same location on mplayer on windows just fine (using vmware). Could it be the version of player itself that is bugged or ffmpeg?, I have the latest version from the repo "MPlayer 1.0rc2-4.3.3" which is actually newer than the version I'm using on windows, same with ffmpeg "FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6"

I am really confused :(.

---

### Post by edwardecl on 2009-10-02
Oh I also have a mixture of other errors too

[flac @ 0x8972330]FRAME HEADER not here7.5%
[flac @ 0x8972330]invalid sample size code (7)
[flac @ 0x8972330]decode_frame() failed
lavc_audio: error

[flac @ 0x8972330]FRAME HEADER not here7.3%
[flac @ 0x8972330]unsupported channel assignment 3 (channels=2)
[flac @ 0x8972330]decode_frame() failed
lavc_audio: error

The FLAC is only 2 channels so why does it think it's 3 channels at one point? Someone else has go to have this bug it's too strange just for me to have it.

---

### Post by andrew.46 on 2009-10-03
Hi edward,

> **edwardecl said:**
> Thanks for the reply, OK that helped a bit I get a billion errors

Is it possible to post one of these files somewhere? It would be interesting to run a newer version of MPlayer over one...

Andrew

---

### Post by edwardecl on 2009-10-03
From what I've been reading in places I think it's a bug is with ffmpeg specificity the flac decoder in libavcodec not supporting headers over 64kb? not sure if this is true or not.

From what I can tell if I uninstall ffmpeg mplayer will supposedly use libflac instead which works fine, but if I uninstall that VLC will get removed and the purpose for having the media server (which uses VLC as well) will be lost.

Mplayer had a codecs.conf but it seems to have been made obsolete and now there is no way of specifying a codec to use. So I am pretty much stuck here I can't think of anyway of getting round this...

Unless anyone knows how to force mplayer to use libflac?

Or someone has modified ps3mediaserver not to use mplayer to decode flacs ^^. Or better still someone fixes libavcodec.

---

### Post by scarf on 2010-03-10
i'd be interested in figuring this out as well.

mplayer has an -ac flag you can use to force the audio codec.  however, i cannot figure out how to get it to use libflac.  in fact, libflac is not even listed as a codec when i use 'mplayer -ac help'.  do you have it listed?  ffflac is the only pertinent option i have.

what are you talking about when uninstalling ffmpeg, libavcodec-unstripped-52?  i tried removing that and, as you said, it remove vlc (along with some other things).  however, when i go to try mplayer again it still indicates it is using the ffflac decoder.

---

### Post by andrew.46 on 2010-03-10
Hi scarf,

> **scarf said:**
>   in fact, libflac is not even listed as a codec when i use 'mplayer -ac help'.  do you have it listed?  ffflac is the only pertinent option i have.

I am ready to be proved wrong but I believe it is not possible to compile against an external flac decoder in MPlayer. 

All the best,

Andrew

---

### Post by mc4man on 2010-03-10
here are some flac samples, I believe on my other pc have some others
(mplayer plays them all (96000Hz, 192000Hz, 88200Hz 6ch

[http://www.linnrecords.com/linn-downloads-testfiles.aspx](http://www.linnrecords.com/linn-downloads-testfiles.aspx)

---

