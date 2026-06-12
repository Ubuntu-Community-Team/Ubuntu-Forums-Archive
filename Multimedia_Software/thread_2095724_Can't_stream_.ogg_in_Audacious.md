---
title: "Can't stream .ogg in Audacious"
date: 2012-12-17
forum: Multimedia Software
---

### Post by Bill Tetzeli on 2012-12-17
Hey all,

   This is a new problem I've come across in Ubuntu 12.10, which I'm running on a System 76 Pangolin Performance (p9) laptop.  I'm using audacious 3.2.3.  When I click on a streaming link at [http://wtju.net/vault]("http://wtju.net/vault") audacious gives me the following message:

```
No decoder found for http://wtju.net:8000/92306f002ad401300776.ogg.
```

However, when I go to the Downloads folder and double click on the downloaded .pls file audacious starts streaming no problem.  This happens in both Chrome and Firefox, both of which are supposed to open the .pls in audacious by default.

libogg0 is installed on my system, as well as all the standard third party and multimedia software (I checked both of those options when I reinstalled Ubuntu 12.10 as part of making a dual boot with Windows).  The relevant .pls and .ogg options are checked on in audacious's preferences, so I'm a bit at a loss as to what's going on.

Any help appreciated, and thanks in advance.

Bill

P.S. This is not a problem at all in Ubuntu Studio 12.04, which I run on two other laptops.

---

### Post by andrew.46 on 2012-12-18
That particular stream seems broken, another one I selected at random seems to work fine:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer 'http://wtju.net:8000/dd580b202b3b01300776.ogg'[/COLOR]**
MPlayer SVN-r35687-4.7.1 (C) 2000-2012 MPlayer Team

Playing http://wtju.net:8000/dd580b202b3b01300776.ogg.
Resolving wtju.net for AF_INET6...

Couldn't resolve name for AF_INET6: wtju.net
Resolving wtju.net for AF_INET...
Connecting to server wtju.net[199.111.170.5]: 8000...

Name   : WTJU-FM Broadcast Archive
Genre  : World
Website: http://wtju.net/
Public : no
Cache size set to 320 KBytes
Cache fill: 16.12% (52824 bytes)   

[Ogg] stream 0: audio (Vorbis), -aid 0
Ogg file format detected.
Clip info:
 Title: Reggae Vibrations,2012-12-15T12:00:00-05:00
 Creation Date: 2012-12-15T12:00:00-05:00
Ogg : bad packet in stream 0
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.80.100 (internal)
AUDIO: 44100 Hz, 2 ch, floatle, 192.0 kbit/6.80% (ratio: 24000->352800)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  63.6 (01:03.6) of 0.0 (unknown)  0.2% 1% 

```

But I admit I did not try to play one of these streams in a gui directly from a browser...

---

### Post by Bill Tetzeli on 2012-12-19
Well, I just tried streaming from the WTJU vault on the following three computers:

Acer Aspire One running Ubuntu Studio 12.04 (32-bit) - streams opened automatically in audacious from both Chrome and Firefox

Acer Aspire One running Windows 7 (64-bit) - streams open automatically in Winamp from Firefox, Chrome does nothing (possibly a separate issue)

System 76 Pangolin Performance (p9) running Ubuntu 12.10 (64-bit) - Chrome gives me the same error message:

No decoder found for [http://wtju.net:8000/c206f6902c8001300776.ogg](http://wtju.net:8000/c206f6902c8001300776.ogg).

Firefox also gives similar error messages, but if I double-click on the .pls playlist in the download window it'll stream.


My uneducated guess is it has something to do with gstreamer, which I've been reading a lot of complaints about in Ubuntu.  I've also been having problems using SoundConverter to decode from flac to WAV, again getting gstreamer error messages.  Neither of the laptops running 12.04 have this problem, but gstreamers been giving me nothing but heartache in 12.10.  I might try backing up my system and testing out either Ubuntu Studio 12.04 or vanilla Ubuntu 12.04 (since Studio was giving me some problems on the System 76 the first time I tried) on my laptop.

(sigh!)

I don't want to spend time making my computer work.  I want to spend time using it.  It's why I love Win 7, loathe Win 8 and have been putting up with the trials of Linux, convinced that the MS landscape is only going to get worse.  But that's what I thought when Vista came out, and Win 7 turned out as good as Vista was bad.  I wish MS would quit doing the turkey-jewel-turkey-jewel back and forth.

I think my only options are the following:

1. find solutions to most of my Linux problems soon and get on with life
2. Go back to Win 7 until it's no longer supported in 2019, trusting that by then MS will recover from its insanity
3. Cave, endure my brothers' gloating and get a Mac


Number 4, endure years of Linux hell in fear of a worse one awaiting me in Windows 9 or 10, is not an option.  I don't want my tombstone to read, "He finally mastered Linux".  Life's too short.

Number 5 - "Don't sweat the small stuff" - is also on the list.  Maybe should be at the top.

---

### Post by mc4man on 2012-12-20
For some reason your experience with that site in 12.10 seems to be the exception. Can say that here all the active streams in the vault work fine in audacious directly from FF, both in 12.10 & win7

Can also say that every time you post a  [http://wtju.net:](http://wtju.net:)..... link it doesn't work anywhere with anything
I guess if inclined to post another example from the vault use the stream name rather than the link from the .m3u

---

### Post by Bill Tetzeli on 2012-12-20
> **mc4man said:**
> For some reason your experience with that site in 12.10 seems to be the exception. Can say that here all the active streams in the vault work fine in audacious directly from FF, both in 12.10 & win7

Can also say that every time you post a  [http://wtju.net:](http://wtju.net:)..... link it doesn't work anywhere with anything
I guess if inclined to post another example from the vault use the stream name rather than the link from the .m3u

Hmmm.. now that's a head scratcher.  As far as the link goes, that was automatically hyperlinked when I pasted the message in.  Sorry I didn't catch that.

The bright side is that one of the problems I thought was related to gstreamer, the inability of Sound Converter to decode from .flac to .wav, was actually caused by Sound Recorder's dodgy .flac encoding.  Turns out Sound Converter works fine on healthy .flacs.  Also turns out Audacity does stream capture much better and saves as canonical .wavs that don't have to be decoded in the first place, and can be tracked within the program itself.  Would have used that as a first choice, but didn't realize it was much easier to do in Linux than Windows.  THAT is a grownup program, not some hobby like Sound Recorder (which has been dodgy in any distro I've used).

---

### Post by mc4man on 2012-12-20
If you have use for an audio recorder that actually works well then ck. out
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)
He's not going to develop anymore but is hoping someone picks up on
[http://ubuntuforums.org/showthread.php?t=2091069](http://ubuntuforums.org/showthread.php?t=2091069)

As it now stands it works quite well thru 12.10 & has numerous options, ect.
(though may require a little time learning how to use depending on what one wants from it...

---

### Post by Bill Tetzeli on 2012-12-20
I downloaded audio-recorder, and while it is definitely an improvement over Sound Recorder the .flacs don't decompress to canonical .wavs, and can't even be made canonical by exporting them in Audacity to a new .wav file (which worked for .wavs decompressed from Sound Recorder's .flacs) or stripped in Trader's Little Helper run under Wine.  Thanks for the suggestion, but I'm going to stick with Keep It Simple, Stupid.  Audacity's already got me covered for the recording, tracking and saving in canonical format.  Looks like the best bet.

---

