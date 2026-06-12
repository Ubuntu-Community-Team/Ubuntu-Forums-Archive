---
title: "No HDMI Audio with Radeon HD3650"
date: 2010-02-07
forum: Multimedia Software
---

### Post by MrDelish on 2010-02-07
I just got my TV set up to use HDMI video (my Olevia TV had a "crop" setting that was turned on for some stupid reason) with my Radeon HD3650 and fglrx. I have an integrated Intel sound card and USB interface that work just fine. Here are is the output from *aplay -l*:

```
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: MobilePre [MobilePre], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

*cat /proc/asound/modules* returns the following:

```
 0 snd_hda_intel
 1 snd_usb_audio
 2 snd_hda_intel
```

I also tried disabling the other cards and editing some xorg.conf settings to no avail. I'm using a DVI to HDMI cable that *should* pass the audio, but this hasn't been fully tested. I'm not sure what I should try next to get HDMI audio working.

Any suggestions are welcome.

---

### Post by markbuntu on 2010-02-07
What app are you using to play the video?
Have you set that up to use the hdmi?

---

### Post by MrDelish on 2010-02-07
All I've done so far besides try to use it for the system sound is use the ALSA test to see if it will even output sound (per [http://alsa.opensrc.org/index.php/DigitalOut):](http://alsa.opensrc.org/index.php/DigitalOut):)

```
$ speaker-test -D hw:2,0

speaker-test 1.0.20

Playback device is hw:2,0
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
^C
```

If I recall correctly, it USED to say that the device was not recognized, so one of my recent changes may have made a difference... I'll try to see if Mplayer does any output and report the results in a few minutes.

---

### Post by MrDelish on 2010-02-07
Just ran *mplayer -ao alsa:device=hw=2.0 video.avi* and it still doesn't go through:

```
Playing vijeo.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [MJPG]  640x480  24bpp  30.000 fps  14934.3 kbps (1823.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG)
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 1 ch, s16le, 705.6 kbit/100.00% (ratio: 88200->88200)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
[AO_ALSA] alsa-lib: pcm_hw.c:1327:(snd_pcm_hw_open) open /dev/snd/pcmC2D0p failed: Device or resource busy
[AO_ALSA] Playback open error: Device or resource busy
Failed to initialize audio driver 'alsa:device=hw=2.0'
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar 422P)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 422P as output csp (no 1)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0xe6ff60]BICUBIC scaler, from yuv422p to yuv420p using MMX2
[swscaler @ 0xe6ff60]using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0xe6ff60]using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0xe6ff60]using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0xe6ff60]640x480 -> 640x480
VO: [xv] 640x480 => 640x480 Planar YV12 
V:   4.5 135/135  7%  5%  0.0% 0 0 
V:  21.4 643/643  7%  5%  0.0% 0 0 
  =====  PAUSE  =====

```

---

### Post by markbuntu on 2010-02-07
The device is busy because something else has already grabbed it, most likely pulseaudio. You should try running mplayer through pulseaudio, or suspending pulseaudio when you run mplayer by using pasuspender.

---

### Post by MrDelish on 2010-02-07
Pretty much the same thing and still no audio:

```
$ pasuspender -- mplayer alsa:device=hw=2.0 video.avi
MPlayer SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing alsa:device=hw=2.0.
File not found: 'alsa:device=hw=2.0'
Failed to open alsa:device=hw=2.0.


Playing video.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x336  12bpp  23.976 fps  828.9 kbps (101.2 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
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
VDec: vo config request - 640 x 336 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.90:1 - prescaling to correct movie aspect.
VO: [xv] 640x336 => 640x336 Planar YV12 
A: 102.6 V: 102.6 A-V: -0.003 ct: -0.000 2462/2462  1%  0%  0.3% 0 0 
Exiting... (Quit)
```

Also tried the following with some slightly different results:

```
$ pasuspender -- mplayer -ao alsa:device=hw=2.0 video.avi
MPlayer SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing video.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x336  12bpp  23.976 fps  828.9 kbps (101.2 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[AO_ALSA] alsa-lib: pcm_hw.c:1327:(snd_pcm_hw_open) open /dev/snd/pcmC2D0p failed: Device or resource busy
[AO_ALSA] Playback open error: Device or resource busy
Failed to initialize audio driver 'alsa:device=hw=2.0'
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
VDec: vo config request - 640 x 336 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.90:1 - prescaling to correct movie aspect.
VO: [xv] 640x336 => 640x336 Planar YV12 
V:  18.5 445/445  1%  0%  0.0% 0 0 
Exiting... (Quit)
```

---

### Post by gammalam on 2010-02-08
may be try this 
pasuspender -- mplayer alsa:device=hw=0.3 video.avi

change "2.0" to 0.1, 0.2 or 0.3

---

### Post by MrDelish on 2010-02-09
> **gammalam said:**
> may be try this 
pasuspender -- mplayer alsa:device=hw=0.3 video.avi

change "2.0" to 0.1, 0.2 or 0.3

Yeah, now that I reread the instructions I'm pretty sure that I had the subdevice number confused with the actual device number. I'll have to try some different combinations including what you suggest and report the results if something works.

Thanks.

---

### Post by markbuntu on 2010-02-10
You need to use hw:2,3 (hw:card,device)

---

### Post by MrDelish on 2010-02-10
So I noticed that a USB headset now gets picked up as the default card, so I tried 

```
pasuspender -- mplayer alsa:device=hw=3.3 video.avi
```

since the *aplay -l* output included

```
card 3: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
```

... but no joy. I also got this with the basic ALSA test:

```
$ speaker-test -D hw:3,3

speaker-test 1.0.20

Playback device is hw:3,3
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Channels count (1) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument

```

Same thing goes for *pasuspender -- speaker-test -D hw:3,3*. I've got the audio working fine with another card, but any more suggestions wouldn't hurt since I'd like to use HDMI instead.

---

### Post by lsu_guy on 2010-02-20
I got mine working by using xorg-edgers

[https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers)
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

It does involve getting a new kernel thought. I'm using my box for myth so I had some screwy things happen with a new kernel (like LIRC not working). I got it working by compiling it myself.

If you are not using any special apps like that and you just want audio, you can download a new kernel and install the radeon drivers from there. Instructions on the wiki will also help you with that.

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

If you do end up doing this, you will need the following in your xorg file

```

Section "Device"
	Identifier	"Default Device"
        Driver   "radeonhd"
        Option   "DRI" "on"   #this is the default in recent radeonhd versions
        Option   "AccelMethod" "EXA" #this is the default in recent radeonhd versions
	Option "MigrationHeuristic" "greedy"
	Option "AccelDFS" "true"
	Option "EnablePageFlip" "true"
	Option "EnableDepthMoves" "true"
        Option "HDMI" "all"
	Option "Audio" "On"
	Option "Audio" "true"
EndSection

```

---

