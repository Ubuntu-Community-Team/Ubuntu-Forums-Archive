---
title: "DivX + Blender. Unable to Render FFMPEG DivX codec"
date: 2009-05-24
forum: Multimedia Software
---

### Post by Spartanis on 2009-05-24
To whom it may concern.

AFter upgrading to Ubuntu 9.04. Install the latest Blender 2.48. I modeled something, and render its animation to avi , using Xvid .. or Divx, or any other codec. Blender crashes and closes itself.

However, rendering it as AVIRaw works perfectly (only to face a HUGE file size for a short movie!)

I have tried to download the latest DivX from various places, From Repository to DivX actual website. Still nothing.

Is there  way to solve this problem... if not.. is there another way i can "convert" this AVIRaw format to a more acceptable format (Xvid, Divx what have youse).

Thanking in advance
Spartanis

---

### Post by kostkon on 2009-05-24
Maybe it has something to do with your FFmpeg.

You could try running Blender from the terminal and see if it will output any errors.

---

### Post by Spartanis on 2009-05-24
k.. did that.. terminal says:


> spartanis@Spartanis-Ubuntu:~$ blender
Compiled with Python version 2.6.2.
Checking for installed Python... got it!
Starting output to /tmp/0001_0250.avi(ffmpeg)...
  Using type=3, codec=2, audio_codec=86016,
  video_bitrate=6000, audio_bitrate=128,
  gop_size=15, multiplex=0, autosplit=0
  render width=720, render height=576
[avi @ 0xa4584d0]Aspect ratio mismatch between encoder and muxer layer
Output #0, avi, to '/tmp/0001_0250.avi':
    Stream #0.0: Video: mpeg2video, yuv420p, 720x576 [PAR 1:1 DAR 5:4], q=2-31, 6000 kb/s, 90k tbn, 25 tbc
Writing frame 1, render width=720, render height=576
[mpeg2video @ 0xa459650]rc buffer underflow
Video Frame PTS: 0
Floating point exception
spartanis@Spartanis-Ubuntu:~$ 


Aspect Ratio Mismatch? :|

---

### Post by kostkon on 2009-05-24
You could try reinstalling FFMpeg.

Also, make sure that you have all of the unstripped libraries installed. To install them in one go, for example give:
```
sudo apt-get install libavcodec-unstripped-51 libavdevice-unstripped-52 libavformat-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0
```

---

### Post by Spartanis on 2009-05-24
> spartanis@Spartanis-Ubuntu:~$ sudo apt-get install libavcodec-unstripped-51 libavdevice-unstripped-52 libavformat-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0
[sudo] password for spartanis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libavcodec-unstripped-51
spartanis@Spartanis-Ubuntu:~$ 


hmm... the plot thickens :P

---

### Post by kostkon on 2009-05-24
> **Spartanis said:**
> hmm... the plot thickens :P
Whoops, yes because it's *libavcodec-unstripped-52*
The right one is
```
sudo apt-get install libavcodec-unstripped-52 libavdevice-unstripped-52 libavformat-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0

```
Sorry about that.

---

### Post by Spartanis on 2009-05-24
lol.. thats quite alright...

Did that.. installed nicely.

Went to Blender.. did a test 250 frames cube animation render with Xvid... Blender closes itself...

in fact.. tried every other.. still closes itself.

I shall sleep and return to this thread in 24 hours to see what else you or the others have suggested..

Spartanis

---

### Post by Spartanis on 2009-05-25
*bump*

EDIT:

After posting the same query @ BlenderNewbies forum.. One guy suggested to follow this instructions [here]("http://ubuntuforums.org/showthread.php?t=786095").

I did as exactly as it said.. Working fine except during "MAKE" i get alot of errors stating something about "Array below/Above Bounds.

I ran Blender and did a test again....same problem.

He reckons he had trouble getting Bender to work in Ubuntu 9.04 at all!

---

### Post by FakeOutdoorsman on 2009-05-25
> **Spartanis said:**
> 
I did as exactly as it said.. Working fine except during "MAKE" i get alot of errors stating something about "Array below/Above Bounds.
Are the "Array below/Above Bounds" errors from the FFmpeg installation or from Blender?

---

### Post by Spartanis on 2009-05-26
FakeOutdoorsman: It came from the FFmpeg MAKE proceedures.

---

### Post by FakeOutdoorsman on 2009-05-26
I've never encountered this error, or perhaps I just haven't noticed it.  Does this error prevent FFmpeg from compiling completely or installing?  Do you see any useful messages at the end of *config.err*?

---

### Post by Spartanis on 2009-05-27
nah it completes the make.. it never stops it...

---

### Post by FakeOutdoorsman on 2009-05-27
Did you install Blender from the repository or from blender.org?

---

### Post by Spartanis on 2009-05-27
From the Repository... mmm you onto something there...

---

### Post by FakeOutdoorsman on 2009-05-28
The repository Blender uses libavcodec52 or libavcodec-unstripped-52 as dependencies, so I doubt it's using your compiled FFmpeg and libavcodec.  You would have to compile Blender to use your compiled FFmpeg/libavcodec.  Jaunty has a relatively new FFmpeg and libavcodec, so I'm not sure if a compiled FFmpeg/libavcodec will help.

---

### Post by Spartanis on 2009-06-06
Well im trying this SevenBlend script atm.. in effort to fix this problem.. but its doing my head in lmao..  :)

---

### Post by linuxNewb on 2009-10-06
Was a fix ever found? I am having the same exact issue. After upgrading to 9.04, Blender just closes (crashes) when I click the Render button.

When running Blender from the Terminal I get the following output when Blender crashes:

[mpeg2video @ 0x9798360]rc buffer underflow
Video Frame PTS: 0
Floating point exception


Does that mean anything to anyone?

---

### Post by Spartanis on 2009-10-07
yes there was a fix. 

Blender website has a patch for it  i think. for those that uses the latest Ubuntu. I forgot how to do about it. since its been a while  lol

---

### Post by linuxNewb on 2009-10-07
Thank you for mentioning the blender site. I'm embarrassed to say that I never checked blender.org. It now contains a deb package for Ubuntu 9.04 which includes FFMPG support.

---

