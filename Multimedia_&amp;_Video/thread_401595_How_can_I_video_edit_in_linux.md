---
title: "How can I video edit in linux?"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by Aro on 2007-04-04
I'm trying to make some short video clips and I need to be able to cut and paste bits out of .avi's and other video formats (the more the merrier). It would also be nice if I could modify audio, too. 

For the most part I'll be using video's I take with my camera. 

I don't know of any software for linux though. I'm not looking for fancy just yet. Just anything to learn with.

Thanks

---

### Post by Maestro23 on 2007-04-04
List of programs here: [http://linuxappfinder.com/multimedia](http://linuxappfinder.com/multimedia)

---

### Post by oilchangeguy on 2007-04-04
found automatix has one, avidemux

---

### Post by bluebyt on 2007-04-04
I think you can use Avidemux. It is very good and userfriendly!

[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)

Install like this: Add/Remove, Search: avidemux 

Good luck!

---

### Post by newlinux on 2007-04-04
What kind of camera/camcorder do you have? if dv look into kino or cinelerra. I don't think kino supports HDV but cinelerra does. If you are just taking avis with a camera then the previous suggestions will do...

---

### Post by qamelian on 2007-04-04
> **oilchangeguy said:**
> found automatix has one, avidemux

You don't need Automatix to install Avidemux. It's in the Ubuntu repos so you can just install it with apt-get/aptitude/Synaptic.

Another one that's pretty good is Kino.

---

### Post by Aro on 2007-04-04
Well, 
I installed avidemux, kino, and something called pitivi...

Avidemux keeps giving me a "Trouble initializing audio device", and beyond that I don't see how I can cut and paste segments of video around...=/ 

I have a digital camera, not video camera so kino's DV feature is kind of useless right now. I plan on getting a DV soonish though. Aside from that, Kino doesn't seem to want to open any .avi files at all. When I try it says, "Failed to load media file". I can't open any files so I can't test editing with it.

Pitivi is like a bad version of windows movie maker. 

Anyone know how to fix the Kino importing problem? Can Kino open a video file then cut out a small clip from that video?

---

### Post by fenian on 2007-04-05
You may want to check out [Kdenlive]("http://ubuntuforums.org/showthread.php?t=322916&highlight=kdenlive").

If you want to use Kino with avi clips you'll need to convert them first you can use Avidemux and other programs or you can do it from the command line with ffmpeg.If you have a lot of small clips that you want to convert ffmpeg is a good choice because you can gather them all into one directory and convert them all with one command.

---

### Post by reclusivemonkey on 2007-04-05
> **Aro said:**
> Well, 
I have a digital camera, not video camera so kino's DV feature is kind of useless right now. I plan on getting a DV soonish though. Aside from that, Kino doesn't seem to want to open any .avi files at all. When I try it says, "Failed to load media file". I can't open any files so I can't test editing with it.

Anyone know how to fix the Kino importing problem? Can Kino open a video file then cut out a small clip from that video?

Are you using Dapper? I found that in Edgy and Feisty, the avi importing to Kino worked fine for me.

---

### Post by Aro on 2007-04-05
Yes, I'm running Dapper on this system.

I got avidemux to play audio by going to edit>preferences>audio then selecting "SDL" for audio output. Whatever that is ;-P I still can't figure out how to edit video, however.

I then tried to use avidemux to convert my avi's into a format I could open in kino, but I couldn't get it to work. The only other format I could successfully save the video file as was OGM, and kino wouldn't open that either. :(

So, I gave ffmpeg a shot. I installed it from the synaptic package manager then read a bit about the commands [here]("http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html#SEC7") 

I ran ffmpeg -i DSCF0002.AVI -target dv /tmp/sexy.dv
and it said: 
> DSCFOOO2.AVI: I/O error occured
Usually that means that input file is truncated and/or corrupted.

This is just a video I pulled off my digital camera. It was in .AVI format and I can view it fine using VLC or anything else I try. So, there shouldn't be anything wrong with it...

Can anyone help me learn how to convert video formats correctly? :)

---

