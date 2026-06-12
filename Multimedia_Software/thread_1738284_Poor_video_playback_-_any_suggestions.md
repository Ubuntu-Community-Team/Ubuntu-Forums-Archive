---
title: "Poor video playback - any suggestions?"
date: 2011-04-24
forum: Multimedia Software
---

### Post by Cheetah05 on 2011-04-24
I don't know what you call it because I have never had video problems before (I've come from Windows). I don't know if this is what people refer to a "choppy playback". Basically the video appears all blocky and you can see distinct areas updating with the new picture faster than the others...Really noticeable it fast-paced action.

Specification:
Core i3 350m
8GB RAM
Intel X25-M G2 80GB SSD
Nvidia GeForce 310m
Ubuntu 10.10

Video input: 720p MKV (not true 720p...file is compressed)
Using VLC player
< 30% CPU usage

Run from terminal I get this:
```

VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x116a120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7f8bf2fc7b20, 0x7f8bf2fc7a80)
Warning: call to signal(13, 0x1)
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
Warning: call to signal(13, 0x1)
Warning: call to srand(1303946973)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:2320): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
[***] Neither PlayResX nor PlayResY defined. Assuming 384x288
[***] fontconfig: Selected font is not the requested one: 'DejaVu Sans' != 'Clearly Gothic'

```

What could be causing this issue?

Thanks.

---

### Post by sikander3786 on 2011-04-24
Did you install the proprietary drivers for your Nvidia graphics card? If not, installing those should definitely improve the performance. Look under System > Administration > Additional Drivers and activate the 'Current' ones.

I am not sure if the drivers are available for the 310m chip. But if they are, they should pop-up in the additional drivers window.

---

### Post by Cheetah05 on 2011-04-24
> **sikander3786 said:**
> Did you install the proprietary drivers for your Nvidia graphics card? If not, installing those should definitely improve the performance. Look under System > Administration > Additional Drivers and activate the 'Current' ones.

I am not sure if the drivers are available for the 310m chip. But if they are, they should pop-up in the additional drivers window.

Already done.

Thanks for the suggestion though.

---

### Post by K_45 on 2011-04-24
Was this encoded properly? If you try to encode m720p with a low bitrate it will look like crap. Otherwise, try

```
sudo apt-get install mplayer
```

Then 

```
mplayer -vo x11 /path/to/file
``` 

and see what that does (path to file is the file you want to play)

---

### Post by Cheetah05 on 2011-04-24
The same video file works perfectly when viewing in Windows.

```

Creating config file: /home/me/.mplayer/config
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/1TB External Hard Drive/My Videos/File.mkv.
libavformat file format detected.
[aac @ 0x1eb7360]Duplicate channel tag found, attempting to remap.
[matroska @ 0x1e96910]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0
[lavf] stream 2: subtitle (unknown), -sid 0
VIDEO:  [H264]  1280x544  0bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 doctype: matroska
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [x11] 1280x544 => 1280x544 Planar YV12 
[swscaler @ 0x7f43ee529620]using unscaled yuv420p -> bgra special converter
A: 681.3 V: 681.3 A-V: -0.000 ct:  0.026   0/  0 32%  8%  3.8% 0 0 

MPlayer interrupted by signal 2 in module: decode_audio
A: 681.4 V: 681.3 A-V:  0.005 ct:  0.026   0/  0 32%  8%  3.9% 0 0 
Exiting... (Quit)

```

---

### Post by SeijiSensei on 2011-04-24
If you have the NVIDIA proprietary driver installed, you should try using VDPAU: "mplayer -vo vdpau /path/to/file.mkv".  The x11 driver is outdated.  If you can't get it to play with VDPAU, try "-vo xv" or "-vo opengl2".

I recommend installing **smplayer**, an excellent graphical front-end to mplayer that will let you control it's vast array of features using a GUI.

---

### Post by Cheetah05 on 2011-04-25
> **SeijiSensei said:**
> If you have the NVIDIA proprietary driver installed, you should try using VDPAU: "mplayer -vo vdpau /path/to/file.mkv".  The x11 driver is outdated.  If you can't get it to play with VDPAU, try "-vo xv" or "-vo opengl2".

