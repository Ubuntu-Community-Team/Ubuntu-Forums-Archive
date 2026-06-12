---
title: "fixing AVI video"
date: 2014-12-11
forum: Multimedia Software
---

### Post by kimble2 on 2014-12-11
My camera takes video in 1280x720x30fps AVI format.
Playing it back with VLC the sound track plays OK, but the video is stuck on the first frame throughout.
DSCN0450.AVI is 2:22 long and is 545.8 MB in size.
So I try to fix it with mencoder:
[INDENT]12:05:01_dk@www2:/media/dk/SATA500$ mencoder -forceidx -oac copy -ovc copy DSCN0450.AVI -o DSCN0450.2.AVI
MEncoder 1.1-4.8 (C) 2000-2012 MPlayer Team
success: format: 0  data: 0x0 - 0x221d94c4
libavformat version 54.20.4 (external)
Mismatching header version 54.20.3
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
Generating Index:  99 %     
AVI: Generated index table for 8546 chunks!
VIDEO:  [MJPG]  1280x720  24bpp  30.000 fps  31783.4 kbps (3879.8 kbyte/s)
[V] filefmt:3  fourcc:0x47504A4D  size:1280x720  fps:30.000  ftime:=0.0333
videocodec: framecopy (1280x720 24bpp fourcc=47504a4d)
audiocodec: framecopy (format=1 chans=1 rate=22050 bits=16 B/s=44100 sample-2)
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos: 142.9s   4289f (100%) 205.04fps Trem:   0min 545mb  A-V:-0.000 [31671:352]
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 31664.562 kbit/s  (3958070 B/s)  size: 565872124 bytes  142.967 secs  4289 frames

Audio stream:  352.800 kbit/s  (44100 B/s)  size: 6280848 bytes  142.423 secs
12:06:14_dk@www2:/media/dk/SATA500$
[/INDENT]


and the resulting file is the same size and does the same thing.
That "ftime=0.0333" is a bit worrying - I don't know what it means, but if the total time is 1/30 sec ...

So I use VLC's Convert/Save function to turn it into .mp4 and it does it OK,
and get DSCN0450.mp4, size 146.1 MB.
Playing it, the sound is horrible and the video is still stuck on the first frame.

What next?

---

### Post by andrew.46 on 2014-12-12
> **kimble2 said:**
> What next?

It might be worthwhile to try to rebuild the file with [a recent copy of FFmpeg]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu"). Mind you if the file is irretrievably damaged there might not be much you can do...

---

### Post by kimble2 on 2014-12-12
If you pause VLC and drag the time marker, the frozen frame moves on - so the data seems to be all in there.

I have also downloaded DivFix++_0.34-1_i386.deb and run that - same problem.

Can you explain what tool does "rebuild the file"?
I can follow a script, but I'm lost as to what's happening.

---

### Post by andrew.46 on 2014-12-12
FFmpeg is a commandline encoder, so similar idea as what you have tried to do with MEncoder but with a much more sophisticated tool. A few more thoughts:

[LIST=1]
[*]If you can play it after a fashion in vlc you can perhaps try to convert the file using vlc's 'Convert/Save' option. This may produce a working file for you.
[*]If you get stuck and the file is less than 150mb place it here: [http://www.datafilehost.com/](http://www.datafilehost.com/) and I would be interested to have a look at it.
[*]
[/LIST]

**Edit:** My apologies I see that you have already tried conversion with vlc :(. Hmmm... and too big for datafilehost...

---

### Post by kimble2 on 2014-12-12
Thanks, I tried this, starting at 2:00 to produce at shorter file:
ffmpeg -ss 120 -report -stats -i /media/dk/SATA500/DSCN0450.AVI /media/dk/SATA500/ffmpeg.short.DSCN0450.mp4
- still the same problem in VLC.
It complains "No pixel format specified, yuvj422p for H.264 encoding chosen." and then proceeds processing normally.
The .mp4 file is at [http://www.datafilehost.com/d/a4cc40a7](http://www.datafilehost.com/d/a4cc40a7) [32 MB], the log is at [http://www.datafilehost.com/d/19415cb9](http://www.datafilehost.com/d/19415cb9)

As you will see, I have yet to rotate the frame.
I should add that this problem occurs with ALL video from this camera - Nikon S3500.

---

### Post by andrew.46 on 2014-12-12
Hmmm..... the file plays perfectly here in both MPlayer and vlc....

---

### Post by kimble2 on 2014-12-13
That's really weird, MPlayer doesn't even show the first frame, the audio plays, and at the end it freezes.
Doesn't that suggest some common video module is corrupt/wrong version?

It doesn't play in MPlayer on my netbook either (also Lubuntu 14.04).

---

### Post by andrew.46 on 2014-12-13
I am not using the stock MPlayer but on the most recent svn it runs a smooth as silk, screenshot attached. Interesting to see if others have any trouble with the file...

---

### Post by kimble2 on 2014-12-13
I decided to uninstall, autoremove and reinstall VLC and Mplayer from the terminal.
Curiously that invoked Software Updater to make some changes to Audacious and Rhythmbox plus some Ubuntu core things (I've not seen that happen before).
That all went smoothly.
I felt sure that that would have fixed everything - but no, its still the same.

I have also run MPlayer on my server box, and that works OK!
So the file is OK, and so my workhorse box installation is probably a bit screwed.
I've got a new motherboard with J1900 (Celeron quad core) and 64-bit coming soon, so I will be installing Lubuntu(64) on that, and hopefully this problem will just go away :)

I'll report in a few days.
Thanks for your help.

---

### Post by andrew.46 on 2014-12-13
> **kimble2 said:**
> I'll report in a few days.

Good luck :)

---

### Post by Rob Sayer on 2014-12-13
Before learning mencoder cli mode, I'd try installing avidemux (which is in the 14.04 repos).  It's quite good at fixing problems with avi files.  E.g. by doing things like rebuilding frames, building vbr audio time maps, etc.

Are there any decent linux mencoder GUIs out there?  I've never had any luck finding any.  Strange.

---

### Post by andrew.46 on 2014-12-13
> **Rob Sayer said:**
> Are there any decent linux mencoder GUIs out there?  I've never had any luck finding any.  Strange.

There is a list here:

[http://www.mplayerhq.hu/design7/projects.html#mencoder_frontends](http://www.mplayerhq.hu/design7/projects.html#mencoder_frontends)

but I confess I have not tried these, MEncoder has not been actively developed for some time and most have moved to FFmpeg.

**Edit:** Mind you I have actually used h264enc & xvidenc, both of these were very nicely made...

---

### Post by kimble2 on 2014-12-17
Well it works nicely in my clean install of Lubuntu(64):p, so it must have been a software glitch in the old OS.
And the netbook was probably running on an SSD that was imaged off the old OS too.
Thanks for all your help.

---

