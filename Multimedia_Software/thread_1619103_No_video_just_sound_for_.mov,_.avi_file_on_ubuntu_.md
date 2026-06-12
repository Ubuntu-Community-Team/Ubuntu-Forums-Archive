---
title: "No video just sound for .mov, .avi file on ubuntu 10.04"
date: 2010-11-11
forum: Multimedia Software
---

### Post by beccax on 2010-11-11
When I use the default Totem Movie Player to watch .mov file (streaming from railscasts) either in browser or stand-alone, I just get sound but no video. If I try to watch .avi file, same thing, sound but no video.

I've already tried all the obvious solutions:
1) [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) -> I read and installed the codecs using "sudo apt-get install w32codecs"
2) I tried installing mplayer, it does the same thing as Totem Movie Player, just slower on the commandline.  Again sound but no picture.
3) I looked into VLC [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html) but it says the default 1.0.6 version doesn't work for ubuntu 10.04 and I should manually install 1.1 but doesnt' tell me how.
4) I tried installing the restricted extras: sudo apt-get install ubuntu-restricted-extras
5) I tried rebooting my machine.

Any idea why it's not working and what else can I try?

I'm on a netbook eeePC 1200 in case you need that also.

Many thanks in advance!
R

---

### Post by SeijiSensei on 2010-11-11
First off, do you have the same problems if you don't try to view streams but open a local .mov or .avi as well?  How about .mkv files? 

Now let's turn to your video card.  My daughter has a 1201N with an Nvidia card which works fine with the proprietary drivers from Ubuntu. So I'd start by running the "Hardware Drivers" application and see whether Ubuntu detects an Nvidia card and offers to install the proprietary driver for you.  If so, follow the instructions to install the driver.

Next, I'd install smplayer, which is a terrific GUI for mplayer.  After it's installed, go to Options > Preferences and click on the Video tab to see what video drivers you have available.  If you installed the proprietary Nvidia driver, I'd use the VDPAU video driver.  If not, try using "xv".  If you don't see any entries in the drop-down control, just type "vdpau" in the box if you have Nvidia or "xv" if you don't.  How are we doing now?

As far as I know, Medibuntu is pretty much deprecated these days.  I just include the restricted extras repository and have access to all the codecs I need.

---

### Post by beccax on 2010-11-11
Thanks so much for responding.

>First off, do you have the same problems if you don't try to view streams but open a local .mov or .avi as well?  How about .mkv files? 

I tried but can't view the .mov file locally either. same problem: just sound but no video.

> Now let's turn to your video card.  My daughter has a 1201N with an Nvidia card which works fine with the proprietary drivers from Ubuntu. So I'd start by running the "Hardware Drivers" application and see whether Ubuntu detects an Nvidia card and offers to install the proprietary driver for you.  If so, follow the instructions to install the driver.

I ran 'Hardware Drivers', but it says no proprietary driver exists.  How do I tell if it has an Nvidia card or not?

> Next, I'd install smplayer, which is a terrific GUI for mplayer.  After it's installed, go to Options > Preferences and click on the Video tab to see what video drivers you have available.  If you installed the proprietary Nvidia driver, I'd use the VDPAU video driver.  If not, try using "xv".  If you don't see any entries in the drop-down control, just type "vdpau" in the box if you have Nvidia or "xv" if you don't.  How are we doing now?

Should I proceed to do this without worrying about the proprietary drivers?


> As far as I know, Medibuntu is pretty much deprecated these days.  I just include the restricted extras repository and have access to all the codecs I need.[/QUOTE]

O good to know. I've installed restricted extras already, but didn't seem to solve the problem.  

R

---

### Post by cotcot on 2010-11-11
Maybe starting totem or smplayer in terminal gives an useful error about the video codec ?

---

### Post by beccax on 2010-11-11
Thanks! Tried it on the commandline, no error:

becca@netbook1:~/Downloads$ totem sample_iTunes.mov
becca@netbook1:~/Downloads$

---

### Post by cotcot on 2010-11-12
Seems to be an iTunes issue. Some proprietary codec or protection from Apple.

---

### Post by SeijiSensei on 2010-11-12
> **cotcot said:**
> Maybe starting totem or smplayer in terminal gives an useful error about the video codec ?

Actually running mplayer with the "-identify" option from the command line is more informative.  Try "mplayer -identify sample_iTunes.mov" and see what you get.  If that's not sufficiently informative, you can use "mplayer -v" but be ready for a LOT of output.

