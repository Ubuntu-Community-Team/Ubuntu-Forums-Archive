---
title: "Pulseaudio crashes randomly"
date: 2013-06-01
forum: Multimedia Software
---

### Post by artbio on 2013-06-01
Pulseaudio crashes randomly while playing mp3 or any other audio files. Please see the attached pulseaudio output log.

[ATTACH]243399[/ATTACH]

What the problem might be? Should I report this as a bug on launchpad?

BTW I am using AC3 real time encoding configured from this guide -> [https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio) If it makes any difference!

Also to get audio working again I have to run:

pulseadio -D

then running

killall indicator-sound-service

brings back the audio icon on the top right corner of the desktop. But the keyboard keys to mute increase or decrease sound volume don't work any more. How can I make them work again? Without logging out?

I appreciate any help.

---

### Post by artbio on 2013-06-26
I  think I found a way to at least minimize this issue. From the  pulseaudio logs I found that for the AC3 plugin it isn't using the  default fragment settings from /etc/pulse/daemon.conf which are:
 default-fragments = 8
default-fragment-size-msec = 10
 Instead it adjusts to the nearest  latency with a default fragment size of 32 ms. So 8*10=80 ms. 32*3=96 ms  is the nearest latency. It is using a default fragment size of 32 ms no  matter what size I set in daemon.conf. This is what I am talking about:
 I: [pulseaudio] alsa-sink.c: Using 3.0 fragments of size 18432 bytes (32.00ms), buffer size is 55296 bytes (96.00ms)
I: [pulseaudio] alsa-sink.c: Disabling rewind for device a52:0
 I tried to lower the number of fragments and found that the frequency  of the audio drops increases. It might be too frequent actually. So  increasing the number of fragments should minimize the problem, right? I  can increase the number of fragments to the maximum hw buffer size  reported:
 D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 320 ms
D: [pulseaudio] alsa-util.c: Set buffer size first (to 3840 samples), period size second (to 480 samples).
 So if I set 10 or more fragments it will use 10 fragments. However  when I set a too large buffer size (at leat 8 fragments) applications  that play through the alsa plugin for pulseaudio will cause noise. So  now I am using 5 fragments with good results so far. Here is what I have  written inside daemon.conf:
 default-fragments = 5 # 8
default-fragment-size-msec = 32 # 10
 This yields a buffer size of 160 ms. An increase of 64 ms from the original 96 ms.

Since using these settings pulseaudio hasn't crashed! Yet!

---