### Post by fenian on 2007-04-05
> I ran ffmpeg -i DSCF0002.AVI -target dv /tmp/sexy.dv

Try renaming the file so the filetype is in lowercase (.avi) rather than in uppercase (.AVI).

---

### Post by Aro on 2007-04-05
Thanks, renaming from .AVI to .avi had the effect of getting passed that error message.

When I run ffmpeg -i dsc.aci ntsc-target dv /tmp/sexy.dv 
i get the following output:

>  ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
Input #0, avi, from 'dsc.avi':
  Duration: 00:00:42.0, start: 0.000000, bitrate: 4684 kb/s
  Stream #0.0: Video: mjpeg, yuvj422p, 640x480, 15.00 fps
  Stream #0.1: Audio: pcm_u8, 8000 Hz, mono, 64 kb/s
Unable for find a suitable output format for 'ntsc-target'


---

### Post by fenian on 2007-04-05
Try this...
> 
 ffmpeg -i dsc.aci -target dv /tmp/sexy.dv

---

### Post by Aro on 2007-04-05
Sorry, I should have made that a little clearer. 
I already tried it without the ntsc command using the lower case .avi (i ran that command you wrote)

i ended up with the following output:
> 
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
Input #0, avi, from 'dsc.avi':
  Duration: 00:00:42.0, start: 0.000000, bitrate: 4684 kb/s
  Stream #0.0: Video: mjpeg, yuvj422p, 640x480, 15.00 fps
  Stream #0.1: Audio: pcm_u8, 8000 Hz, mono, 64 kb/s
Could not determine norm (PAL/NTSC/NTSC-Film) for target.
Please prefix target with "pal-", "ntsc-" or "film-",
or set a framerate with "-r xxx".


That is why I tried with ntsc in front. Which also didn't work =/

---

### Post by fenian on 2007-04-06
Try...

ffmpeg -i dsc.avi -target ntsc-dvd /tmp/sexy.dv

---

### Post by Aro on 2007-04-06
ffmpeg -i dsc.avi ntsc-dvd /tmp/sexy.dv

> ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
Input #0, avi, from 'dsc.avi':
  Duration: 00:00:42.0, start: 0.000000, bitrate: 4684 kb/s
  Stream #0.0: Video: mjpeg, yuvj422p, 640x480, 15.00 fps
  Stream #0.1: Audio: pcm_u8, 8000 Hz, mono, 64 kb/s
Unable for find a suitable output format for 'ntsc-dvd'


Am I missing some dependancies or something??

---

### Post by fenian on 2007-04-06
Sorry I made a typo in my last suggestion it should have been...
> 
ffmpeg -i dsc.avi -target ntsc-dv /tmp/sexy.dv

If this doesnt work try converting it to mpeg2 with

> ffmpeg -i dsc.avi -target ntsc-dvd /tmp/sexy.mpg

then try importing the mpeg into kino.

---

### Post by doobit on 2007-04-06
The video off a digital still camera is normally mjpeg format. .avi is just a wrapper made for Microsoft so the Microsoft Media player can run it. There are all kinds of mjpeg formats, so you may need to install the codec that's specific for your camera in order for the editing software to work with it. I can't tell you how to do that, except that you may find a codec package on the CD that came with the camera. Usually it's a matter of copying it to the right folders so the editing software can find it and use it.

---

### Post by Aro on 2007-04-08
Hi again :)

I ran 
> ffmpeg -i dsc.avi -target ntsc-dv /tmp/sexy.dv
and it's actually working now :D

I guess the -dvd part was my mistake :)

I double clicked the .dv file and it automatically loaded it (successfully) in kino.

I toyed with kino for 30 seconds and figured out how to cut and paste segments of video around as well as import other files. Which was the MAIN thing I was trying to do.

Thank you all very much,
and a special shout out to fenian who never gave up on me :D

Thank you!:KS

---

### Post by usererror on 2007-04-11
thanks for this thread!  I want to start playing with video editing myself just starting off with video clips from my digital camera (Canon S500) I will use this as a reference when I get to it!!

The avidemux program is awesome, I am finally using it now.

---

