---
title: "Video Problem"
date: 2010-08-22
forum: Multimedia Software
---

### Post by Mortesins93 on 2010-08-22
Hello,
I have an Xubuntu 9.10 on my computer and I can't see any videos. I tried installing the recommended libraries from the **Comprehensive Multimedia & Video Howto **thread but it still doesn't work. Neither VLC nor Totem work, I can only hear sound. The only program which works is Avidemux which I have been using for about 6 months or so and it works great but it can't open as many video files as VLC. What should I do? I would really like using VLC which works great on my other computers with Ubuntu.
Thanks in advance

---

### Post by cool Cpu on 2010-08-22
my dear berlusco :)

what pc do you have? what sound card what graphic card ?

sound and graphic should work it does on my laptop ati4850 and acl1200 ati hdmi

there is just issue with playing HD clips 

you could check dmesg if there are any issues check up what alsa or whatever sound driver do you have

---

### Post by corrytonapple on 2010-08-22
To install hardware drivers, go to the top of the screen, then to **System>Administration>Hardware Drivers**  and download and install any drivers for your sound or video card. See picture (I have no drivers  to install).

---

### Post by Mortesins93 on 2010-08-23
I don't have anything to install too. If it is really a driver problem why can I watch videos on Avidemux and on youtube??
To cool CPU:
First of all, what do you mean by berlusco
Second, I have an ASUS A4GA with an ATI mobility radeon 9700 at least that is what is says my laptop but if I enter sudo lshw this is what comes up:
id:display
                   description: VGA compatible controller                 product: RV350 [Mobility Radeon 9600 M10]                 vendor: ATI Technologies Inc                 physical id: 0
                 bus info: pci@0000:01:00.0
                 version: 00                 width: 32 bits                 clock: 66MHz                 capabilities: agp agp-3.0 pm bus_master cap_list                  configuration: latency=64 mingnt=8                 resources: memory:d0000000-d7ffffff(prefetchable) ioport:c800(size=256) memory:dfef0000-dfefffff memory:dfec0000-dfedffff(prefetchable)
 Is that my graphic card?? I attached my hardwareinfo file.
My sound card is AC'97 Sound Controller but it hasn't had any problems so far, as I already said I can hear the video but I can't see it.
Thank you all for the replies

---

### Post by Mortesins93 on 2010-08-23
Oh no I didn't upload my hardwareinfo file. Is there a way I can do it??

---

### Post by Mortesins93 on 2010-08-25
Anyone??

---

### Post by Mortesins93 on 2010-08-27
Please help, there is a particular video that I can't watch.

---

### Post by corrytonapple on 2010-08-27
Is it an application you are watching this video in? If you are watching in Firefox, use this:
Firefox Flash Extension Helper

---

### Post by no2498 on 2010-08-27
type smplayer in a terminal it tell you how to install it

it loads ff mpeg and some codes like the ones you need for mp4's


hope this helps

if they run slow try this it come from the program cheese



5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

### Post by Mortesins93 on 2010-09-02
Thank you for the advice but it doesn't work. Like all of the other players, I can hear the sound but there is no video.
I have tried all of these:
GNOME Mplayer
Mplayer
Movie Player (Totem, right?)
xine
VLC
but nothing. But I don't understand why only avidemux works. It is fine but ,as I said earlier, it doesn't open as many files as VLC.

---

### Post by tripmix on 2010-09-02
Do mplayer give you any errors when running it in a terminal "mplayer movie.avi" like can't open /dev/whatever or something? Does it make a difference if you run mplayer like this "mplayer -vo xv movie.avi" or "mplayer -vo gl movie.avi" or "sudo mplayer -vo fbdev movie.avi"?

---

