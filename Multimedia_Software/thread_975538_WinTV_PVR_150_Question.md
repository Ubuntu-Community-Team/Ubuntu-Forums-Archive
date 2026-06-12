---
title: "WinTV PVR 150 Question"
date: 2008-11-08
forum: Multimedia Software
---

### Post by LAKOSWOLF on 2008-11-08
Greetings all!

I've upgraded to Ubuntu 8.10 almost flawlessly, with the exception of my Hauppauge WinTV PVR-150MCE card. I have tried almost every link I can think of on Ubuntu Forums as well as google and thus have been able to figure out a few things.

my card IS Identified, I ran  lspci with the following result,

```
 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

```
When running:  ```
mplayer /dev/video0
``` I get a window with static but no sound.

Mplayer output:

```
lakoswolf@GRAYWOLF:~$ mplayer /dev/video0 
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 35, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  8000.0 kbps (1000.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
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
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
GNOME screensaver enabled.000 ct: -0.324 401/401  9%  1%  7.2% 0 0 

```

when attempting to tune the FM radio in ivtv: ```
lakoswolf@GRAYWOLF:~$ ivtv-radio -f 101.3
set to freq 101.30
Running: aplay -f dat < /dev/video24
Playing raw data 'stdin' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo
```

^This is an improvement over the output I received while running Hardy, however I should note that I was never able to get video or audio running with this card under Hardy. It seems to be tuning to the station, but I don't hear anything. I can't figure out why it says that its using dev/video24 if I just want to hear audio?

I have been unable to try this card via Windows XP due to the fact I don't have an MCE version.

I would like to be able to setup the card to play FM Radio and TV. Perhaps I am missing something? Any suggustions would be greatly appreciated.

Thank You,

-Lakoswolf

---

### Post by MikeB23930 on 2009-01-25
Try installing libv4l-0.  Worked for me in Kubuntu 8.10.

Mike

---

### Post by wolfen69 on 2009-01-25
If the following does not work, it means you have corrupted system files somewhere. this has worked for me on 3 different computers with 3 different versions of ubuntu. And has been verified to work for other people.

I have a Hauppauge PVR150 card running on my box, and I get  tv by: 

```
sudo apt-get install ivtv-utils 
```

open VLC player

Media -> Open Capture Device -> PVR (from pull down menu) -> OK

then you can do (in terminal)

```
ivtv-tune -c25
``` (25 is channel number)

which changes the channel.

```
ivtv-tune -h
```

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/) (see attachment)

remember to have java installed first. then you can right click: open with java.

to record tv:

```
cat /dev/video0 > /tmp/name_of_file.mpg
```

it will record whatever channel you are on. then ctrl-c to stop recording.

---

### Post by jv2112 on 2009-01-25
Anyway of tracking down what is corrupted ?

I get :

"ioctl VIDIOC_S_FREQUENCY failed"

---

### Post by ttolstead on 2009-01-25
I am experiencing the same issue, it worked fine in Gutsy using ivtv-tune to set the channel and vlc to view the output.  I have installed ivtv-utils and followed the same path to no avail.  I have purged and reinstalled ivtv-utils, and vlc.  I get the same thing with mplayer.

Athlon x2 5200*
Ubuntu 8.10
4gb ram
vlc works fine for other applications.

---

### Post by Macintosh SE on 2009-01-25
I have this exact card working perfectly under 8.04. Feel free to ask me specific questions, if you think I could help.

I usually watch TV via Totem and use ivtv-tune to tune channels.


Did tou try this to test your card?

```
cat /dev/video0 > test.mpg
```

Do Control-C to stop recording. If you can play the recording, the card is functioning properly.

---

### Post by ttolstead on 2009-01-26
I have tested the card using the /dev/video0 > test.mpg method, it appears to work but all I get is snow.  And, of course the thing works when I run Vista.

---

### Post by wolfen69 on 2009-01-26
> **jv2112 said:**
> Anyway of tracking down what is corrupted ?

I get :

"ioctl VIDIOC_S_FREQUENCY failed"

in vlc, try changing device  to /dev/video1

i have a feeling that upgrading ubuntu instead of doing a clean install has something to do with it. my method has never failed after a clean install.

---

### Post by Macintosh SE on 2009-01-27
> **ttolstead said:**
> I have tested the card using the /dev/video0 > test.mpg method, it appears to work but all I get is snow.  And, of course the thing works when I run Vista.

By snow, do you mean static, like that which your TV might display while tuned to an unused channel?

Could you post 2 things:

-What channel 3 looks like on your TV
-what your .ivtv-tune file looks like (hidden file in your home folder)

---

### Post by ttolstead on 2009-01-27
The .ivtv-tune file contains the following:

device /dev/video0
freqtable us-cable

The TV signal is coming from a satellite box and is on channel 33.  I have attached an image of what shows up on channel 33.  This was working under Kubuntu 8.04, the current install is a fresh Xubuntu 8.10 installed on top of Vista using wubi.

---

### Post by buddyd16 on 2009-01-27
If you have the satelite box connected to the card via a coax cable try setting the capture card to channel 3.

---

### Post by ttolstead on 2009-01-28
I have tried many different channels, including channel 3, to no effect.  I am beginning to think I may have to do a complete re-installation of Xubuntu.

---

### Post by ttolstead on 2009-02-08
I have now uninstalled Xubuntu 8.10.  I have made a clean install of Ubuntu 8.10, and have the same issue with both vlc and mplayer.  The output from mplayer when using the command: "mplayer /dev/video0" is:

tom@ubuntu:~$ mplayer /dev/video0
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ (Family: 15, Model: 67, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
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
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
GNOME screensaver enabled.220 ct: -0.220  56/ 56 22%  4% 20.6% 0 0 

Upon closing mplayer:

Exiting... (Quit)

Any ideas? I have no idea what a scale filter might be. (bump):(

---

### Post by saedelaere on 2009-02-17
> **ttolstead said:**
> I have now uninstalled Xubuntu 8.10.  I have made a clean install of Ubuntu 8.10, and have the same issue with both vlc and mplayer.  The output from mplayer when using the command: "mplayer /dev/video0" is:

tom@ubuntu:~$ mplayer /dev/video0
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ (Family: 15, Model: 67, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
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
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
GNOME screensaver enabled.220 ct: -0.220  56/ 56 22%  4% 20.6% 0 0 

Upon closing mplayer:

Exiting... (Quit)

Any ideas? I have no idea what a scale filter might be. (bump):(

Are you sure you are using the correct video device? Have you set the correct video input?

---

### Post by ttolstead on 2009-02-17
At this point, I have tried all three video devices in /dev.  I have also tried changing the input selections, apparently successfully, to no avail.  I have tried many different channels, and remain baffled.

---

### Post by kb7ypf on 2009-03-17
Hi

I read your WinTV PRV-150 response.  

I just got my PRV-150 work with VLC and the Desktop Java TV Remote (cool) and it all works great.  The question I have is I can't record.  I type the command you  provided (cat /dev/video0 > test.mpg) in a terminal and I get back the following response:  **Device or resource busy**

I goto the /dev directory and I see the .mpg file there.

Any suggestions of how I can work around the problem.

Thanks

---

### Post by ttolstead on 2009-03-17
If you are seeing a "device busy", I believe you may have vlc open when you are attempting to record.  To record, you should tune the channel with vlc so you know what you are about to record, then close vlc and use the terminal command to record.  At least that is how it worked for me, when it worked.

---

### Post by kb7ypf on 2009-03-18
ttolstead:

Thanks much for the post.  That was the problem.  I am able to record.  I really appreciate all you folks helping all of us out.  :popcorn:

Dick

---

