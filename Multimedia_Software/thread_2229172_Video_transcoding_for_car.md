---
title: "Video transcoding for car"
date: 2014-06-11
forum: Multimedia Software
---

### Post by Alex_K. on 2014-06-11
Hi all,

After numerous tries I decided to ask for community help.

The issue at hand is simple. I'm looking for transcoding a video file to a format that my car video player supports. It's (as it turned out) a chinese FlyAudio, very "well" documented BUT - fortunately, simply by chance, the first video I've tried to play, works. Here's it:

```
user@ubuntu$ avconv -i abc.avi
avconv version 0.8.10-4:0.8.10-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:59:08 with gcc 4.6.3
Input #0, avi, from 'abc.avi':
  Metadata:
    encoder         : VirtualDubMod 1.5.4.1 (build 2178/release)
    title           : abc
    artist          : abc
    copyright       : www.abc.com
    comment         : 13.02.2008
  Duration: 01:27:04.00, start: 0.000000, bitrate: 2391 kb/s
    Stream #0.0: Video: mpeg4 (Advanced Simple Profile), yuv420p, 720x304 [PAR 1:1 DAR 45:19], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
At least one output file must be specified
```

I've been trying to reproduce the encoding above, with none success this far. The files I've produced won't even play. That's my latest example:

```
avconv -i abc.mp4 -vcodec mpeg4 -vtag xvid -acodec ac3_fixed -ab 192k -ac 2 -ar 44100 abc-2.avi

And that's the result:

user@ubuntu$ avconv -i abc-2.avi
avconv version 0.8.10-4:0.8.10-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:59:08 with gcc 4.6.3
Input #0, avi, from 'abc-2.avi':
  Metadata:
    encoder         : Lavf53.21.1
  Duration: 01:04:29.98, start: 0.000000, bitrate: 403 kb/s
    Stream #0.0: Video: mpeg4 (Simple Profile), yuv420p, 480x360 [PAR 1:1 DAR 4:3], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: ac3, 44100 Hz, stereo, s16, 192 kb/s
At least one output file must be specified
ubuntu@ubuntu:/media/B090CC5E90CC2D22$ 
```

Any help in finding the correct avconv command line will be appreciated.

---

### Post by TheFu on 2014-06-11
I don't "know" the answer. Just have some ideas.

Far East is full of VCD/SVCD formats that should be well supported.  ffmpeg has presets for VCD/SVCD formats. I'd try those to start.
Since you already have a working AVI file, you'll note that it is NOT using mp3, but AC3.  Those are completely different audio formats and cannot be mixed as you attempted.

I'd suggest that you locate and read the manual for the device - it will contain the exact video and audio formats supported.  Pay careful attention to CBR/VBR and bitrate limits on both audio and video codecs.

Are you certain that the mp4 file won't play as is?  Have you tried the ipod profile from Handbrake?  It is pretty much the industry standard (regardless of what I think personally).  The iPad profile might work too.

I tried to get more info on FlyAudio - that is just the company - can't look up the product with that alone.

---

### Post by Alex_K. on 2014-06-12
Hello TheFu and thank you for your suggestions.

I've already tried to locate FlyAudio manual but unfortunately all the documentation available does not list the supported formats. In fact, it's more a FAQ listed on site or basic operation manuals found over the Internet. And by the way, from what I've saw on their website and youtube reviews, all their products alike, they only differ in size and logo displayed on startup to match different car manufacturers (mine is Toyota Corolla)

Regarding the container – yes, only AVI is supported by this player. Never mind the fact I didn't find the correct codec setup yet, other video file formats – such as *.mp4 – won't even show up as an available video files on the player, both files I discovered by chance can be played successfully are AVIs and I think I saw in one of the manuals, that this player support AVIs only.

I've tried Handbrake and none of its profiles seems to work, I'll give it another try.

By the way, where did you saw mp3? I think I've selected AC3 for audio in the example I posted above. Anyhow, if it is mp3 that I'm using, any help in establishing the correct command line for AC3 will be appreciated.

Basically, due to lack of manual, I'm trying the reproduce the codecs and their setup from 2 files that are played, such as the one I've posted above. The only difference I notice this far (besides mp3-ac3 as TheFu pointed out), is my file's encoded using mpeg4 (Simple Profile) while the working one using mpeg4 (Advanced Simple Profile). What's the difference and how I encode it?

Any suggestions will be appreciated.

---

### Post by andrew.46 on 2014-06-15
Always difficult to find the best recipe for devices like this! If the sound is perhaps choking the device I see that FFmpeg at least has 3 ac3 encoders:

```

andrew@ilium~$ **[COLOR="#FF0000"]ffmpeg -encoders 2>/dev/null | grep -i ac3[/COLOR]**
 A..... ac3                  ATSC A/52A (AC-3)
 A..... ac3_fixed            ATSC A/52A (AC-3) (codec ac3)
 A..... eac3                 ATSC A/52 E-AC-3

```

but unfortunately I don't know enough about ac3 encoding to guide a choice here. The following should produce a 'Advanced Simple Profile' mpeg4 encoding, and uses eac3, and might be worth looking at:

```

ffmpeg -i abc.mp4 \
       -c:v mpeg4 -vtag XVID **[COLOR="#FF0000"]-profile:v 15 -level 7[/COLOR]** -q:v 5 -f avi \
       -mbd rd -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 \
       -c:a  eac3 -ab 192k -ac 2 -ar 48000 \
       abc-2.avi

```

You could also experiment with *-level xxx* and I am not sure what level is best. See [here for more details of a complex issue]("http://en.wikipedia.org/wiki/MPEG-4#Profiles_and_Levels"). I don't use avconv, rather I use FFmpeg, but these commands should work perhaps with some massaging for avconv :).

---

