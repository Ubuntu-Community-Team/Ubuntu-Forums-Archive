---
title: "Convert 3GP - also xvid?"
date: 2010-10-04
forum: Multimedia Software
---

### Post by PerfectReign on 2010-10-04
I shot some video on my Android-based MyTouch yesterday. (This is also known as the HTC Magic in the parts of the world outside the USA.)

The device takes video in a format called 3GP - [http://en.wikipedia.org/wiki/3GP_and_3G2](http://en.wikipedia.org/wiki/3GP_and_3G2) - which is I guess a format used by phones.

I copied over the video from yesterday and wanted to both re-encode it to something I can use and rotate it, as the video was shot in landscape mode on the phone.  MPlayer won't play the sound but VLC does just fine.

Looking I see there's a few mencoder processes that should do it. I tried Avidmux but it gave me some funky error about video and audio.

I used this command, which worked to move to .avi and rotate, but the resolution was way down and the sound was out of sync:

[B]mencoder -vf rotate=1 -o file_out.avi -oac pcm -ovc lavc source_file_in.3gp
[/B]
I had tried also this command, but got the message that xvid was an unsupported format:

**ffmpeg -i 2010_October_Curly_CG.3gp -f avi -vcodec xvid -acodec mp3 -ar 22050 curly_cg_out.avi**


Doing some searching I found that xvid was a part of libxine, so I dutifully typed: **sudo apt-get install libxine1-ffmpeg**

That told me libxine1 was already installed.

Any ideas?

---

### Post by PerfectReign on 2010-10-04
Oh, by the way.  I checked if mencoder has xvid:



[FONT="Courier New"][B]kai@kai-laptop:~/Videos$ mencoder -ovc help
MEncoder SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   xvid     - XviD encoding
   x264     - H.264 encoding[/B][/FONT]

---

### Post by ron999 on 2010-10-04
Hi
I think that you are on the right track with the **mencoder** command.

But you need to do some research.

Find out what file types are supported by the MyTouch.
For example, avi, mp4.

Find out what video codecs are supported by the MyTouch.
For example, mpeg4, x264.

Find out what audio codecs are supported by the MyTouch.
For example, mp3, aac.


Then find out which audio codecs are available in mencoder.
[FONT="Courier New"]```
mencoder [COLOR="Red"]-avc[/COLOR] help
```[/FONT]

[COLOR="Red"]EDIT[/COLOR]
My bad.
As andrew.46 has said below.
The correct command is:-
[FONT="Courier New"]```
mencoder [COLOR="Red"]-oac [/COLOR]help
```[/FONT]

---

### Post by gordintoronto on 2010-10-04
I find it a lot easier to use winff, aka "video converter." It's really just a GUI for ffmpeg, but it's a lot more user-friendly.

---

### Post by PerfectReign on 2010-10-05
@Ron - thanks. I had tried that - if you notice I ran the avc - help in my post.  In any case...

@gordintoronto - I did originally try using winff. I have ZERO desire to downgrade to the command-line, since this is no longer the 80's.  I couldn't find the right combination, however.

I did eventually get it. I picked XViD fullscreen as teh device preset. That seemed to work. I wanted "MS Compatible AVI" but that was failing.

Got it now!

---

### Post by andrew.46 on 2010-10-09
Hi Perfect,

> **PerfectReign said:**
> @Ron - thanks. I had tried that - if you notice I ran the avc - help in my post. 

Or perhaps *oac* -help:

```

andrew@skamandros~$ **[COLOR="Red"]mencoder -oac help[/COLOR]**
MEncoder SVN-r32449-4.3.3 (C) 2000-2010 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   faac     - FAAC AAC audio encoder

```

:)

Andrew

---

### Post by ron999 on 2010-10-09
It was a typo.
Post now edited.:lolflag:

---

