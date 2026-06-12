---
title: "skype screencast"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by bayonetblaha on 2008-04-14
here's an interesting idea: anyone know a way to use the display as a video input device for skype, to show one's screen over skype?

---

### Post by loell on 2008-04-14
show a screencast  at that particular instant? not yet.

but you can show your prerecorded screencast by using these tools

**recordmydesktop** which records desktop session,

after making the video, you can pipe it to a video device by using

[http://allonlinux.free.fr/Projets/AVLD/]("http://allonlinux.free.fr/Projets/AVLD/")

then use the particular video device through skype to stream it.

---

### Post by bayonetblaha on 2008-04-14
wow! thanks! I need a little help getting it set up though. I got all the way to "write on the device", and I don't understand what that command is doing. 

File not found: 'my_movie.***'
Failed to open my_movie.***.
Cannot open file/device.

basically, I don't understand the purpose of "my_movie". Is that a file where AVLD is putting its output for programs to access?

---

### Post by loell on 2008-04-14
what's **my_movie.*****   whats the video format of this file?

---

### Post by bayonetblaha on 2008-04-14
I tried replacing *** with mpg, same error

---

### Post by loell on 2008-04-14
> **bayonetblaha said:**
> 
basically, I don't understand the purpose of "my_movie". Is that a file where AVLD is putting its output for programs to access?

its rather the input file or movie to be be streamed , make sure you have a my_movie.mpg file.

---

### Post by bayonetblaha on 2008-04-14
ok, I get it now. That's supposed to be the filename that I give recordmydesktop to run.  I can't seem to get that file going, though. 

recordmydesktop video.mpg

and no file gets created. I get a lot of Broken pipe: Underrun occurred. lines

I looked at my new dev/video1 device in mplayer, looks like TV static

---

### Post by loell on 2008-04-14
recordmydesktop doesn't record in mpg  format, its sole format in use is ogg, unfortunately. ;)
**out.ogg** is the default output of recordmydesktop in your base directory.

for mpg or avi convertion  use mencoder, [http://ubuntuforums.org/showthread.php?t=294605]("http://ubuntuforums.org/showthread.php?t=294605")

yeah i know, this whole process is a bit tedious.


edit.. 

uhmm, wait, i think you don't need to convert it to mpg or avi, just use the ogg if you've already produced it.

---

### Post by bayonetblaha on 2008-04-14
I really feel like I'm getting there. I have the ogg file, now I just have the problem that my mencoder command "finishes" after a few seconds and no more video device

---

### Post by loell on 2008-04-14
just let me know where you get stuck.

---

### Post by bayonetblaha on 2008-04-14
still the same... I run that mencoder command and it counts up to 100% on encoding and stops. I left mplayer running on /dev/video1 and all I saw was the same static image

interesting.. went to 101% last time I ran it

---

### Post by loell on 2008-04-14
ok, so we will not  convert it. try to play the ogg video , just to make sure that you see your desktop when played.

---

### Post by bayonetblaha on 2008-04-14
I've been playing with that, yeah, when I run the ogg video in totem it always shows my desktop from when I began recording and streams video from that point on

just need to get that .ogg to /dev/video1

---

### Post by loell on 2008-04-14
i see, :)

if you've loaded the **avld** module previously,  could you unload it, by

```
sudo rmmod avld
```

then load it with the parameters

```
modprobe avld width=**[your screen resolution width]** height=**[ your screen resolution height]** fps=15
```

then pipe the video file

```
mencoder out.ogg  -nosound -ovc raw -vf format=bgr24 -of rawvideo -o /dev/video1
```

---

### Post by bayonetblaha on 2008-04-14
heh. stuck right away

ERROR: Module avld is in use

---

### Post by loell on 2008-04-14
i guess we'll gonna have to reboot, to unload the module.

heheh, we should have just use **rmmod -f** , but next time anyway.

---

### Post by bayonetblaha on 2008-04-15
mencoder still encodes to 100% or a little more and ends, leaving me back at the prompt

---

### Post by bayonetblaha on 2008-04-15
well that's strange... I tried it again and now it works as far as mencoder continuing... it's at 700% as I speak.  However, when I try to switch Skype's input to /dev/video1 it crashes.  Might this be because video1 is piping at 1440x900? I've read the mencoder manpages some, but I can't figure out how to change it to 640x480 (I assume that's the proper dimensions) Always getting parsing errors, so I guess I just don't get it

---

### Post by bayonetblaha on 2008-04-17
mencoder output when it insists on completing the operation

nelson@ron:~$ mencoder /home/nelson/Videos/out.ogg  -nosound -ovc raw -vf format=bgr24 -of rawvideo -o /dev/video1
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0xa2b000
[Ogg] stream 0: video (Theora v3.2.1), -vid 0
Ogg file format detected.
VIDEO:  [theo]  1440x896  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:1440x896  fps:15.00  ftime:=0.0667
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [format fmt=bgr24]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x88056f0]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1440 x 896 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.61:1 - prescaling to correct movie aspect.
[swscaler @ 0x8800710]SwScaler: using unscaled yuv420p -> bgr24 special converter
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
Pos: 106.6s   1599f (119%) 105.93fps Trem:   0min   0mb  A-V:0.000 [464486:0]
Flushing video frames.

Video stream: 464486.400 kbit/s  (58060800 B/s)  size: 6189281280 bytes  106.600 secs  1599 frames
nelson@ron:~$

---

