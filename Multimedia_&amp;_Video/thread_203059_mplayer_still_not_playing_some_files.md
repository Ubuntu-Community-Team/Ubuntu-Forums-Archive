---
title: "mplayer still not playing some files"
date: 2006-06-24
forum: Multimedia &amp; Video
---

### Post by muhkayoh on 2006-06-24
Hello,

When I initially installed Ubuntu I went the Automatix route to get extra codecs and such, and for the most part I seem to be able to view most video files.  However, there are a few files that I can't figure out how to view.  One such file is this example movie from the Blender movie gallery:

[http://download.blender.org/demo/movies/ChairDivXL.avi](http://download.blender.org/demo/movies/ChairDivXL.avi)

I tried running mplayer from the command line and here's what I get:

> $ mplayer ChairDivXL.aviMPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing ChairDivXL.avi.
AVI file format detected.
VIDEO:  [DIVX]  800x600  24bpp  30.000 fps  1506.1 kbps (183.8 kbyte/s)
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/60208 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 800 x 600 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 800x600 => 800x600 Planar YV12
alsa-space: xrun of at least 5.326 msecs. resetting stream?,?% 0 0
X11 error: BadAlloc (insufficient resources for operation)


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed

Mplayer starts to play the file. I even hear a brief second of sound, but then mplayer shuts down.  I've also tried playing the file in VLC and Totem with similar behavior and results.

Looking through the feedback above, I don't have a joystick and I'm not concerned at the moment about remote control. So unless those areas impact my basic ability to view the file, feel free to ignore that stuff if you're trying to help me out.

I see the bit about "insufficient resources for operation" and I get what that means in general, but I'm at a loss as to why that happens with this file and not others or what do to about it.


At any rate some help in figuring out how to get this file to play would be greatly appreciated.  There are several of the Blender video tutorials that I have similar trouble with, and I'm hoping to figure out a way to watch them.

Thanks,

Matt Jordan

---

### Post by tonyr on 2006-06-24
I got codecs from Penguin Liberation Front, and had no problem with your download sample using
**mplayer**.

Add these to your **/etc/apt/sources.list**
```

## Specifically for w32codecs
## Penguin Liberation Front
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

```

then in a terminal do
```

sudo apt-get update
sudo apt-get install w32codecs

```

You can use **breezy** instead of **dapper** in the sources lines.  I think a 
lot of the actual packages are the same anyway.

---

### Post by muhkayoh on 2006-06-24
Thanks for the reply, but here's what happened:

```
$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

And when I tried to play the file, just in case, I got the same result - brief start, then shutdown.

Matt Jordan

---

### Post by muhkayoh on 2006-06-24
Doing some further poking around and looking at files on my system, I'm comparing those that play to those that won't.  I'm starting to think that my problem may not be codec-related.  

The file above that won't play is ISO MPEG-4 (ffmpeg) for video and MPEG layer 2/3 for audio, but I have quite a few files that will play with the exact same codec info (via the properties window).  This would seem to indicate that the problem isn't the codecs, no?  And isn't this position backed up by the fact that I apparently already had the most up-to-date Windows codecs, as evidenced in my post above?  

This may be a case where I don't know enough about what I'm talking about :D , but if it isn't the codecs, what else could it be?

Matt Jordan

---

### Post by tonyr on 2006-06-24
...hmmm... don't know... here's what my mplayer output is, FWIW:
```

mplayer Desktop/movie.avi
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing Desktop/movie.avi.
AVI file format detected.
VIDEO:  [DIVX]  800x600  24bpp  30.000 fps  1506.1 kbps (183.8 kbyte/s)
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/60208 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 800 x 600 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 800x600 => 800x600 Planar YV12
A:   4.2 V:   3.7 A-V:  0.437 ct:  0.363 113/113 38% 68%  1.5% 89 0

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

alsa-space: xrun of at least 0.393 msecs. resetting stream1.5% 90 0
alsa-space: xrun of at least 0.011 msecs. resetting stream1.3% 202 0


```

It's very interesting to me that it says "Too slow", and then plays it anyway:-k

---

### Post by muhkayoh on 2006-06-25
I certainly appreciate tonyr's attempts to help me out, but this issue is still unresolved for me.  So if anybody else has some input, I'd be most grateful.

I've tried using MEncoder to convert the file to some other type to see if I could get the new type to play.  Each time I tried that, the conversion seemed to work insofar as a new file was created, but the new file would never play, no matter what conversion settings I tried.

I also note that tonyr's "You're system is too slow" message occurs at the same point as my "insufficient resources" message, but I don't know what to make of it.

Matt Jordan

---

### Post by tonyr on 2006-06-25
Since it doesn't play in any player, have you considered the possibility that the
file is bad?  Are you dual booting, or do you otherwise have access to another
OS (Windows, Mac) that you could try on the **same file**?

---

### Post by muhkayoh on 2006-06-25
tonyr,

Thanks again for the reply.  Yes, I've done what I could to rule out the bad file possibilty.  I had already re-downloaded the file as one check against some sort of download corruption.  And if I correctly understood your first reply, you were able to play the file, so I downloaded the file anew after your post and got the same result.

I don't currently have access to a windows machine, but I had what I reasonably assume was this same file, downloaded via the same link, on my XP machine before my switch to Ubuntu just a couple of weeks ago, and it played fine on Media Player Classic.

So, in short, I can't directly test the particular file I've downloaded on a separate system, but the indirect evidence I've got suggests that it's not the file.

Matt Jordan

---

### Post by tonyr on 2006-06-25
There are a couple of other threads reporting identical symptoms.  I seached on the whole phrase **X11 error: BadAlloc (insufficient resources for operation)** Have l look, maybe 
there are clues.
[http://www.ubuntuforums.org/showthread.php?t=202118]("http://www.ubuntuforums.org/showthread.php?t=202118")
[http://www.ubuntuforums.org/showthread.php?t=185784]("http://www.ubuntuforums.org/showthread.php?t=185784")

---

### Post by muhkayoh on 2006-06-25
Okay, I read through those threads and followed some links.  I don't quite follow everything that I read yet, but I did note that one of the threads pertained to the mplayer plug-in for mozilla.  I've been right-clicking and saving the file so that, when i view it repeatedly as I use it to help me learn blender (and this is more true of the tutorials which I haven't linked here, but which have similar problems when I try to view them), I won't unnecessarily tax the blender server.

In other words, I haven't been using the plug-in approach to view these files.  So I thought I'd try.

My first attempt yielded the same result as playing the file from my hard drive.  (I also have the Media PLayer Connectivity plug-in for Firefox, so I temporarily disabled that.)  Then, I went into the plug-in configuration (by right-clicking in the browser window) to try different video and audio settings in accordance with the advice from the thread you linked.  I noted that no video and audio selections had been made, so I just picked something: X11 for video and alsa for audio.  Then I reloaded the page and the video played perfectly.

So now I'm trying to figure out how this translates into playing the files from the hard drive.  I looked at the plug-in's config file, mplayer-in.conf, and saw the entries "vo=x11" and "ao=alsa."  I copied those to the mplayer conf file, which until this point was empty except for a default "loop=0" line I added a week or so ago.  Then I tried to play the video and got the same result: an aborted attempt with a second of sound.

So the situation at this point is:  The plug-in version, with x11 and alsa specified, plays the file, but the straight mplayer won't play it from the hard drive.

Matt Jordan

---

### Post by muhkayoh on 2006-06-26
As a temporary work-around, I created an html page with a link to the blender tutorials on my harddrive.  When I click on a vidoe file link, the plug-in version of the Mplayer plays the tutorials with no problem.  This is an acceptable work-around for the tutorials, but I still have two problems:

1) I'd really like to figure out how to get the Mplayer without the plug-in to play these files, just so I have more control over what's going on.

2) Even this plug-in approach doesn't seem to work well with bigger files.  For instance, I downloaded the bittorrent file for the largest version of the open source Blender movie, *Elephants Dream*.  I had been unable to play the file thus far, so I tried the plug-in trick.  The file plays, but the video is start-stop and lags severely behind the audio.

I've tried going through all of the items in the plug-in config file and copying them over to the Mplayer config file in various combinations to see if anything makes the Mplayer work like the plug-in version.  I'm pretty sure I tried every possible combo, from one item at a time, to copying the entire plug-in config file.  Nothing worked.

I'm obviously no Mplayer expert, but I am nonetheless baffled as to why I can't get the plain old player to do what the plug-in version can do.

Matt Jordan

---

### Post by glennric on 2006-08-19
Have you tried changing the same settings that you set for the plugin in the files ~/.mplayer/gui.conf and ~/.mplayer/config and /etc/mplayer/mplayer.conf?

---

### Post by Rangeli on 2006-09-24
I have the same problem and I found a workaround using scale video filter to make the picture smaller.

mplayer -vf scale=480:360 file.avi

Of course, we have to use other dimensions for different movies. The point is to keep the aspect ratio.

Did someone find out which package is cousing this problem? Then we could find some other version.

---

