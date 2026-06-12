---
title: "Video doesn't play, sound is fine"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by jusmurph on 2007-10-29
Not sure really where to start, but the thing that has me stumped is Mplayer and VLC won't play the video, the sound works fine, i even get the thumbnails working fine.

M Player crashes and i have to restart the Xserver? (Ctrl + Alt + Backspace)
VLC just plays it like its an MP3.

I'm on Gutsy though it when i first installed Gutsy it was fine.

Any help would be appreciated.

---

### Post by matthewboh on 2007-10-30
I'm having the same problem with MPlayer especially with wmv, avi files.  Sound but no video.  I've uninstalled and reinstalled several times - it used to work - now with Gutsy.  Here's what happens when I try to run a wmv file through the terminal command

```
mlb@mlb-laptop:~/Desktop$ gmplayer clinton.wmv
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1400MHz (Family: 6, Model: 9, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/mlb/Desktop/clinton.wmv.
ASF file format detected.
VIDEO:  [WMV1]  240x176  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Trying to force video codec driver family ffmpeg...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv1] vfm: ffmpeg (FFmpeg M$ WMV1/WMV7)
==========================================================================
==========================================================================
Forced audio codec: mad
Trying to force audio codec driver family mp3lib...
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 11025 Hz, 1 ch, s16le, 10.2 kbit/5.76% (ratio: 1271->22050)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 240 x 176 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 240x176 => 240x176 Planar YV12 
A:   6.9 V:   7.0 A-V: -0.004 ct: -0.088  58/ 58  2%  1%  1.2% 0 0              
Exiting... (Quit)

```

Any ideas?  I hate keeping my Windows box around just so I can watch videos

---

### Post by jusmurph on 2007-10-31
I changed my theme back to Human and it 'fixed it'.

---

### Post by bananaman on 2007-10-31
I had the same issue, could be caused by a lot of things... i found it was fixed by disabling desktop effects (compiz)... im using an Nvidia card and havent found a solution... though, as you said, it was working just fine for the first week... both video and compiz

---

### Post by matthewboh on 2007-10-31
I wonder if it's possible if someone who CAN see and run videos could try and run it from the terminal and post the output here - that might help me

---

### Post by ohzopants on 2007-10-31
Same problem here.

2 days ago I removed all gstreamer packages as well as all the video players (VLC, xine, kaffeine, totem), restarted X and reinstalled the basics and it worked.  Then it stopped working again.

This is a really weird issue.

---

### Post by Dave in Tempe on 2007-11-01
Add me to the list with this problem; no video, just sound.  Streaming video is the only video that I can get to play right now.

---

### Post by reado on 2007-11-02
I'm in the same boat.

I'm still new to Ubuntu but I'm having the same problems as the rest of you...

To my knowledge, I've installed all the necessary codecs and software... I don't know why video isn't working and only audio plays.  I'm just getting a black screen the size of the video

Don't know if it matters, but I'm running with an ATI Radeon 9800.  I'm using the default drivers (Mesa) because after breaking my computer so many times trying to get Compiz running with the new ATI driver, I just gave up.

Sigh, I'd love to appreciate Ubuntu but this kind of stuff is making me question it  :confused:

Hopefully someone will get a proper fix for this stuff

---

### Post by Dave in Tempe on 2007-11-03
Bump. When I disable desktop effects, I get my picture back.  So I think the problem is in compiz somewhere, though I can't say where "somewhere" is.

---

### Post by ashughes on 2007-11-04
I am having the same issue.  Disabling Compiz Fusion does not rectify the issue.  My only work around right now is to load my VirtualBox WinXP VM and copy the files over using shared folders then play it in there.

If anyone wants me to write a quick guide on this, let me know.

---

### Post by matthewboh on 2007-11-04
I'm not running Compiz Fusion - I have a Toshiba Tecra M1 with the Trident XP4m32 graphics controller with 32MB DDR video memory.  Could that be the trouble?

It was the problem - long ago when I first installed Ubuntu, I had to make changes to the video drivers.  I backed up /etc/X11/xorg.conf and ran

sudo dpkg-reconfigure -phigh xserver-xorg

and now mplayer works.  Still trying to check streaming capability with mplayer streamer for mozilla.

---

### Post by Dave in Tempe on 2007-11-04
This guide got VLC and Xine working for me while running Compiz Fusion at the same time:  [http://wiki.compiz-fusion.org/VideoPlayback?highlight=%28playback%29%7C%28video%29](http://wiki.compiz-fusion.org/VideoPlayback?highlight=%28playback%29%7C%28video%29)

It did not work for mplayer or totem, which is weird because I use the xine back end version of totem.

---

### Post by mra122 on 2007-11-04
yeap...
same here :(
I get sound but not video...and also for some unobvious reason the font size in the window title is too small and bearly readable, and disabling compiz solved both problems, the video and the fonts...
But I really would like to continue using Compiz...
I hope they get it fixed soon...

---

### Post by mpgarate on 2007-11-04
my problem is similar and possibly related. sound and thumbnails are fine, but the video is displayed in weird pink and lime green tones (see attachment). It does this for any video, and even the vizualization plugin for rhyhthmbox. Happens with or without compiz-fusion.

[http://mikesubuntu.googlepages.com/Screenshotweirdvideo.jpg](http://mikesubuntu.googlepages.com/Screenshotweirdvideo.jpg)

---

### Post by bananaman on 2007-11-05
> **mpgarate said:**
> my problem is similar and possibly related. sound and thumbnails are fine, but the video is displayed in weird pink and lime green tones (see attachment). It does this for any video, and even the vizualization plugin for rhyhthmbox. Happens with or without compiz-fusion.

[http://mikesubuntu.googlepages.com/Screenshotweirdvideo.jpg](http://mikesubuntu.googlepages.com/Screenshotweirdvideo.jpg)

I got that "fixed" by disabling compiz fusion, then disabling the restricted nvidia driver, then restarting, then enabling the restricted nvidia driver then restarting again...

I got video working now, but i cant enable compiz or itll go back to that...

---

### Post by ubuntu-freak on 2007-11-12
If you select the X11 driver in MPlayer's video preferences you can watch vids while running Compiz Fusion. That's what I did in Debian. As for streaming wmv's and mp4's etc, I have to disable Compiz completely or I just hear the audio. Are some of you able to watch streaming wmv's with the MPlayer plugin while Compiz is running? I thought it was a universal problem. I can only watch flash vids and some random ones with CF running. I figured the people behind MPlayer needed to make it more CF compatible. Spit your thoughts at me.

---

### Post by bananaman on 2007-11-12
A few days ago there were updates... both nvidia and compiz... now my video is working fine with compiz... though the progress bar doesnt move *sometimes* in totem...

Go figure... i did nothing... but apparently still not working for a lot of people huh? Frustrating not to understand why it suddenly works now... but oh well...

---

### Post by ubuntu-freak on 2007-11-14
I've posted a fix for the Compiz/MPlayer plugin problem in the Debian User Forums Howtos section (I run Debian Sid)  [http://forums.debian.net/viewtopic.php?t=21315](http://forums.debian.net/viewtopic.php?t=21315)

It's working fantastic for me. It doesn't just enable you to see and not just hear, it improves streaming in general. I hope it helps you all out. P.S. Don't forget to add zoom=1 to the mplayer.conf in your home or /etc/mplayer/mplayer.conf directory if you are having problems resizing videos with the x11 driver. Also, with DVD playback or fullscreen playback you will need to use the xv driver and disable Compiz. Unless you're using the patched MPlayer of course. I'm not and it's unofficial anyway. Okay I'm done. Hope I've helped.

---

