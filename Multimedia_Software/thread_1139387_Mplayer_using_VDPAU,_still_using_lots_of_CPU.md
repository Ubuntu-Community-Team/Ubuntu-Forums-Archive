---
title: "Mplayer using VDPAU, still using lots of CPU"
date: 2009-04-27
forum: Multimedia Software
---

### Post by djbon2112 on 2009-04-27
Hello everyone. I'm trying to make use of VDPAU on my laptop because the processor is not what you'd call the best (2.0 GHz Core 2 Duo). The video card is an nVidia 8600M GT. Using 9.04 Jaunty, fresh install.

I have the latest restricted driver in the Jaunty repos (180.44) which is the most current and I know supports VDPAU with my card. I followed the directions [HERE]("http://blog.avirtualhome.com/2009/02/10/compile-mplayer-with-vdpau-support-on-ubuntu/") to compile Mplayer with VDPAU. However, upon playing a video (using either mplayer or gmplayer), my CPU usage is still maxed out on one core, and my GPU doesn't seem to be used at all (its temperature stays the same). I've set the driver as VDPAU on both. Anyone have any advice? I'd really like to watch some HD movies on my laptop!

---

### Post by inobe on 2009-04-27
why don't you install the latest 180.51 driver ?

there are regression issues with 180.44 !

edit: in fact' you don't even need to manually install them manually, take a break rather.

[http://ubuntuforums.org/showpost.php?p=7154131&postcount=16](http://ubuntuforums.org/showpost.php?p=7154131&postcount=16)

---

### Post by djbon2112 on 2009-04-27
I'm updating the drivers now, but I probably won't check if they work or not until tomorrow. I'll let you know.

---

### Post by inobe on 2009-04-27
i will be here.

---

### Post by djbon2112 on 2009-04-27
Still nothing. I'm now using 180.51, but I still get the same issue.

It seems even though I've selected vdpau, it's using ffmpeg. Here's a sample output:

```
joshua@W01-Zeus:~$ mplayer -vo vdpau "<insert x264-encoded, mkv-container movie file here>"
...
Matroska file format detected.
VIDEO:  [avc1]  1280x536  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
```

I'm stumped. I compiled it to the letter, I'm using the latest nVidia driver, and I know my video card is supported. All my media files are x264-encoded (which is what VDPAU is supposed to assist in decoding), with a Matrotska container. I've tried about 20 different movies (I have a lot) and none of them work. They all say "ffmpeg".

---

### Post by mc4man on 2009-04-27
Don't have an capable card so never used but don't you need to also have a -vc option in your command?

There's a how to around somewhere on this forum, will edit in



[http://ubuntuforums.org/showthread.php?t=1037625&highlight=vdpau](http://ubuntuforums.org/showthread.php?t=1037625&highlight=vdpau)

---

### Post by inobe on 2009-04-27
just curious, why are you using mplayer, xine support vdpau very well.

here i found this thread [http://www.nvnews.net/vbulletin/showthread.php?t=124791](http://www.nvnews.net/vbulletin/showthread.php?t=124791)

there is a ton of information there, also notice it doesn't need ffmpeg.

it starts old and gets new

---

### Post by yoasif on 2009-04-27
if you want to enable vdpau for everything that it supports, input 

```

vo=vdpau,xv,
vc=ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,

```into your ~/.mplayer/config file. obviously you need to have a vdpau compatible build of mplayer and a vdpau compatible video driver.

---

### Post by djbon2112 on 2009-04-27
> **mc4man said:**
> Don't have an capable card so never used but don't you need to also have a -vc option in your command?

There's a how to around somewhere on this forum, will edit in



[http://ubuntuforums.org/showthread.php?t=1037625&highlight=vdpau](http://ubuntuforums.org/showthread.php?t=1037625&highlight=vdpau)

I followed that guide, and it works! I've got VDPAU when I use the command-line mplayer. However, my next question, is it possible to enable this with gmplayer (the GUI one) as well?

I've also never heard of xine, but I like mplayer, and since this works, I have no reason to change!

---

### Post by mc4man on 2009-04-27
> is it possible to enable this with gmplayer (the GUI one) as well?

Again I have no experience here and no way to try, though I'd think post 8 is relevant.
I probably wouldn't bother with gmplayer, smplayer seems more suited for this. 

 [link]("http://smplayer.sourceforge.net/")

---

