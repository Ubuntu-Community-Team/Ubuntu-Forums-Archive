---
title: "Video/audio &quot;plays&quot; without actually playing - 9.10."
date: 2009-10-16
forum: Multimedia Software
---

### Post by tim22b on 2009-10-16
When I try to open a song in Rhythmbox or a video in Totem and click the play button, the player acts like I clicked play (for instance, in Totem, the play button turns to a pause button), but the media doesn't actually play.  In Rhythmbox, the slider sits at the beginning of the progress bar and in Totem, the slider does the same thing and the video sits at the first frame.  If I move the slider over, I can see the frame I moved it to, but it still doesn't play.

A week ago I had to reinstall Ubuntu, so I backed up home, and redid the entire drive.  Started with the 7.10 Live CD, and upgraded all the way up to 9.10, so everything should be fresh.

The stuff in the Examples directory in my home directory do the same things so I don't think it's a codec problem (I *do* have the gstreamer codecs installed though).  I ran a video with totem from terminal and after a couple of seconds of not saying anything it spit this out 4 times:


[FONT="Courier New"](totem:4388): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;[/FONT]


For audio there doesn't appear to be a similar output.

The file types in the Examples folder are ogv, oga, and spx.

Any ideas?

---

### Post by nos09 on 2009-10-16
its a bug. go ahead and report it, and for now you can remove them and try to reinstall them form synaptic.
see if that works and please let me know.

---

### Post by HappyFeet on 2009-10-16
> **tim22b said:**
>  Started with the 7.10 Live CD, and upgraded all the way up to 9.10, so everything should be fresh.


That's probably your problem right there. Most people are lucky to upgrade once without problems, and you just did 4 upgrades back to back. Why didn't you just download 9.10 and do a clean install? I would hardly call 4 upgrades in a row "fresh".

---

### Post by tim22b on 2009-10-16
> **HappyFeet said:**
> That's probably your problem right there. Most people are lucky to upgrade once without problems, and you just did 4 upgrades back to back. Why didn't you just download 9.10 and install fresh?

Honestly, I didn't have a CD to use.  If there's a way to do it without that, I'm open to suggestions.  I guess I'll go explore a little.


Other than that, are there any other ideas?`

---

### Post by Marc Higgins on 2009-10-18
I have the same issue on my Dell Inspiron 640m (AKA Dell E1405). I upgraded to Karmic as well.

The audio track plays but the video does not. It is the same in Totem, VLC, Mplayer Flash videos play OK in the bowser.

Before I post this as a bug i would like to understand the problem better. There is nothing obvious looking at dmesg. I suspect it is an intel graphics issue

If you could also post the output of a lspci & the output you receive when you try to play a movie from the command line it might help nail down what the problem is & at least provide more information for when we post this as a bug

__________________________________________________________________________++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

marc@dell-640m:~/Desktop$ vlc Leaving.wmv 
VLC media player 1.0.2 Goldeneye
[0x97c7690] main interface error: no interface module matched "globalhotkeys,none"
[0x97c7690] main interface error: no suitable interface module
[0x9721140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9721140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1


marc@dell-640m:~/Desktop$ vlc Great\ Story.wmv 
VLC media player 1.0.2 Goldeneye
[0x87341d0] main interface error: no interface module matched "globalhotkeys,none"
[0x87341d0] main interface error: no suitable interface module
[0x868e140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x868e140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xb7301eb8] main decoder error: no suitable decoder module for fourcc `wmap'.
VLC probably does not support this sound or video format.
QPainter::begin: Paint device returned engine == 0, type: 1


This text desplays in the gui interface;

No suitable decoder module:
VLC does not support the audio or video format "wmap". Unfortunately there is no way for you to fix this.
__________________________________________________________________________
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

marc@dell-640m:~/Desktop$ mplayer Leaving.wmv 
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Leaving.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV2]  320x240  24bpp  1000.000 fps  143.0 kbps (17.5 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv2] vfm: ffmpeg (FFmpeg WMV2/WMV8)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 64.0 kbit/4.54% (ratio: 8005->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x240 => 320x240 Planar YV12 

__________________________________________________________________________
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

marc@dell-640m:~/Desktop$ mplayer Great\ Story.wmv 
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Great Story.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 31
VIDEO:  [WMV3]  480x360  24bpp  1000.000 fps  360.0 kbps (43.9 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
[VO_XV] Could not grab port 85.
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 480 x 360 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 480x360 => 480x360 Planar YV12 
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 44100 Hz, 2 ch, s16le, 48.0 kbit/3.40% (ratio: 6003->176400)
Selected audio codec: [wma9dmo] afm: dmo (Windows Media Audio 9 DMO)
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...

__________________________________________________________________________
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

marc@dell-640m:~/Desktop$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

### Post by akplm on 2009-10-25
Hello,
i installed KArmic and I have the same problem but just with totem! i tryed to re-install it with synaptica but it's the same!

---

### Post by Anubis on 2009-11-01
Maybe this thread is related?

[http://ubuntuforums.org/showthread.php?p=8211992#post8211992](http://ubuntuforums.org/showthread.php?p=8211992#post8211992)

---

### Post by TheShader on 2009-11-02
I have exactly the same problem. I made a fresh install of Ubuntu 9.10 from the CD and everything is up to date... :/

[img]http://www.roflcat.com/images/cats/270911980_0baa512314.jpg[/img]

---

### Post by TheShader on 2009-11-02
*bump*

---

### Post by lokutus25 on 2009-11-15
Same problem here. After upgrade from 9.04 to 9.10, Totem doesn't play videos or it play them without audio . But VLC and mplayer play correctly the same videos. I think that VLC use ALSA and works fine while Totem use pulseaudio and maybe need some configuration fix that I'm missing.
Still looking for solution...;)

---

### Post by lokutus25 on 2009-11-29
Bump?!

---

