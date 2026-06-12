---
title: "Pinnacle 800i +mplayer +composite source audio"
date: 2009-06-24
forum: Multimedia Software
---

### Post by watchreader on 2009-06-24
OK, so I have a wii I would like to play.  I have a Pinnacle 800i PCTV card.  Yes, I've updated the firmware.  I'm not interested in watching TV on this card for the time being, I just want the composite input to work!

I've tried around various programs.  MythTV was too complicated for me to set up (and it took up the whole screen but didn't cover up the tool bar, and the arrow buttons stopped working after I pressed esc, etc).  

I've tried TVTime, but a) the video quality was terrible and b)there was no audio.  I know there's a way of getting around this TV time audio thing by using the instructions here: [http://ubuntuforums.org/showthread.php?t=1173653](http://ubuntuforums.org/showthread.php?t=1173653), but those suck and get terribly out of sync very quickly.  So TVTime's no good.

I've tried VLC player, which managed to read both my audio and video correctly, but with a 3 second delay and had very low quality (not good for games).  So that's out :(

But then, someone suggested I try mplayer.  I followed their instructions, and the visual is perfect!

But there's no audio :(

I'm using this command: 
mplayer tv:// -tv driver=v4l2:alsa:adevice=/dev/audio2:amode=1:device=/dev/video1:input=1:norm=NTSC-M -quiet

I know it's odd that it's video1 but audio2, but those are what worked in vlc so I assume those are still the right devices.  At any rate, I get the output: 

> 
v4l2: current audio mode is : STEREO
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Packed UYVY)
VDec: using Packed UYVY as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Packed UYVY 
Selected video codec: [rawuyvy] vfm: raw (RAW UYVY)
==========================================================================
Audio: no sound
Starting playback...
I know I'm really really close, but so far I haven't been able to get *any* sound out of mplayer- not even my microphone!  Any mplayer guru's out there have the answer? :O

---

### Post by watchreader on 2009-07-23
Is there no one with an answer?  I'm so close!  I can get vlc to play the audio, but it looses sync after a few seconds.  Is there anyone with an answer to this problem?

---

### Post by wiresquire on 2009-07-27
A couple of suggestions. I don't have a Pinnacle, but have been playing around a little with mplayer.

1. You do get sound out of mplayer when you just play a normal video clip like an mpg, right? That would help make sure that mplayer is working OK.

2. I don't think your adevice is correct. You are using alsa in the above command line. mplayer manual states:
adevice=<value>
Set an audio device. <value> should be /dev/xxx for OSS and a hardware ID for ALSA. You must replace any ’:’ by a ’.’ in the hardware ID for ALSA.

For my card, mine looks like:
mplayer tv:// -vf pp=lb -tv driver=v4l2:device=/dev/video1:alsa:**adevice=hw.1,0**:input=1:amode=1
and NOT /dev/audio2. You'd need to work out which ALSA ID yours is...

3. Try adding immediatemode=0, eg with my device to get composite, I use:
```

mplayer tv:// -vf pp=lb -tv driver=v4l2:device=/dev/video1:alsa:adevice=hw.1,0:input=1:amode=1:immediatemode=0

```
This forces the sound to be picked up by mplayer. By default mplayer thinks that you are going to hook up sound cables directly from the device to your speakers, and not go via mplayer.

4. Now, if the above immediatemode works it may work OK for your purposes. I was using composite to play a PS2 through. And the performance was not good. It was 'laggy' and slow when using a controller, like a delay between pressing a button, and it showing on the screen. The problem was with immediatemode, and I hadn't found a way around that via mplayer. But you may be able to have the device sound play anyways. What I did was :
a) Run your normal mplayer command WITHOUT immediatemode, eg in my case:
mplayer tv:// -vf pp=lb -tv driver=v4l2:device=/dev/video1:alsa:adevice=hw.1,0:input=1:amode=1
There will be no sound when you start this, just video output.
b) In a separate terminal, start the alsa sound:
arecord -D hw:1,0 -r 48000 -c 2 -f S16_LE | aplay -
Note again that this has the alsa device number (-D) that yours may be different.
This worked well for me and there was no performance lag. I suspect that the video and audio could get out of sync, but I didn't notice that in my short testing.

hth
ws

---

### Post by watchreader on 2009-07-27
Thank you so much for your reply!

I've tried a few things you listed there, but I still got no sound.  I eventually just broke down and went to radio shack and got $9 worth of components.  I plug my speakers into those, and play the video through the computer.  It works great, I just have to switch the speaker cord every time I want to change eh?

---

