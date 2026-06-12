---
title: "No video in mplayer"
date: 2008-04-24
forum: Multimedia Software
---

### Post by ferrelas on 2008-04-24
When I try to play something in mplayer it gives no video output. I have tried both avi and mkv files with the same result. This is what it says when I try to play:

```
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  704x396  12bpp  23.976 fps  825.5 kbps (100.8 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2542/release)
 Name: Ghost Hound - 20 - Shaman's District
 Copyright: #Shinsen-Subs @ irc.rizon.net
Can't open /dev/fb0: No such file or directory
[fbdev2] Can't open /dev/fb0: No such file or directory
VO: [v4l2] No such file or directory
vo_cvidix: No vidix driver name provided, probing available ones (-v option for details)!
[cyberblade] Error occurred during pci scan: Operation not permitted
[mach64] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[nvidia_vid] Error occurred during pci scan: Operation not permitted
[pm3] Error occurred during pci scan: Operation not permitted
[radeon] Error occurred during pci scan: Operation not permitted
[rage128] Error occurred during pci scan: Operation not permitted
[s3_vid] Error occurred during pci scan: Operation not permitted
[SiS] Error occurred during pci scan: Operation not permitted
[unichrome] Error occurred during pci scan: Operation not permitted
[VO_SUB_VIDIX] Couldn't find working VIDIX driver.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 704 x 396 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [null] 704x396 => 704x396 Planar YV12
```

---

### Post by Periswell on 2008-04-24
im not sure if this is right but i dont get any playback when im running beryl. so if you are running beryl then i surrgest you turn it off.

just a guess

-josh

---

### Post by ferrelas on 2008-04-24
I have not installed beryl so unless it installs with ubuntu and is running by default I'm not running it. If it is, can you tell me how to turn it off?

Audio works fine if that is any help.

---

### Post by Canis familiaris on 2008-04-24
To turn off Beryl, right click on Beryl icon on the taskbar and choose Metacity.


TO turn off Compiz Fusion:
Go to System->Preferences->Appearance

Go to Visual Effects Tab and Select NONE

---

### Post by Canis familiaris on 2008-04-24
Yes Compiz/Beryl gives problems with Video

---

### Post by Archmage on 2008-04-24
> **ferrelas said:**
> 
```
VO: [null] 704x396 => 704x396 Planar YV12
```

If I'm reading this right, you mplayer is config to use for videoutput nothing.

Try to start the mplayer with the -vo gl2 (or -vo gl) switch. If this is the case, then change the .mplayer/config file.

---

### Post by ferrelas on 2008-04-24
As I suspected mplayer being configured to use null as vo was not the problem, rather it seems like it is using null because all else fails (or something). This is what I get when I try to force it with the -vo option:

```
Error opening/initializing the selected video_out (-vo) device.
```

I tried both gl, gl2 and x11 (the ones I could remember). Also turning off visual effects did nothing and I don't even think I have beryl at all.

Btw, how do I get to the config file? I'd like to take a look at it and maybe modify it a little.

---

### Post by ferrelas on 2008-04-24
I look into it a bit more and it seems I have no /dev/fb0 at all. This makes this msg seem kinda reasonable:

```
Can't open /dev/fb0: No such file or directory
```


 Is this normal and if it isn't what could be wrong and how to fix it?

---

