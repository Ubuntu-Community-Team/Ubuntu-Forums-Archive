---
title: "video4linux sound problems"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by mrchaotica on 2007-05-04
I'm trying to set up a TV tuner in Ubuntu Feisty, and no matter what I do, I can't get the sound to work properly.

Hardware setup:
Motherboard & video: ASUS M2NPV-VM motherboard (nForce 430, geForce 6150)
TV tuner: Kworld Global TV Tuner (saa7134-based)

I'm using ALSA.

```
$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I've tried viewing TV using xawTV, TVtime, mplayer, and MythTV. In xawTV and TVtime I get no sound unless I use arecord:
```
$ arecord -D hw:2,0 -r 32000 -c 2 | aplay -
```
In which case the sound lags slightly behind the video. Of course, from what I read this is how it's supposed to work.

However, I *also* get no sound in mplayer, even though I'm specifying what I think is the correct device on the command line:

```
$ mplayer -tv driver=v4l2:norm=NTSC:adevice=hw2,0:amode=1:audiorate=232000:forceaudio:volume=100 tv://
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 75, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: V-Stream Studio TV Terminator
 Tuner cap: STEREO LANG1 LANG2
 Tuner rxs: MONO
 Capabilites:  video capture  video overlay  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = PAL; 1 = PAL-BG; 2 = PAL-I; 3 = PAL-DK; 4 = NTSC; 5 = SECAM; 6 = SECAM-DK; 7 = SECAM-L; 8 = SECAM-Lc; 9 = PAL-M; 10 = PAL-Nc; 11 = PAL-60;
 inputs: 0 = Television; 1 = Composite1; 2 = S-Video;
 Current input: 0
 Current format: BGR24
v4l2: current audio mode is : STEREO
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar YV12 
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
**Audio: no sound**
Starting playback...

```

And in MythTV I get high-pitched sound and dropped frames/lag (with both sound and video).

Can somebody please help, before I get fed up and return this stupid TV tuner card?!

---

### Post by stadt on 2007-05-05
After a long search I've finally managed to record from my SAA7134 based TV-card perfectly (a Terratec Cinergy 400).

Here's an example script:

mencoder -v tv:// -tv driver=v4l2:device=/dev/video0:input=0:alsa:width=384:height=288:chanlist=europe-west:channel=E5:adevice=hw.1:audiorate=32000:amode=1:forceaudio:immediatemode=0:norm=PAL:buffersize=64 -ovc lavc -lavcopts vcodec=mjpeg:aspect=720/576 -oac pcm -mc 0 -noskip -vf harddup -fps 25 -o test.avi

Comparing it to your mplayer options may show you what's going wrong (Hint: the device isn't capable to capture sound with an audiorate of 232000

Here my tvtime.xml cofiguration file (sound is perfect)

[COLOR="Blue"]<?xml version="1.0"?>
<!DOCTYPE tvtime PUBLIC "-//tvtime//DTD tvtime 1.0//EN" "http://tvtime.sourceforge.net/DTD/tvtime1.dtd">
<tvtime xmlns="http://tvtime.sourceforge.net/DTD/">
  <option name="DefaultBrightness" value="-1"/>
  <option name="DefaultContrast" value="-1"/>
  <option name="DefaultSaturation" value="-1"/>
  <option name="DefaultHue" value="-1"/>
  <option name="Norm" value="pal"/>
  <option name="PrevChannel" value="7"/>
  <option name="Channel" value="8"/>
  <option name="FramerateMode" value="0"/>
  <option name="OverScan" value="3.5"/>
  <option name="CheckForSignal" value="1"/>
  <option name="AudioBoost" value="100"/>
  <option name="AlwaysOnTop" value="0"/>
  <option name="QuietScreenshots" value="0"/>
  <option name="UnmuteVolume" value="24158"/>
  <option name="Muted" value="0"/>
  <option name="V4LInput" value="0"/>
  <option name="AudioMode" value="stereo"/>
  <option name="PalDKMode" value="0"/>
  <option name="DeinterlaceMethod" value="AdaptiveAdvanced"/>
  <option name="WideScreen" value="0"/>
<option name="Fullscreen" value="0"/><option name="Verbose" value="0"/><option name="WindowGeometry" value="0x576"/><option name="InputWidth" value="720"/><option name="V4LDevice" value="/dev/video0"/><option name="VBIDevice" value="/dev/vbi0"/><option name="Frequencies" value="europe"/><option name="MixerDevice" value="/dev/mixer:line"/><option name="XMLTVFile" value="none"/><option name="XMLTVLanguage" value="german"/><option name="ProcessPriority" value="-10"/></tvtime>[/COLOR]

Hope this helps

---

### Post by mrchaotica on 2007-05-06
Aha, thanks! Trying your mplayer incantation (after changing the cable settings for my USian locale) worked. It turns out the problem was the lack of "immediatemode=0" in my version. Oh, by the way -- I wasn't really trying to use that high audiorate; that was a typo.

So now, viewing TV with mplayer works. However, TVtime still doesn't, even though I tried your tvtime.xml file (only changing norm to "ntsc" and frequencies to "us-cable"). From what I've read, TVtime (and xawTV) doesn't natively deal with ALSA, so (I think) it just gets the audio from /dev/dspX. I think there's some ALSA setting that might be different between your computer and mine, that allows TVtime to work for you.

Also, I'm still getting the chipmunk-voices in MythTV in both live TV and recordings (and also freezes/pauses in live TV), even though I changed the audio rate settings on the backend from "unlimited" to "32000". Anybody have any suggestions about that?

Thanks again, stadt, for at least helping me get mplayer to work!

---

### Post by stadt on 2007-05-06
> **mrchaotica said:**
>  From what I've read, TVtime (and xawTV) doesn't natively deal with ALSA, so (I think) it just gets the audio from /dev/dspX. I think there's some ALSA setting that might be different between your computer and mine, that allows TVtime to work for you.


As my TV-Card routes the sound through the soundcard (it uses a loop-cable to the sound-card-input) I had to set the soundmixer correctly. Sound worked for me after I leveled 'analog-mix' up. Before TVTime was muted here  too.

---

### Post by mrchaotica on 2007-05-06
> **stadt said:**
> As my TV-Card routes the sound through the soundcard (it uses a loop-cable to the sound-card-input) I had to set the soundmixer correctly. Sound worked for me after I leveled 'analog-mix' up. Before TVTime was muted here  too.
Ah, that'd be why -- my tuner doesn't have such a cable, and is instead *only* driven by ALSA (apparently).

I guess I ought to start a new thread about the remaining MythTV problems (unless, of course, I find the answer as I continue to search).

---

