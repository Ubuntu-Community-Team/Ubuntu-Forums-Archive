---
title: "Mplayer Video Delayed, Video Game Controls Feel Stuck"
date: 2011-01-22
forum: Multimedia Software
---

### Post by cessusbangy on 2011-01-22
I'm streaming an EasyCAP DC60 video on Ubuntu 11.04 using mplayer, with the following command:

> [I]mplayer -tv driver=v4l2:device=/dev/easycap1:input=1:width=640:height=480:outfmt=yuy2:alsa:adevice=copy:buffersize=1024:fps=25:amode=2:audiorate=8000:forceaudio:immediatemode=0:norm=PAL -vfm skiploopfilter=all tv://
[/I] 
The video feels delayed, so when I move the analog stick, the video feels like it processes the command later, so I end up having little or no control over the movement, as it is not constant synced.
Any suggestions as to how I might change the command? This is the default log that happens all the time;

[B]MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: EasyCAP DC60
 Capabilites:  video capture  audio  read/write  streaming
 supported norms: 0 = PAL_BGHIN; 1 = NTSC_N_443; 2 = PAL_Nc; 3 = NTSC_N; 4 = SECAM; 5 = NTSC_M; 6 = NTSC_M_JP; 7 = PAL_60; 8 = NTSC_443; 9 = PAL_M; 10 = PAL_BGHIN_SLOW; 11 = NTSC_N_443_SLOW; 12 = PAL_Nc_SLOW; 13 = NTSC_N_SLOW; 14 = SECAM_SLOW; 15 = NTSC_M_SLOW; 16 = NTSC_M_JP_SLOW; 17 = PAL_60_SLOW; 18 = NTSC_443_SLOW; 19 = PAL_M_SLOW;
 inputs: 0 = CVBS0; 1 = CVBS1; 2 = CVBS2; 3 = CVBS3; 4 = CVBS4; 5 = S-VIDEO;
 Current input: 0
 Current format: YUYV
