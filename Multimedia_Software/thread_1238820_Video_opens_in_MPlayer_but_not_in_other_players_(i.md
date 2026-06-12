---
title: "Video opens in MPlayer but not in other players (inc. Avidemux)"
date: 2009-08-12
forum: Multimedia Software
---

### Post by Replicon on 2009-08-12
Hi,

I'm running 8.04. I'm having a problem where an mpeg file opens fine in MPlayer, but not in any other player. VLC opens just the sound, and Avidemux just plain says "could not open file"

What I don't get is, how come MPlayer can handle it fine? I was under the impression that codecs were shared, so if MPlayer can handle it, so should all other tools that load video.

Here is relevant the output when running avidemux from the command line:

```

Cannot identify <filename>.mpeg as mpeg (4/6)
Cannot identify as H264 ES (2/50)

 unrecognized file detected...
.RMF (464D522E)
 (12000000)


```

EDIT: Oh I can see now - when I look at the file properties, it says the codec is Real Video 4.0

This is frustrating, because I used to be able to convert and play with real media without any problems in the past. It might have been with 7.10 though, and it might have over-written it after updating to 8.04 (grumble).

My comment about MPlayer handling it fine still stands, though... if I didn't have the right codec installed, shouldn't it consistently just not play? :)

Thanks!

---

### Post by Replicon on 2009-08-21
ping? I ran all the install instructions on the "Comprehensive" sticky, but it's still failing. What could I be missing?

---

### Post by andrew.46 on 2009-08-21
Hi Replicon,

> **Replicon said:**
> ping? I ran all the install instructions on the "Comprehensive" sticky, but it's still failing. What could I be missing?

Could you identify the problem file with FFmpeg? The easiest way is to follow the directions here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and then interrogate the file from the commandline as follows:

```
ffmpeg -i ***[COLOR="Red"]myproblemfile.mpg[/COLOR]***
```

This will give a reasonable level of information about the audio and video codecs used in your problem file.

All the best,

Andrew

---

### Post by Replicon on 2009-08-21
```

ffmpeg -i 80scream.mpeg 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:11:10, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
[NULL @ 0x7f4dc786a8d0]Unsupported video codec
Input #0, rm, from '80scream.mpeg':
  Duration: 00:10:40.8, start: 0.000000, bitrate: 935 kb/s
  Stream #0.0: Video: RV40 / 0x30345652, 720x576, 832 kb/s, 12.00 fps(r)
  Stream #0.1: Audio: cook, 44100 Hz, stereo, 96 kb/s
  Stream #0.2: Data: 0x0000
Must supply at least one output file

```

As part of re-running all those commands on the comprehensive video guide, it does look like I've run the big medibuntu command. How do I know if the version of ffmpeg I have is the right one? I *think* it updated it for me (as soon as I ran that, synaptec kicked in with updates, including I think ffmpeg).

It looks like it can figure out the file (duration is the same, etc.)

When I try to run it, I usually do:

ffmpeg -i 80scream.mpeg -sameq -r ntsc 80scream.mpg

or 

ffmpeg -i 80scream.mpeg -sameq 80scream.mpg

(convert the RM to mpg)

It's frustrating cause it's clear from that output that it knows exactly what the file is, and -sameq should basically use those same parameters.

---

### Post by Bucky Ball on 2009-08-21
Have you got 

```
ubuntu-restricted-extras
```and 

```
ubuntu-restricted-modules
```installed?

System->Admin->Synaptic, search for them and have a check. You might also consider adding the Medibuntu repository to your software sources. :)

Sounds like you don't have the right codec for the others.

---

### Post by Replicon on 2009-08-21
ubuntu-restricted-extras is already the newest version.

E: Couldn't find package ubuntu-restricted-modules

(that howto did mention that the restricted modules/packages are really for Intrepid and Jaunty)

It plays fine in mplayer, so the codec is there somewhere :)

---

### Post by andrew.46 on 2009-08-22
Hi Replicon,

