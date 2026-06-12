---
title: "VDPAU under Jaunty Jackalope"
date: 2009-05-22
forum: Multimedia Software
---

### Post by SatanzJudge on 2009-05-22
What's the best and cleanest way to get [_VDPAU_]("http://en.wikipedia.org/wiki/VDPAU") running under Jaunty at the moment? 

I've compiled the latest mplayer version according to [_this tutorial_]("http://ubuntuforums.org/showthread.php?t=1081070"). It works but it's still a little bit fiddly to have to compile it yourself. Do binary packages of media players with VDPAU support already exist?

Thanks for any hint!

---

### Post by Arup on 2009-05-22
> **SatanzJudge said:**
> What's the best and cleanest way to get [_VDPAU_]("http://en.wikipedia.org/wiki/VDPAU") running under Jaunty at the moment? 

I've compiled the latest mplayer version according to [_this tutorial_]("http://ubuntuforums.org/showthread.php?t=1081070"). It works but it's still a little bit fiddly to have to compile it yourself. Do binary packages of media players with VDPAU support already exist?

Thanks for any hint!

I install Gnome Mplayer from the repos which in turns installs mplayer. Gnome Mplayer has option of enabling vdpau and after its enabled, CPU usage goes to to max4% with full screen HD movies on a nvidia card.

---

### Post by SatanzJudge on 2009-05-22
What about Totem or VLC?

---

### Post by Arup on 2009-05-22
> **SatanzJudge said:**
> What about Totem or VLC?

With VLC they are working on it but with Totem nothing yet.

---

### Post by Tumbledown on 2009-05-22
Hi there,
Im running 9.04 with the stock 180.44 driver.
I installed Gnome Mplayer, selected VDPAU as the video output
but all I get is the sound

Any thoughts??

Do I have to upgrade the driver?

CPU Core2Quad
GFX 8800GT

---

### Post by andrew.46 on 2009-05-22
Hi SatanzJudge,

> **SatanzJudge said:**
> What's the best and cleanest way to get [_VDPAU_]("http://en.wikipedia.org/wiki/VDPAU") running under Jaunty at the moment? 

I've compiled the latest mplayer version according to [_this tutorial_]("http://ubuntuforums.org/showthread.php?t=1081070"). It works but it's still a little bit fiddly to have to compile it yourself. Do binary packages of media players with VDPAU support already exist?

I am afraid that this guide, which I wrote, does not deal with vdpau for the poor reason that I do not have one of those fancy cards to play with :-). RVM has a [PPA for MPlayer]("https://launchpad.net/~rvm/+archive/mplayer") that I believe is vdpau enabled, but I am not 100% sure of this.

Alternatively there is a guide on these forums that deals with this:

HOWTO: Nvidia Driver + VDPAU + Smplayer +Mplayer
[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

One day I will get a computer better than this clunky old one I am typing on and experience the vdpau revolution :-).

Andrew

---

### Post by SatanzJudge on 2009-05-23
> **Tumbledown said:**
> Hi there,
Im running 9.04 with the stock 180.44 driver.
I installed Gnome Mplayer, selected VDPAU as the video output
but all I get is the sound

Any thoughts??

Do I have to upgrade the driver?

CPU Core2Quad
GFX 8800GT

I'm using the same driver (from the repository) so I guess you don't have to upgrade. Have you checked if your card supports VDPAU? This seems to be quite complicated since same models can have different chipsets, so I've heard. Maybe the video codec is not supported by Gnome Mplayer?

> **andrew.46 said:**
> 
I am afraid that this guide, which I wrote, does not deal with vdpau for the poor reason that I do not have one of those fancy cards to play with :-). RVM has a [PPA for MPlayer]("https://launchpad.net/~rvm/+archive/mplayer") that I believe is vdpau enabled, but I am not 100% sure of this.

Alternatively there is a guide on these forums that deals with this:

HOWTO: Nvidia Driver + VDPAU + Smplayer +Mplayer
[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

One day I will get a computer better than this clunky old one I am typing on and experience the vdpau revolution :-).

Andrew

Hi Andrew, thanks for the hints. Actually you don't need a fancy card for VDPAU. I just bought a **new** GF8400GS for 25EUR! Unbelievable!

---

### Post by Tumbledown on 2009-05-24
> **SatanzJudge said:**
> I'm using the same driver (from the repository) so I guess you don't have to upgrade. Have you checked if your card supports VDPAU? This seems to be quite complicated since same models can have different chipsets, so I've heard. Maybe the video codec is not supported by Gnome Mplayer?

Got the video to work after I installed the latest driver (180.51)
CPU now running at 2% from 10%.

Only challenge is that the audio is out of sync, feels like Im
watching a Bruce Lee film ;)

I just tried a h264 video I encoded and all audio is in sync.
The video that is out of sync is a 720p mov from the nasa site?? 
Strange!

any thoughts, Movs are supported right?

Im off to download some more and see if I can see any links

---

### Post by exploding5heep on 2009-06-02
I also have the issue where gnome-mplayer only plays back the sound and not the video when vdpau is selected as the output. Does anyone know why this happens? I am currently using a fresh install of 9.04 64bit. The only things I have done are updates through the update manager, and then a manual install of the 180.60 drivers, since using jockey to install the 180.44 drivers resulted in lots of crashing/trouble. Any help would be much appreciated.

---

### Post by Arup on 2009-06-02
> **Tumbledown said:**
> Hi there,
Im running 9.04 with the stock 180.44 driver.
I installed Gnome Mplayer, selected VDPAU as the video output
but all I get is the sound

Any thoughts??

Do I have to upgrade the driver?




CPU Core2Quad
GFX 8800GT



Have you installed FFMPEG codecs? Do a sudo apt-get install ffmpeg libavcodec-unstripped-52 w64codecs libdvdcss2

Make sure your medibuntu repos is enabled.

---

### Post by exploding5heep on 2009-06-02
I had forgotten to install those codecs, but I still get the same problem. Running mplayer at the command line gives this result:

```
mplayer -vo xv -vc ffh264vdpau /home/XXXXXXX/Desktop/Batman.Begins.2005.HD.DVDRip.1080p.x264.DD.5.1-AsdaBags.Sample.mkv 
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/XXXXXXX/Desktop/Batman.Begins.2005.HD.DVDRip.1080p.x264.DD.5.1-AsdaBags.Sample.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3) "Batman", -aid 0, -alang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x800  24bpp  23.972 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Forced video codec: ffh264vdpau
Cannot find codec matching selected -vo and video format 0x31637661.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  35.1 (35.0) of 35.4 (35.3)  1.5% 

Exiting... (End of file)

```

The computer I am doing this on is a lenovo T61 with a quadro NVS140M video card. Are there any compatibility issues with it?

---

### Post by krul on 2009-06-13
You probably do not have the right mplayer with vdpau support. I had a similar problem but was working again after using the mplayer from [ http://avenard.com/media/Ubuntu_Repository/Ubuntu_Repository.html ]( http://avenard.com/media/Ubuntu_Repository/Ubuntu_Repository.html )

---

