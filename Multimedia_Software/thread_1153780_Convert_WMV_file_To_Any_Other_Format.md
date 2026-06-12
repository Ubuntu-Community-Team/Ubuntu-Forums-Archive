---
title: "Convert WMV file To Any Other Format"
date: 2009-05-09
forum: Multimedia Software
---

### Post by spikoley on 2009-05-09
[I have a .wmv file that will only play in mplayer and would like to convert it to any other format.  I have the w32codecs install, but the file does not play in VLC.  How can I find out what the wmv codec type so I can convert the file?  What format and program should I use to convert it?

Here are the details when opening the file with mplayer in the shell.

```

mplayer file01.wmv 
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing file01.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [MSS2]  800x600  24bpp  1000.000 fps   37.8 kbps ( 4.6 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] Could not grab port 57.
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:1440000  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: RGB8 RGB555 RGB565 RGB24 RGB32 
VDec: vo config request - 800 x 600 (preferred colorspace: Packed YUY2)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using BGRA as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0x896d370]SwScaler: BICUBIC scaler, from rgb32 to yuv420p using MMX2
[swscaler @ 0x896d370]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x896d370]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x896d370]SwScaler: using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0x896d370]SwScaler: 800x600 -> 800x600
VO: [xv] 800x600 => 800x600 Planar YV12 
Selected video codec: [wmsdmod] vfm: dmo (Windows Media Screen Codec 2)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [dmo] Win32/DMO decoders
GetOutput r=0x0   size:16384  align:1
StreamCount r=0x0  1  1
AUDIO: 22050 Hz, 1 ch, s16le, 20.0 kbit/5.67% (ratio: 2500->44100)
Selected audio codec: [wma9spdmo] afm: dmo (Windows Media Audio 9 Speech DMO)
==========================================================================
AO: [pulse] 22050Hz 1ch s16le (2 bytes per sample)
Starting playback...

```

The video plays fine but I would rather use VLC.  Any idea on what codec I need and how to make VLC use it?

---

### Post by andrew.46 on 2009-05-09
Hi spikoley,

The easiest way to get around this is to use MPlayer to convert the file to wav and then either play it that way with vlc or convert it to the format of your choice from there. Syntax would be:

```

mplayer file01.wmv -vc null -vo null -ao pcm:fast:waveheader:file=output.wav

```

If you are happiest using vlc it should be able to convert the file to ogg, flac, mp3 or whatever format you prefer.

All the best,

Andrew

**Edit:** Never mind I misread your question, this only deals with the audio of course. My apologies....

---

### Post by spikoley on 2009-05-10
> **andrew.46 said:**
> 
**Edit:** Never mind I misread your question, this only deals with the audio of course. My apologies....

Thanks for the reply.  Do you have any ideas on how to do this with video?  I tried it with mencoder and it converted, but it would crash VLC.

[code]mencoder file01.wmv -ofps 23.976 -ovc lavc -oac copy -o file01.avi[.code]

---

### Post by Sin@Sin-Sacrifice on 2009-05-10
Don't know what format you want it but avi would be easy with [http://anotherugly.wordpress.com/wmv2avi/](http://anotherugly.wordpress.com/wmv2avi/) There\'s several format2format programs out there to chose from... my favorite is flac2mp3.

---

### Post by collinp on 2009-05-10
In addition to the suggestions above, you could try the package soundconverter. Great GUI app.

---

### Post by andrew.46 on 2009-05-11
Hi spikoley,

> **spikoley said:**
> Thanks for the reply.  Do you have any ideas on how to do this with video?  I tried it with mencoder and it converted, but it would crash VLC.

```
mencoder file01.wmv -ofps 23.976 -ovc lavc -oac copy -o file01.avi
```

Try transcoding the sound as well, so rather than use '-oac copy' try something like:

```
-oac mp3lame -lameopts preset=standard
```

and perhaps vlc will be happier with this. Your copy of MEncode will need to have mp3 support though and this can be checked as follows:

```

andrew@skamandros~$ mencoder -oac help
MEncoder SVN-r29286-4.2.4 (C) 2000-2009 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   **[COLOR="Red"]mp3lame  - cbr/abr/vbr MP3 using libmp3lame[/COLOR]**
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   faac     - FAAC AAC audio encoder

```

If this is not in your copy grab MPlayer from the Medibuntu repository and this will work.

Hope this helps,

Andrew

---

### Post by spikoley on 2009-05-11
> **andrew.46 said:**
> Hi spikoley,



Try transcoding the sound as well, so rather than use '-oac copy' try something like:

```
-oac mp3lame -lameopts preset=standard
```

and perhaps vlc will be happier with this. Your copy of MEncode will need to have mp3 support though and this can be checked as follows:

```

andrew@skamandros~$ mencoder -oac help
MEncoder SVN-r29286-4.2.4 (C) 2000-2009 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   **[COLOR="Red"]mp3lame  - cbr/abr/vbr MP3 using libmp3lame[/COLOR]**
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   faac     - FAAC AAC audio encoder

```

If this is not in your copy grab MPlayer from the Medibuntu repository and this will work.

Hope this helps,

Andrew

Andrew you are the man!  It worked!  Thank you for the reply!

Here is the command I used.
```
mencoder file01.wmv -ofps 23.976 -ovc lavc -oac mp3lame -lameopts preset=standard -o file01.avi
```

---

### Post by mc4man on 2009-05-11
> I have the w32codecs install, but the file does not play in VLC

By default and apparently in many builds vlc will not use w32codecs for decoding various wma formats (in this case needed for wmas

It's actually quite trivial to enable vlc to use w32codecs, why it's not done I don't know. (should enable playback of almost all wma formats, the notable exception being only wmal atm

[http://ubuntuforums.org/showthread.php?p=7255538#post7255538](http://ubuntuforums.org/showthread.php?p=7255538#post7255538)

---