> **Replicon said:**
> 
```

Stream #0.0: Video: RV40 / 0x30345652, 720x576, 832 kb/s, 12.00 fps(r)
Stream #0.1: Audio: cook, 44100 Hz, stereo, 96 kb/s

```


MPlayer will play these files with the (so-called) w32codecs:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vc help | grep rv40[/COLOR]**
rv40        realvid   problems  Linux RealPlayer 9 RV40  [drv4.so.6.0]
rv40win     realvid   working   Win32 RealPlayer 9 RV40  [drv43260.dll]
rv40mac     realvid   working   Mac OS X RealPlayer 9 RV40  [drvc.bundle/Contents/MacOS/drvc]
ffrv40      ffmpeg    working   FFmpeg RV40  [rv40]

```

Do other media players actually use these codecs? Possibly vlc with the dmo loader enabled but this is not the default in Ubuntu.

Andrew

---

### Post by mc4man on 2009-08-22
@ Replicon
It would be interesting, possibly helpful if you ran mplayer from the cli to see what codec it's using. ( mplayer /path/to/file/filename

or a sample or link to the same type you're playing or trying to play

> Do other media players actually use these codecs?
Here at least all the media players I have will play the couple of different RV40's I've found, one a .rm, one ,rmvb.
(totem-xine, xine-ui, vlc, mplayer

Only mplayer and vlc say what they're using, only mplayer is specific.
Vlc and probably the xine players use ffmpeg - ffrv40

With only the  all-2007-1007...codecs from mplayer site mplayer uses ffmpeg also.
Adding a .dll ( drv43260.dll) mplayer then uses that instead

some clipped outputs
vlc
> [00000427] avcodec decoder debug: ffmpeg codec (Real Video 4.0) started
mplayer w/default w32codecs

> Win32 LoadLibrary failed to load: drvc.dll, /usr/lib/win32/drvc.dll, /usr/local/lib/win32/drvc.dll
Error loading dll
ERROR: Could not open required DirectShow codec drvc.dll.
.................
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffrv40] vfm: ffmpeg (FFmpeg RV40)


with drv43260.dll added to codecs ( drv43260.dll is included in w32codecs
> Opening video decoder: [realvid] RealVideo decoder
Win32 LoadLibrary failed to load: drvc.dll, /usr/lib/win32/drvc.dll, /usr/local/lib/win32/drvc.dll
Error loading dll
ERROR: Could not open required DirectShow codec drvc.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Selected video codec: [rv40win] vfm: realvid (Win32 RealPlayer 9 RV40)


(( there are quite a number of additional drv* codecs, tthough never have seen drvc.dll

---

### Post by Replicon on 2009-08-22
Andrew,

I am seeing some differences between your output and mine for what codecs mplayer is aware of:

```
mplayer -vc help | grep -i rv40
rv40        realvid   working   Linux RealPlayer 9 RV40 decoder  [drv4.so.6.0]
rv40win     realvid   working   Win32 RealPlayer 9 RV40 decoder  [drv43260.dll]
rv40mac     realvid   working   Mac OS X RealPlayer 9 RV40 decoder  [drvc.bundle/Contents/MacOS/drvc]
```

Your RV40 is listed as having problems, while mine is listed as working.

However, you have ffrv40 and I don't, which is... interesting. Is this a sign that I still don't have the correct ffmpeg installed? When I check in Synaptec, it definitely says my ffmpeg is the Medibuntu version.


@mc4man:

Here is a run of mplayer with the file:

```

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 80scream.mpeg.
REAL file format detected.
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
[real] Video stream found, -vid 0
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 1
Stream mimetype: logical-fileinfo
VIDEO:  [RV40]  720x576  24bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 comment: 
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [realvid] RealVideo decoder
Selected video codec: [rv3040] vfm: realvid (Linux RealPlayer 10 RV30/40 decoder)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 96.5 kbit/6.84% (ratio: 12058->176400)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio decoder)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar I420)
VDec: using Planar I420 as output csp (no 0)
Movie-Aspect is 1.25:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 720x576 Planar I420 
GNOME screensaver enabled.001 ct: -0.070  47/ 47 18%  1%  1.2% 0 0