Some iTunes files are encrypted, but that wouldn't explain why she can't watch an AVI.

---

### Post by beccax on 2010-11-12
Thanks Cotcot.  Here's the result.  It mentioned something about not being able to access some file.  So I tried sudo but same result, so looks like maybe the directories are just not there. 

There's a lot of info.  Not sure what's the relevant line here.

becca@netbook1:~$ sudo mplayer -identify ~/Downloads/*.mov
[sudo] password for becca: 
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/becca/Downloads/sample_iTunes.mov.
libavformat file format detected.
ID_VIDEO_ID=0
[lavf] Video stream found, -vid 0
ID_AUDIO_ID=1
[lavf] Audio stream found, -aid 1
VIDEO:  [mp4v]  640x480  32bpp  10.000 fps    0.0 kbps ( 0.0 kbyte/s)
ID_FILENAME=/home/becca/Downloads/sample_iTunes.mov
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=mp4v
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=640
ID_VIDEO_HEIGHT=480
ID_VIDEO_FPS=10.000
ID_VIDEO_ASPECT=1.3333
ID_AUDIO_FORMAT=255
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=32000
ID_AUDIO_NCH=1
ID_LENGTH=85.54
ID_SEEKABLE=1
ID_CHAPTERS=0
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] This driver only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5.
[VO_3DFX] Unable to open /dev/3dfx.
[VO_XV] Could not grab port 85.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
ID_VIDEO_CODEC=ffodivx
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 32000 Hz, 2 ch, s16le, 128.0 kbit/12.50% (ratio: 16000->128000)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=32000
ID_AUDIO_NCH=2
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 32000Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=faad
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.3333
VO: [xv] 640x480 => 640x480 Planar YV12 
No bind found for key 'MOUSE_BTN0'.                         4% 1 0 
No bind found for key 'MOUSE_BTN0'.                         5% 1 0 
No bind found for key 'MOUSE_BTN0'.                         5% 1 0 
No bind found for key 'MOUSE_BTN2'.                         5% 1 0 
No bind found for key 'MOUSE_BTN0'.                         5% 1 0 
No bind found for key 'MOUSE_BTN2'.                         5% 1 0 
No bind found for key 'MOUSE_BTN0'.                         5% 1 0 
No bind found for key 'MOUSE_BTN2'.                         4% 1 0 
No bind found for key 'MOUSE_BTN0'.                         4% 1 0 
No bind found for key 'MOUSE_BTN2'.                         4% 1 0 
No bind found for key 'MOUSE_BTN2'.                         3% 1 0 
No bind found for key 'MOUSE_BTN0'.                         2% 1 0 
No bind found for key 'MOUSE_BTN0'.                         2% 1 0 
A:  23.3 V:  23.3 A-V:  0.000 ct:  0.032   0/  0  4%  0%  2.2% 1 0 
Exiting... (Quit)
ID_EXIT=QUIT

---

### Post by beccax on 2010-11-12
O, I should add I found out I can play .m4v file just fine.  How strange.

---

### Post by SeijiSensei on 2010-11-12
You seem like you're fairly experienced with *nix.  If you know how to compile, maybe you should trying building your own copy of mplayer and see how that works out.

See: [http://ubuntuforums.org/showpost.php?p=9943493&postcount=10](http://ubuntuforums.org/showpost.php?p=9943493&postcount=10)

But you might need to do this first: [http://ubuntuforums.org/showthread.php?t=1584707](http://ubuntuforums.org/showthread.php?t=1584707)

After "./configure; make; sudo make install" the application will be placed under the /usr/local branch.

To use this binary in smplayer, replace the entry "mplayer" with "/usr/local/bin/mplayer" in Options > Preferences > General.

---

### Post by andrew.46 on 2010-11-15
Hi beccax,

I imagine your sample file is [this one]("http://km.support.apple.com/library/APPLE/APPLECARE_ALLGEOS/HT1211/sample_iTunes.mov")? The svn MPlayer has no trouble with this file (screenshot attached) which actually is a pretty simple one, being mpeg4 video and aac sound wrapped in a mov container. Perhaps you could experiment by using a different video out device? Something like the following might be a good start:

```
mplayer -vo x11 /home/becca/Downloads/sample_iTunes.mov
```

x11 is not ideal by any means but it might demonstrate if you simply have some trouble with the default xv video out.

Andrew

---

