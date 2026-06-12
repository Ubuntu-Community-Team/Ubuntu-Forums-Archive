---
title: "SUPER equivelant in Linux?"
date: 2010-12-20
forum: Multimedia Software
---

### Post by zer010 on 2010-12-20
I have known about a handy program called SUPER by e-rightsoft(sp?).  I was thinking that since it's nothing more than a front-end to quite a few common tools found in Linux,[COLOR=#000070][SIZE=2]
   [/SIZE][/COLOR]> [COLOR=#000070][SIZE=2] SUPER © Simplified Universal Player Encoder & Renderer.
    A GUI to FFmpeg,  MEncoder,  MPlayer,  x264,
    MusePack, Monkey's audio, Shorten audio, TAK audio, True audio,
    WavPack, the libavcodec library & the theora/vorbis RealProducer's    plugIn[/SIZE][/COLOR]I figured there has to be a version for Linux. I looked in Synaptic...nothing.  I went to their website....only downloads for Windows!  So I searched to see if there was anything like it and I found ONE thread here: [http://ubuntuforums.org/showthread.php?t=399804](http://ubuntuforums.org/showthread.php?t=399804) .  It suggested " [Vive]("http://vive.sourceforge.net/"), [Sive]("http://sive.sourceforge.net/"), or [thinliquidfilm]("http://thinliquidfilm.org/")", but these are only encoders to work with ipods. And if you read the thread, SUPER works in a VM(which I don't have setup)  and is a disaster in Wine(as I've found most things are). 

Is there nothing as robust as SUPER for Linux?  One of the operations it was particularly useful for was pulling audio from an A/V file.  I wouldn't even know where to begin to do this in the CLI. Any ideas or suggestions?

---

### Post by cchhrriiss121212 on 2010-12-20
> One of the operations it was particularly useful for was pulling audio  from an A/V file.  I wouldn't even know where to begin to do this in the  CLI. Any ideas or suggestions?
Avidemux is good for this:
[http://techblissonline.com/rip-audio-from-video/](http://techblissonline.com/rip-audio-from-video/)

---

### Post by wojox on 2010-12-20
Try VLC. All SUPER is is a front end. ;)

---

### Post by zer010 on 2010-12-20
I have VLC and I have never seen the options to do the things that SUPER does. It might only be a front-end, but it puts all kinds of tools and options in one easy to understand place.  Hell, I couldn't get VLC to recognise a radio stream...

Avidemux(sp?) would do that I guess, but that's only one tiny part of what SUPER can do. 

I wouldn't mind knowing how to do everything SUPER does via command line, but I'm sure it'll get a little cryptic getting into some of the functions.  Any CLI A/V How-To's?

---

### Post by zer010 on 2010-12-20
Screw it, I'll just treat A/V like games and do the work in Win.... I already have a hodge-podge of A/V apps installed in Ubuntu for a few "simple" tasks.  I just hate having to restart or eat up HDD space for a VM.

---

### Post by sisco311 on 2010-12-20
Check out mplayer's home page. Maybe you find a good (GUI) frotend for ffmpeg, mencoder, mplayer...

[http://www.mplayerhq.hu/design7/projects.html](http://www.mplayerhq.hu/design7/projects.html)

---

### Post by wojox on 2010-12-20
Also try Handbrake. It all depends on what you want to do.

---

### Post by markthekdeguy on 2010-12-20
WinFF is what you need.

hope you've got the Medibunti repo enabled.

WinFF (a Gui frontend for FFMpeg) is handy.

pretty much all videos can be transcoded to and fro,

even .flv files can be converted to MPG of just to mp3 or ogg.

some obscure samr audio codecs dont work properly 

these are found sometimes in the occasional cell phone video/audio track)

But if u got Firefox, and FFmpeg - suggest you try the popular

'video download helper' extension. this adds an icon in firefox that

spins when playing streamed video, allows it to be downloaded in browser

then, if you enable 'conversion' and set even a (already built-in) default rule,

it'll d/load, say, a youtube clip, ask you to choose which quality, and convert

it to mpeg, avi, audio etc etc all in one or two simple mouse clicks.

have a play :)

Mark

---

### Post by zer010 on 2011-02-21
I appreciate the tips, but after some more reading I was able to get a good mp3 from a flv.  It was unbelievably easy too, but I'm sure some more options could be used to get a better result. 
```
ffmpeg -i input.flv output.mp3
```Easy peasy!

---