```

---

### Post by mc4man on 2009-08-22
if the video is rv40, which it appears to be, then vlc can play it if libavcodec can decode plus vlc has the real module enabled. (at least in 0.9.x and 1.x.x

You could test your ffmpeg with ffplay /path/to/filename

While I use hardy I've changed things a bit so can't say if vlc 0.8.6 can play rv40 (or rv30 either

You could upgrade your vlc to 0.9.a thru a ppa if it's 0.8.6 that you're using.

As far as most rv30 vlc 0.9.x will only play audio, 1.0.2 will playback fine

---

### Post by Replicon on 2009-08-22
ffplay only gets the audio, as expected.

Really, I think we might have reduced the problem to, "What steps do I need to take to install the ffrv40 driver, and have ffmpeg use it?" Oddly, google is really not helping here. Alternately, I guess the question could also be, "What steps do I need to take to make ffmpeg use one of the existing rv40 drivers on my system for its conversion needs?"

It looks like I may have to install some win32 dll somehow, but I have no idea about the procedure, and what dll I need to grab. I think I probably already have it installed (rv40win?) so it might be a matter of telling ffmpeg to use it.

---

### Post by andrew.46 on 2009-08-23
Hi Replicon,

> **Replicon said:**
> What steps do I need to take to install the ffrv40 driver, and have ffmpeg use it.

I suspect that you need to be running newer versions of both FFmpeg and MPlayer. There is a nice guide for FFmpeg here:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and there are a few different guides for the svn MPlayer elsewhere on the forums + suggestions for some PPAs hosting new copies.

Andrew

---

### Post by hl2040 on 2009-08-23
Same thing here. I am running 8.04 (kubuntu) and all of a sudden after a reboot, videos which I had just been watching prior to reboot no longer work at all. I went ahead and installed w32codecs from medibuntu, but something else seems weird here. vlc plays the files file, which is to be expected but somehow in a recent upgrade I'm guessing the codec situation has changed. Sometimes when files get removed by dpkg/apt, they continue to exist while applications have them open, and then promptly disappear as soon as KDE/Gnome/thecomputer is restarted.

---

### Post by hl2040 on 2009-08-23
Sorry for the noise, in case we have different problems. For me, it came down to reinstalling about seven libxine1 packages: libxine1, libxine1-bin, libxine1-ffmpeg, libxine1-console, libxine1-misc-plugins, libxine1-plugins, libxine1-x.

This probably isn't the minimal set of packages to reinstall, but it worked for me.

---

### Post by Replicon on 2009-08-24
I just removed/re-installed those packages myself, with no results. How did you come up with that list, out of curiosity?

I suppose I might just be forced to build from source if I don't find a viable solution within the next few days (though I'm not in any particular hurry). I just *know* there's a magic incantation that'll make it work. There's got to be like a flag for ffmpeg, like "--use_the_already_installed_codec_that_works_fine_dumbass=rv40" :lol:

---

### Post by hl2040 on 2009-08-24
First off: I use 8.04, so maybe things are different in a newer release.

The libxine package bunch was just a group of packages that I found searching in aptitude for the string "libxine". Also, they were of a group of xine packages (possibly linked by dependencies) which had two package versions available: one, say was libxine1-ubuntu8, and the other (newer) was "libxine1-ubuntu8.3". I don't think those are the exact package names, but that's the gist of it. I downgraded, then upgraded (maybe there was an X restart just for giggles) and it worked.

Too bad this is a *stupid* problem. I say just build it from source!

If you can find a deb file which contains the dll or whatever for your rv40, you can use dpkg or alien to extract the files from the deb and manually insert them into your /usr/lib/codecs folder. Or if you're really bored you can run strace on ffmpeg to see where it is looking for codecs.

---