tv.c: norm_from_string(PAL): Bogus norm parameter, setting default.
Selected input hasn't got a tuner!
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Movie-Aspect is undefined - no prescaling applied.
VO: [vdpau] 320x240 => 320x240 Packed YUY2 
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 8000 Hz, 2 ch, s16le, 256.0 kbit/100.00% (ratio: 32000->32000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 8000Hz 2ch s16le (2 bytes per sample)
Starting playback...
v4l2: 41 frames successfully processed, 3 frames dropped.87.9% 6 0 

Exiting... (Quit)
ben@ubuntu:~$ 
[/B]

---

### Post by rmt1947 on 2011-01-22
Hi,

Looking at your mplayer command line I guess you are using easycapdc60 driver version 0.8.5.  This and earlier versions of the driver depend on OSS audio support, which is missing from Ubuntu 10.10 and later (or so I thought).  So I'm surprised that you are getting any sound at all:  

[http://ubuntuforums.org/showthread.php?p=10374223#post10374223](http://ubuntuforums.org/showthread.php?p=10374223#post10374223)

Maybe PulseAudio has been improved in Ubuntu 11.04 so that it now genuinely provides functional OSS emulation after all (in which case I'll have to retract some of the unkind things I said about Ubuntu 10.10 in the discussion at

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300)

but let's not be too hasty about that.)

I don't have Ubuntu 11.04 running on any machines here so all I can do is to mention some things that might be relevant.  I have not tested the mplayer commands suggested below - your mileage may vary.

(1) If you don't need audio, don't ask for it in the command line.  Use something like

```
mplayer -tv driver=v4l2:device=/dev/easycap1:input=1:width=640:height=480:outfmt=yuy2:buffersize=1024:fps=25:norm=PAL:noaudio -vfm skiploopfilter=all tv://

```

instead.  (If you ask mplayer for audio and then don't provide a valid audio stream from the driver I find that mplayer often gives poor _video_ performance as well as poor/no audio output.)

(2) If you do need audio, try connecting the audio cables directly to the sound-card input jack, bypassing the EasyCAP entirely.

(3) If this does not give well-synchronized audio and you wish to stay with Ubuntu version 11.04, you can try using easycapdc60 driver version 0.9, which is intended to cope with a situation where OSS is disabled.  You would then need to change your command line to something like

```
mplayer -tv driver=v4l2:device=/dev/video1:input=1:width=640:height=480:outfmt=yuy2:alsa:adevice=plughw.1,0:buffersize=1024:fps=25:amode=2:audiorate=32000:forceaudio:immediatemode=0:norm=PAL -vfm skiploopfilter=all tv://
```

Notice here that /dev/easycap1 becomes /dev/video1 and the audiorate is 32000 (because the driver automatically upsamples your 8000 Hz audio to 32000 Hz).  The string "video1" might be "video0" or "video2" and the string "plughw.1,0" might be "plughw.2,0" or whatever, depending on how many webcams and audio devices are present on your computer.  If the driver is installed correctly, you can find out what the digit in the "plughw" string should be by plugging in the EasyCAP, running the command

```
ls -l /proc/asound
```

and looking to see the number of the card which the link "EasyALSA" points to.

(4) You could retain easycapdc60 driver version 0.8.5 and downgrade your Ubuntu to 10.04 LTS Lucid.  This will give the best results for the EasyCAP, as regards both video and audio, but I expect this is not what you will want to do so I'll say no more about this option.

Since the mplayer commands above are untested it's quite possible that they won't work first time and will require tweaking.

Mike

---

### Post by cessusbangy on 2011-01-23
I am using 0.0.9. I just happen to be using the model with only a 8000 Khz sound frequency. 
Thank you so much for this command buddy. It works like a charm :)

*EDIT* The controller still feels laggy, but... I suppose I can survive without sound, just using subtitles. So, once again... thankyou :)

*EDIT* Also... how would one separately play sound directly from a sound card? So that, it wouldn't affect video performance.. just a separate terminal window?

---

### Post by rmt1947 on 2011-01-24
> Also... how would one separately play sound directly from a sound card? So that, it wouldn't affect video performance.. just a separate terminal window?


I'm not sure what hardware you are using as an audio-video source.  Quite often there are three output sockets, colour-coded red, white and yellow.  Normally you connect these with three separate cables to the red, white and yellow input sockets on the EasyCAP.  The alternative mentioned in my previous post is to disconnect the red and white cables from the EasyCAP and connect them to the line-input jack on the computer, usually colour-coded blue:

[http://en.wikipedia.org/wiki/Line_level](http://en.wikipedia.org/wiki/Line_level)

(Note the warning about ground loops mentioned in the above article.)  An adapter is needed for this alternative setup, something like:

[http://www.soundbasemegastore.com/3m-Twin-RCA-Phono-To-35mm-Stereo-Jack-p12465/](http://www.soundbasemegastore.com/3m-Twin-RCA-Phono-To-35mm-Stereo-Jack-p12465/)

[http://www.dabs.com/products/cablestogo-2m-3-5mm-plug-rca-jack-y-cable-67RD.html](http://www.dabs.com/products/cablestogo-2m-3-5mm-plug-rca-jack-y-cable-67RD.html)

(These examples may not be right for your computer - you will need to check what kind of line-input socket you have.)

The yellow video cable remains attached to the EasyCAP as before, and you can use mplayer in the usual way to get silent video.  To route the audio through the computer's sound card (the EasyCAP's sound chip is not in use now) you open a new terminal window and run the command

alsamixer

(as suggested by cchhrriiss121212 in post #2 of your other thread).  The tab and arrow keys on the keyboard allow you to set the volume of the line-input channel.  And that's it.

This morning I've tried out this alternative (for the very first time, actually), and found that the sound quality is good, but audio-video synchronization is poor.  But this may be due to peculiarities in the hardware and/or software configuration of my computer, and you might have better luck on your machine.

There is no guarantee that the alternative setup will give less overall cpu load, smoother video or any other benefit, but it might be worth a try.  The underlying issue is that modern Linux audio is just too resource-greedy.

Mike

---

### Post by cessusbangy on 2011-01-24
Thank you all for the input!
I have now made a video for youtube, a comprehensive tutorial on how to use EasyCAP DC60 for Linux :D
[http://www.youtube.com/watch?v=Gl_DTRh2h2Q](http://www.youtube.com/watch?v=Gl_DTRh2h2Q)

---

