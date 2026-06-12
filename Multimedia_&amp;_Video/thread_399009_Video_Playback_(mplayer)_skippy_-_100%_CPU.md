---
title: "Video Playback (mplayer) skippy - 100% CPU"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by lodp on 2007-04-01
Hi everyone,

For a couple of weeks now, I've been struggling with a problem for a couple of weeks now, before that everything was working very well.

When I play videos using kmplayer or kplayer, CPU usage is very high from the beginning -- usually around 70%. When I turn to full screen, often it climbs to 100% after a while, and playback becomes very skippy. It's even worse with Xine Movie Player.

How do I find out more about this? It used to be fine until a couple of weeks ago. CPU usage was much lower (I believe -- I never had any reason to check up on it). My graphics card is an ATI Mobility Radeon, and I'm using the proprietary fglrx driver, If that's relevant in any way.

I would appreciate anything you could point me to..

---

### Post by sakal on 2007-04-07
I have a similar problem and if a switch to full screen the picture is not smooth it looks like software rendered. If i use beryl CPU usage goes almost to zero and the picture is smooth (HW accelerated)

---

### Post by krussell on 2007-04-08
Hello :-)
Check the video driver in Mplayer Preferences Video Tab. Generally "xv" works best with lowest memory. Also enable 'Direct Rendering", disable "Frame Dropping", and in Misc Tab enable "Auto Sync with value 30, and enable Cache with value 128. This should solve the problem in mplayer. For Gxine, i don't know.

---

### Post by sakal on 2007-04-08
Hi,

problem is that mplayer does not work at all! I have done all the settings but if i try to play a video
mplayer window goes black for 1s then mplayer logo appears and nothing happens. I think Mplayer never worked its NOT due to your setting.
Do you have any idea ? THX for HELP!

---

### Post by krussell on 2007-04-08
Hello :-)
I have downloaded mplayer source from their original web site ([www.mplayerhq.hu](www.mplayerhq.hu)) and compiled it. You have used the mplayer from ubuntu respository. So i can suggest its worth to give a try with the original source. 

(1) Go to mplayer website and download the source. Unzip the source and open console in the    unzipped directory (or go to the unzipped directory in console). 
Now in the colsole give the following commands:
./configure --enable-gui
make
make install (as super user)

(2) Download one skin from mplayer website and unzip the skin and copy it in the /usr/local/share/mplayer/Skin directory and change the name of the skin folder as 'default'
Download one font file from mplayer web site and copy the unzipped contect into /usr/local/share/mplayer/Font.

Now run gmplayer and enjoy!

To get the full codec/sound support you'd also like to install different libraries and codecs from ubuntu repository. after each install, remember to reinstall mplayer to get the full functionality.

---

### Post by sakal on 2007-04-08
Hallo,

all done and i get the error:

[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not readable.
Skin not found (default).

here are all *.png files extracted /usr/local/share/mplayer/skins/default/skin/Ater
 i have alred try to change permissions with chmod (in MC) to R/W under SU account same

---

### Post by sakal on 2007-04-08
SORRY fixed it (ahah i m stupid)!!

---

### Post by sakal on 2007-04-08
ok mplayer now mplayer starts but it cant play any movie ERROR:

AVI file format detected.
VIDEO:  [XVID]  624x352  12bpp  23.976 fps  1023.2 kbps (124.9 kbyte/s)
Clip info:
 Software: VirtualDub
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
Error opening/initializing the selected video_out (-vo) device.

++++++++++++++++++++++++++++++++++++++++++++++++++
root@Asus:/home/max/MPlayer-1.0rc1# xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present

root@Asus:/home/max/MPlayer-1.0rc1# mplayer -vo help
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2400  @ 1.83GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Available video output drivers:
        xv      X11/Xv
        x11     X11 ( XImage/Shm )
        xover   General X11 driver for overlay capable video output drivers
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        xvidix  X11 (VIDIX)
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        png     PNG file
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame

---

### Post by sakal on 2007-04-08
Hi,

ok so i could fix the problem with:

sudo aticonfig --overlay-type=Xv

but i still get no video on Mplayer with X11/xv if i use X11(Ximage/Shm) i get a smooth video
but i have these frames on fast camera movements. And CPU usage was increased from 5% to
30%. Maybe CPU rendered ??
thx for help

---

### Post by sakal on 2007-04-08
All solved here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

thx !!!

---

### Post by krussell on 2007-04-09
Cheers!!

---

### Post by nisseblink on 2007-05-23
> **sakal said:**
> All solved here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

thx !!!

It sure works! :D

---