Still got the same issue. **Could it be a graphics driver issue? Ie some settings with the graphics driver rather than how media player is outputting?**

It seems to happen alot in the face paced action bits and the CPU is under 30% like I said.

Just to be doubly sure its not the file...does anyone know of a 1080p stress-test file with lots of face-paced scenes?

Output from mplayer -vo vdpau:

```

ben@Ben-Laptop:~$ mplayer -vo vdpau "/media/1TB External Hard Drive/My Videos/file.mkv"
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/1TB External Hard Drive/My Videos/file.mkv.
libavformat file format detected.
[aac @ 0x2093360]Duplicate channel tag found, attempting to remap.
[matroska @ 0x2072910]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0
[lavf] stream 2: subtitle (unknown), -sid 0
VIDEO:  [H264]  1280x544  0bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 doctype: matroska
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [vdpau] 1280x544 => 1280x544 Planar YV12 
A: 692.2 V: 692.2 A-V:  0.000 ct:  0.064   0/  0 31%  3%  3.9% 0 0 

MPlayer interrupted by signal 2 in module: sleep_timer
A: 692.3 V: 692.3 A-V:  0.000 ct:  0.064   0/  0 31%  3%  3.9% 0 0 
Exiting... (Quit)

```

mplayer -vo vx &  mplayer -vo opengl2 = no display.

---

### Post by Cheetah05 on 2011-04-25
I've also found what my problem is....

apparently its called screen tearing: [http://en.wikipedia.org/wiki/Screen_tearing](http://en.wikipedia.org/wiki/Screen_tearing)

---

### Post by cchhrriiss121212 on 2011-04-25
Have you tried disabling compiz? Or enabling vsync in nvidia-settings?

---

### Post by Cheetah05 on 2011-04-25
> **cchhrriiss121212 said:**
> Have you tried disabling compiz? Or enabling vsync in nvidia-settings?

I shall try these now.

I  assume you mean the "Sync to VBlack" options, there are two of them - should I enable both? Also, surely this would only work if it detects my laptop screen correctly?

---

### Post by Cheetah05 on 2011-04-25
I disabled Compiz by going System->Preferences->Appearance->Visual Effects = None

I also enabled both VBlank options and 


**I'm still getting the issue.**

Thanks.

---

### Post by SeijiSensei on 2011-04-25
Try running "sudo nvidia-xconfig" if you haven't ever done so.  You'll then need to logout and either reboot, or choose the "Restart X server" option if it's available to you in a menu at the login screen.

---

### Post by Yellow Pasque on 2011-04-25
> **Cheetah05 said:**
> I disabled Compiz by going System->Preferences->Appearance->Visual Effects = None
And you still get high CPU load even with using mplayer and vdpau?

---

### Post by Cheetah05 on 2011-04-25
> **SeijiSensei said:**
> Try running "sudo nvidia-xconfig" if you haven't ever done so.  You'll then need to logout and either reboot, or choose the "Restart X server" option if it's available to you in a menu at the login screen.

Tried this...it doesn't help. Thanks for the suggestion.

> **Temüjin said:**
> And you still get high CPU load even with using mplayer and vdpau?

I'm not getting high CPU load (< 30%)....and much lower when using VDPAU. **The problem I am getting is screen/video tearing.**

EDIT:

Maybe its a placebo? I'm starting to think its just me now....I just watched some video in Windows and it appeared to tear aswell....maybe its got to the point where I am looking for it

---

### Post by SeijiSensei on 2011-04-25
> **Cheetah05 said:**
> Maybe its a placebo? I'm starting to think its just me now....I just watched some video in Windows and it appeared to tear aswell....maybe its got to the point where I am looking for it

Try some other 720p files then.  Maybe the file you have has encoding problems.  If it's a file you obtained from the Internet, there's no guarantee the encoder knew what he or she was doing.

---

### Post by Cheetah05 on 2011-04-26
> **SeijiSensei said:**
> Try some other 720p files then.  Maybe the file you have has encoding problems.  If it's a file you obtained from the Internet, there's no guarantee the encoder knew what he or she was doing.

I've tried other files which other people have vetted as being OK....I've checked MD5 sums to check I've downloaded it properly and stuff like that.

...guess it must just be me...

Thanks for the help everyone btw.

---

