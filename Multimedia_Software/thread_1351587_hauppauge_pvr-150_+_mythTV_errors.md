---
title: "hauppauge pvr-150 + mythTV errors"
date: 2009-12-10
forum: Multimedia Software
---

### Post by haze. on 2009-12-10
Hi,

I have been trying with no luck to get MythTV to work on my computer.  I can get the system to find channels etc, but when I go to watch TV, I get a snowy screen (attached photo)

I am still fairly new with ubuntu, so ANY help would be great...

When I open MythTV and try to watch ANY channels I get the snowy screen.

This is the output I get when I run 'mplayer /dev/video0' if its any help.

haze@haze:~$ mplayer /dev/video0 
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ (Family: 15, Model: 67, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
MPEG-PS file format detected.
VIDEO:  MPEG2  480x576  (aspect 2)  25.000 fps  6000.0 kbps (750.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 480 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 480 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 480x576 => 768x576 Planar YV12 
GNOME screensaver enabled.007 ct: -0.439 316/316  4%  1% 13.6% 8 0 


I would really like to get this working, as I seem to loose out on the battle to watch whats on our home TV.  

Please, any help would be GREAT!

Thanks

---

### Post by noelvh on 2009-12-10
I have to say I had a very simmilar issue with my Win PRV 150 card. You did get farther than I did. I worked on this for a year and gave up. I hope some one can help you, as I think the 150 is the very best anlog pvr card. I ended up using XP with GB PVR, and it worked with out any issues at all. 

I do with I could have gotten ether Myth or linuxprv to work.

Noel

---

### Post by HappyFeet on 2009-12-10
During setup, did you select mpeg2 pvrx50? The default is v4l. Run setup again, (you don't need to reinstall) and double check. My pvr150 has always worked great.

One other thing. Are you trying to set up a tivo-like machine, or do you just want to watch tv? If you just want to watch tv and record on the fly, I have a simple tutorial for that, without the need for mythtv.

---

### Post by haze. on 2009-12-10
> **HappyFeet said:**
> During setup, did you select mpeg2 pvrx50? The default is v4l. Run setup again, (you don't need to reinstall) and double check. My pvr150 has always worked great.

One other thing. Are you trying to set up a tivo-like machine, or do you just want to watch tv? If you just want to watch tv and record on the fly, I have a simple tutorial for that, without the need for mythtv.

ideally I would like the option to PVR some shows etc which is why I am looking at mythtv.

Alternatively, I would be interested in your tutorial for watching TV on fly...  please do send!

---

### Post by HappyFeet on 2009-12-10
```
sudo apt-get install ivtv-utils vlc 
```

open VLC player

Media -> Open Capture Device -> PVR (from pull down menu) -> Play.

then you can do (in terminal)

```
ivtv-tune -c25
``` (25 is channel number)

which changes the channel.

```
ivtv-tune -h
```

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels, or to start tv) go to: [http://sourceforge.net/projects/tvremote/](http://sourceforge.net/projects/tvremote/)    Highly recommended. I attached a screenshot for you.

remember to have java installed first. then you can right click>properties> open with> java. After that, just click normally to launch.

---

### Post by HappyFeet on 2009-12-10
I forgot one thing. To record with vlc, go to View>Advanced Controls, and there will now be a record button on the bottom of vlc that will save to your home folder. Enjoy.

---

### Post by haze. on 2009-12-10
> **HappyFeet said:**
> ```
sudo apt-get install ivtv-utils vlc 
```

open VLC player

Media -> Open Capture Device -> PVR (from pull down menu) -> Play.

then you can do (in terminal)

```
ivtv-tune -c25
``` (25 is channel number)

which changes the channel.

```
ivtv-tune -h
```

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels, or to start tv) go to: [http://sourceforge.net/projects/tvremote/](http://sourceforge.net/projects/tvremote/)    Highly recommended. I attached a screenshot for you.

remember to have java installed first. then you can right click>properties> open with> java. After that, just click normally to launch.


ok, well I tried all of those things you suggested, and I am still getting a snowy picture.  I tried the above suggestion, GB-PVR in my Windows partition... worked great.  Ideally, I would like to run this in Ubuntu.

Any suggestions?  

Here are the option when I do the ivtv-tune -h

Channel/Frequency changer for V4L2 compatible video encoders

Usage: ivtv-tune [OPTIONS]...

  -h, --help              Print help and exit
  -V, --version           Print version and exit
  -c, --channel=CHANNEL   set new channel
  -d, --device=DEVICE     set video device node
  -f, --frequency=FREQ    set new frequency (MHz)
  -l, --list-channels     list all channels and their frequencies  
                            (default=off)
  -L, --list-freqtable    list all available frequency mappings  (default=off)
  -t, --freqtable=STRING  set frequency map to use
  -x, --xawtv=CHANNEL     set new channel using custom map from ~/.xawtv

When I LIST the channels, it shows hundreds of channels, but when I try to scroll through them, NOTHING.  Snow...

---

### Post by HappyFeet on 2009-12-10
What happens when you do
```
ivtv-tune -c25
```
try some other channel numbers also.

---

### Post by haze. on 2009-12-10
> **HappyFeet said:**
> What happens when you do
```
ivtv-tune -c25
```
try some other channel numbers also.

i get this:

haze@haze:~$ ivtv-tune -c25
/dev/video0: 229.250 MHz

and the image in VLC is SNOW!!  We have enough snow outside, dont need it on my screen...

i have been battling this for a few weeks on forums before i posted...  i dont get it.

after doing some more research, it appears its an ivtv issue, seeing as i cannot view simple tv through mplayer or vlc.  does anyone know how to fix my ivtv to work with the pvr 150?

---

### Post by HappyFeet on 2009-12-10
Did you do an upgrade of ubuntu?

---

