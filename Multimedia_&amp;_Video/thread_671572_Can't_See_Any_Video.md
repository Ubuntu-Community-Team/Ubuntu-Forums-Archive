---
title: "Can't See Any Video"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by Prima Facie on 2008-01-18
I can't see any video at all. Not even the .ogg file with Nelson Mendela in the Examples folder. Help.

---

### Post by Zurd on 2008-01-18
Which video player do you use? Have you tried VLC or mplayer ?

If you go into a console/terminal and you type 'vlc video.ogg' what does it say?

---

### Post by Prima Facie on 2008-01-18
> **Zurd said:**
> Which video player do you use? Have you tried VLC or mplayer ?

If you go into a console/terminal and you type 'vlc video.ogg' what does it say?

I installed it. Video still doesn't work--neither in Movie Player nor VLC.

---

### Post by Zurd on 2008-01-19
You need to add more information so we can help you, try running the movie from a console, that will provide good information.

---

### Post by Prima Facie on 2008-01-19
> **Zurd said:**
> You need to add more information so we can help you, try running the movie from a console, that will provide good information.

What do you mean?

---

### Post by Zurd on 2008-01-19
Open up a Terminal, go into the directory where your video is, and type 'vlc your_movie.avi' then paste the result from the Terminal here so we can see what is the problem.

---

### Post by Prima Facie on 2008-01-19
> **Zurd said:**
> Open up a Terminal, go into the directory where your video is, and type 'vlc your_movie.avi' then paste the result from the Terminal here so we can see what is the problem.

Can you give me precisely what I need to type in?

---

### Post by Zurd on 2008-01-20
After you open up a Terminal, you need to type just a few commands, you should first read what they say on  [http://www.linuxcommand.org](http://www.linuxcommand.org) it may looks like long and complicated but it will pay off everytime you have a bug.

In fact, you only need to learn the command 'cd', 'ls', 'pwd' and stuff like that, it's very simple actually. Once you get in the directory of your video, run it like so 'vlc video.avi' or 'mplayer video.avi', then just copy and paste the results into the post and everyone here will have much more information to help you.

---

### Post by spindler04 on 2008-04-27
tmoney@tmoney-laptop:~$ cd Desktop
tmoney@tmoney-laptop:~/Desktop$ mplayer video.avi
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1600MHz (Family: 6, Model: 9, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing video.avi.
File not found: 'video.avi'
Failed to open video.avi.

I am a noob but I followed your instructions or at least I think I did.  I don't understand why I don't select a file to play?  Btw I am having the same problems as the OP.  Black screen and no audio when a video "plays".  help!

---

### Post by Zurd on 2008-04-27
Read the output : File not found: 'video.avi'

What more can I say? The file doesn't exist, type in another filename.

---

### Post by spindler04 on 2008-04-27
hey sorry I'm an idiot and didn't put an actual video for video.avi... Please laugh I know I am.  So thanks to you I did it correctly..

tmoney@tmoney-laptop:~/Desktop$ mplayer National.avi
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1600MHz (Family: 6, Model: 9, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing National.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [DX50]  640x360  24bpp  25.000 fps  998.4 kbps (121.9 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 256.0 kbit/18.14% (ratio: 32000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 360 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 640x360 => 640x360 Planar YV12 
[mpeg4 @ 0x8939870]frame skip 8t:  0.000   1/  1 ??% ??% ??,?% 0 0 
GNOME screensaver enabled.001 ct:  0.027 365/365  5%  3%  3.5% 4 0

I THINK its having a problem with my video card, Mobility Radeon 9000.  I'm not sure what to do.  I also have probs with my resolution and no extended desktop option.  So video card would be my noob guess.

---

### Post by Zurd on 2008-04-28
Great, you're on the good track. You could always install w32codecs from Synaptic, there's a few codecs in it that can help you watch more type of videos or install VLC, another great program to watch videos. 

For you video card, go into Synaptic and search for the name of your card (i.e. ati or nvidia), in my case I had to install nvidia-glx to use my video card at its fullest.

---

### Post by jelofson on 2008-04-29
I had a similar problem with my video players. I had to disable any desktop effects for them to be visible. I don't know why, I just did.

When no desktop effects are going it's fine.

Check if yours are enabled under System->Preferences->Appearance->Visual Effects.

---

### Post by jjstein on 2008-04-29
I have a similar problems and all efforts to alleviate thus far have proven fruitless though I have discovered this: If you open two simultaneous instances of the same video, the second will play.  At least that is how it is for me. I have no idea why, but it does.

---

