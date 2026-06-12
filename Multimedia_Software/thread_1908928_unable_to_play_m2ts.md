---
title: "unable to play m2ts"
date: 2012-01-14
forum: Multimedia Software
---

### Post by stephenbbb on 2012-01-14
latest vlc plays audio, while video is frozen. mplayer plays extremely slow.
looking at the details I saw mplayer reports fps: 30 while vlc reports 59.65
file is from Sony AVCHD and should be 60fps. mplayer has correct size 1920/1080 while vlc says 1440/1080

tried setting -fps from the command line , same delayed playback. now the kick in the gut:

scb@scb-Aspire-5250:~/Videos$ mplayer -fps 60 /home/scb/Videos/vid1.m2ts 
mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MPlayer SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/scb/Videos/vid1.m2ts.
TS file format detected.
VIDEO H264(pid=4113) AUDIO A52(pid=4352) SUB Teletext(pid=4608)  PROGRAM N. 1
FPS seems to be: 29.970030
Load subtitles in /home/scb/Videos/
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
FPS forced to be 60.000  (ftime: 0.017).
Starting playback...
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1440x1080 => 1920x1080 Planar YV12 
A:   3.6 V:   1.9 A-V:  1.761 ct: -0.057  52/ 52 401% 28% 16.6% 50 0 


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

A:  11.5 V:   4.7 A-V:  6.769 ct: -0.233 224/224 279% 13%  9.8% 219 0 
  =====  PAUSE  =====

Exiting... (Quit)

so system is too slow (Ubuntu 11.10), but it plays perfect in Win 7 !!!
hardware: amd dual C-50, amd radeon HD 6250, 2gb ddr3

pls advise if it is possible to check the radeon driver and maybe speed up things with the driver. Ubuntu seems to be much faster than Win 7 doing anything else, I cannot believe video playback should be different.

---

### Post by WasMeHere on 2012-01-14
Hi Stephen,

I am also playing around with high definition video, but from a Panasonic camera (MTS format). It plays, but not fast enough if there is a lot of motion in the video clip. I have nvidia graphics and need the built-in proprietary driver, which can use vdpau and hardware decoding via ***mplayer***. ***VLC*** is almost fast enough. On the same computer VLC is doing well in Windows XP. So I have similar experiences as you.

I have also a new TV, that can show 960x540-50p, 1280x720-50p, 1920x1080-30p and 1920x1080-50i (but not 1920x1080-50p, the best quality video produced by the camera). I can use ***ffmpeg*** to convert the MTS files to mp4 files encoded with x264. The resulting files are well compressed and play well on the TV. They also play well on PCs (up to a limit set by the graphics and processing power). Obviously smaller frame size (width x height) and slower frame rate makes it easier. If you want, I can post details about the script.

This question may be stupid: have you activated a proprietary driver? I know that there have been problems with Radeon graphics in linux, but that it works for some people and cards. I think that you might find some clues browsing the Ubuntu Forums and internet in general for linux and your particular graphics card.

Have fun finding out about linux :-)
Olle

---

### Post by stephenbbb on 2012-01-14
well, after checking graphics in the GUI it says: driver unknown, experience standard

will try to get a driver from radeon website.

fglrx driver installed and tests show 200 fps running great. however driver is not used. sysinfo says driver used is VESA wrestler.

how can I force the fglrx driver?? and where to look for why it refuses to use it??

---

### Post by shantiq on 2012-01-14
hi stephen    the only player that can handle such HD files is **smplayer** in your synaptic


with   options/preferences/video/vdpau



also from command line    mplayer should be fine too    but not mplayer gui


```
mplayer    nameoffile
```



last year i also had some good results with   1080p    with [**xbmc**]("http://www.google.co.uk/url?sa=t&rct=j&q=xbmc&source=web&cd=1&ved=0CDcQFjAA&url=http%3A%2F%2Fxbmc.org%2F&ei=2NIRT9SLEMWv8gOq5-3VAw&usg=AFQjCNEMqlJviAjiBVKI0EwCs_puv9nDAw&sig2=pLd1roytzilAkim1NAT__Q")

---

### Post by WasMeHere on 2012-01-14
> **stephenbbb said:**
> well, after checking graphics in the GUI it says: driver unknown, experience standard

will try to get a driver from radeon website.

fglrx driver installed and tests show 200 fps running great. however driver is not used. sysinfo says driver used is VESA wrestler.

[COLOR="Red"]how can I force the fglrx driver?? and where to look for why it refuses to use it??[/COLOR]

What about the video performance: did it change? I ask, because some software might not recognize that the new driver is installed. You might also need to restart your system. I guess that there is a proprietary tool to set the graphics mode, that comes with the driver. Have you found and used it?

[COLOR="Red"]Someone with experience of the fglrx driver, please come into this thread and help us![/COLOR]

---

### Post by stephenbbb on 2012-01-15
> **shantiq said:**
> hi stephen    the only player that can handle such HD files is **smplayer** in your synaptic


with   options/preferences/video/vdpau



also from command line    mplayer should be fine too    but not mplayer gui


```
mplayer    nameoffile
```

last year i also had some good results with   1080p    with [**xbmc**]("http://www.google.co.uk/url?sa=t&rct=j&q=xbmc&source=web&cd=1&ved=0CDcQFjAA&url=http%3A%2F%2Fxbmc.org%2F&ei=2NIRT9SLEMWv8gOq5-3VAw&usg=AFQjCNEMqlJviAjiBVKI0EwCs_puv9nDAw&sig2=pLd1roytzilAkim1NAT__Q")

I tried mplayer from command line with some of the suggested fixes in its own output, no luck.
smplayer is GUI for mplayer and freezes like vlc.

---

### Post by stephenbbb on 2012-01-15
> **Olle Wiklund said:**
> What about the video performance: did it change? I ask, because some software might not recognize that the new driver is installed. You might also need to restart your system. I guess that there is a proprietary tool to set the graphics mode, that comes with the driver. Have you found and used it?

[COLOR=Red]Someone with experience of the fglrx driver, please come into this thread and help us![/COLOR]

fglrx is actually active. running the test suite showed an error that the rendering method wasn't chosen.

i think it won't change anything as it is intended to speed up video from a game, where the pc is computing the images. the fglrx test shows a moving 3d image like from a game. video streaming is different (my understanding here is extremely shallow ) so I think it is a problem with the way mplayer runs h264. I checked supertux cart and the video was great, definitely better, so fglrx helps a lot in gaming.

another user suggested that windows is actually more efficient than linux in streaming video and maybe we have to live with that...

---

### Post by WasMeHere on 2012-01-16
> **stephenbbb said:**
> fglrx is actually active. running the test suite showed an error that the rendering method wasn't chosen.
...
another user suggested that windows is actually more efficient than linux in streaming video and maybe we have to live with that...

Yes, maybe we have to live with that, but I think that your graphics can be improved in linux. At least my experience with nvidia cards and chips is that the difference is fairly small: With a card that is one or two steps better (than what is sufficient with Windows) you will get good graphics rendering of your high definition video clips.

But as I wrote before, I wish someone with experience of Radeon graphics can help us. There might be some tweak that can make a big difference.

---