### Post by Mortesins93 on 2010-09-02
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Guida_in_coppia-Giole_Dix.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [FMP4]  384x288  24bpp  25.000 fps  798.6 kbps (97.5 kbyte/s)
Clip info:
 Software: MEncoder SVN-r29237-4.4.1
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 32.0 kbit/2.27% (ratio: 4000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 384 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 384x288 => 384x288 Planar YV12 
A:   4.3 V:   4.4 A-V: -0.013 ct:  0.090 110/110  4%  0%  2.1% 0 0 
Exiting... (Quit)

This is what I get from "mplayer movie.avi" , so yes there is a problem with some /dev.

axel@axel-laptop:~/Videos$ mplayer -vo xv Guida_in_coppia-Giole_Dix.avi
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Guida_in_coppia-Giole_Dix.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [FMP4]  384x288  24bpp  25.000 fps  798.6 kbps (97.5 kbyte/s)
Clip info:
 Software: MEncoder SVN-r29237-4.4.1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 32.0 kbit/2.27% (ratio: 4000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 384 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 384x288 => 384x288 Planar YV12 
A:   6.1 V:   6.1 A-V: -0.027 ct:  0.090 154/154  3%  0%  2.0% 0 0 
Exiting... (Quit)

This is what I get with "mplayer -vo xv movie.avi" and there is a difference in what I get, but I still can only hear sound.

MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Motosega500.mpg.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [FMP4]  480x360  24bpp  25.000 fps  848.3 kbps (103.6 kbyte/s)
Clip info:
 Software: MEncoder SVN-r29237-4.4.1
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 32.0 kbit/2.27% (ratio: 4000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
waitpid(): No child processes
AO: [pulse] Init failed: Internal error
Failed to initialize audio driver 'pulse'
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 480 x 360 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0xa20240]using unscaled yuv420p -> rgb32 special converter
VO: [gl] 480x360 => 480x360 BGRA 
A:  12.2 V:  12.2 A-V: -0.008 ct:  0.088 305/305  6%  7%  1.8% 1 0 
Exiting... (Quit)

This is what I get with "mplayer -vo gl movie.avi", it actually works but with a certain file it quits after a bit.

axel@axel-laptop:~/Videos$ sudo mplayer -vo fbdev Guida_in_coppia-Giole_Dix.avi
[sudo] password for axel: 
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Guida_in_coppia-Giole_Dix.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [FMP4]  384x288  24bpp  25.000 fps  798.6 kbps (97.5 kbyte/s)
Clip info:
 Software: MEncoder SVN-r29237-4.4.1
Can't open /dev/fb0: No such file or directory
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 32.0 kbit/2.27% (ratio: 4000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
Home directory /home/axel not ours.
AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  35.3 (35.3) of 11629.7 ( 3:13:49.7)  1.9% 
Exiting... (Quit)

This is what I get with "sudo mplayer -vo fbdev movie.avi", the file doesn't quit but I only hear sound and the video window does not even show up.

Hope this helps, thanks a lot anyways.

---

### Post by Blue DaNoob on 2010-09-02
I don't know if this will help you, but I am having very similar problem. I have a netbook plugged into an external monitor. With the external monitor plugged in, I get no video - only sound. Unplug the external monitor, reboot, and everything works again. This just started happening to me - maybe within the last few software updates. The external monitor will play flash in the browser, but not video files on the computer... weird.

---

### Post by Mortesins93 on 2010-09-03
Thanks, I have a monitor plugged into my laptop too. I do this because my ASUS A4GA laptop's screen becomes white after a bit even if it is still working.

---

### Post by Mortesins93 on 2010-09-16
Anyone? I tried searching for proprietary drivers in the Applications>System>Hardware Drivers but it says.: " No proprietary drivers are in use on this system " and the list is blank. So would installing proprietary drivers solve my problem? Are there any monitor drivers I should install? By the way, a part from the video problem, my monitor screen becomes black if I try using some Windows games through wine, and only works if I press Ctrl Alt F1 on the "tty1" (also tty2,3,4,5,6 work). What should I do?

---

### Post by jrsy85 on 2010-10-06
I have had issues with drivers for 9600 pro since 9.04, for that machine (HP NC8000) I just have to keep Hardy running. This has only been my experience but a R300, R350 is legacy and isn't supported very well in the new versions of Xorg. I can get 2900fps in glxgears with hardy but nothing close to that in newer versions. I'm running this machine as an XBMC box on my 42" LCD at 1360x768 with no problems.

Cheers,
Joel

---

### Post by Mortesins93 on 2010-11-12
So I switched off my laptop screen using this code:
```
xrandr --output LVDS1 --off
```
referred to [this thread]("http://ubuntuforums.org/showthread.php?t=1541046")
Now I can watch videos on VLC. Thank you so much anyways.

---

