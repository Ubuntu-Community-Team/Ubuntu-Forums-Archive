---
title: "Need help troubleshooting recording line-in (8.10)"
date: 2008-12-31
forum: Multimedia Software
---

### Post by jumpfroggy on 2008-12-31
Hi all!
I've installed Ubuntu 8.10 and have been playing around with it for a while.  I'm trying to get MythTV working and am having trouble with audio recording.  I've got the TV card working (record/view tv), and can play audio files, but cannot record anything.

I have an NForce3 motherboard with built-in AC97 audio.  I can play wav files with 'aplay -vv test.wav', and I hear it fine.  However, when I go run 'arecord -vv test.wav' it starts recording but only creates a 44 byte file with no audio.

This is the output from arecord:
Recording WAVE 'test.wav' : Unsigned 8 bit, Rate 8000 Hz, Mono
ALSA <-> PulseAudio PCM I/O Plugin
Its setup is:
  stream       : CAPTURE
  access       : RW_INTERLEAVED
  format       : U8
  subformat    : STD
  channels     : 1
  rate         : 8000
  exact rate   : 8000 (8000/1)
  msbits       : 8
  buffer_size  : 4000
  period_size  : 1000
  period_time  : 125000
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1000
  period_event : 0
  start_threshold  : 1
  stop_threshold   : 4000
  silence_threshold: 0
  silence_size : 0
  boundary     : 2097152000

This is the output from amixer:
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 45875 [70%] [on]
  Front Right: Playback 45875 [70%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 65536 [100%] [off]
  Front Right: Capture 65536 [100%] [off]

What else can I try?  I've been reading a lot of tutorials an troubleshooting, but unfortunately there's a huge amount of info, some outdated, and I haven't found anything that helps.  What troubleshooting steps can I take?  (Logfiles, drivers, mixer settings, etc).

Thanks!

---

### Post by jumpfroggy on 2009-01-04
I figured out what it was, and I'm posting here for other users.  My goal was to use the line-in of my sound card with mythtv, but all I got was a horrible hissing noise.

First, I tried a few mixers.  `alsamixer` only shows me the "capture" channel for input, on the "PulseAudio" card, had no effect on anything.  I also tried `pavucontrol`, but none of these settings had any effect as well (muting inputs, selecting "default" input channels, enabling different switches, etc).

I finally found [this article about recording with bttv.]("http://tldp.org/HOWTO/BTTV/recording.html")  I'm not using the sound input on my card (allegedly, some non-FM WinTV-GO cards don't have an internal audio capture), but it helped.

I had to run `cat /proc/asound/cards`, which showed me that #0 was the NVidia CK8S (onboard sound), and #1 was the Bt87x (wintv go tuner input, may not even exist).

Then I ran `amixer -c 0 controls` (the 0 is for card #0 from the first step) and saw 'Capture Source'.

`amixer -c 0 cget name='Capture Source'` showed that I had some inputs, including `; Item #4 'Line'`.  That's what I want, so now I do `amixer -c 0 cset name='Capture Source' 4`, which sets the capture source to the line-in.

Now it works, finally!!!!  But I still get scratchy audio in mythtv.  So now I see [this troubleshooting page]("http://www.mythtv.org/wiki/index.php/Sound_Troubleshooting#Distorted_audio_on_input") which says to change the sampling frequency for all the encoding profiles in mythtv.  I run `mythtv-setup` and go to Utilities/Setup > Setup > TV Settings > Recording Profiles > Software Encoders (v4l based).  I see a list of profiles, for each one I click on it, hit Next, Next, Next, then change the Sampling Rate to 48000, which is correct for my card (ECS NForce-3A).  The default for mythtv is 32000, which is strange to me.  After setting the sampling rate to 48k, sound is perfect!

I can't control the input sound volume with the 'Capture Volume' control, but thankfully it's at a good volume so I don't care.  Still strange.

Hopefully this helps someone else out.  Good luck!

---

