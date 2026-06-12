---
title: "gt 240 hdmi audio - works in xbmc, not mythtv"
date: 2011-01-15
forum: Multimedia Software
---

### Post by pharcycle on 2011-01-15
Hi there, 

I just bought a gt 240 for my htpc and have been following the various guides to enable hdmi audio. My computer is hooked up to my av receiver then to the HDTV.

I've done a vanilla install of mythbuntu and out the box it detects the card but the system doesn't seem to use it. in the xbmc audio options i've got audio to work by using plughw:0,7 as the custom devices for audio out and passthrough. Works with most of my video files so far.

I've not had any joy yet getting mythtv or system sounds to output through hdmi yet so looking for a few pointers if anyone can help?

Many thanks.

```

speaker-test -c6 -tpink -Dplughw:0,3
speaker-test -c6 -tpink -Dplughw:0,7
speaker-test -c6 -tpink -Dplughw:0,8
speaker-test -c6 -tpink -Dplughw:0,9

```all play fine in 5.1 through my receiver,

```

david@HTPC:~$ speaker-test -c6 -tpink -Dplughw:0,7

speaker-test 1.0.23

Playback device is plughw:0,7
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 349504
Period size range from 32 to 174752
Using max buffer size 349504
Periods = 4
was set period_size = 174752
was set buffer_size = 349504
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE


```output of aplay -l and -L

```

david@HTPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
david@HTPC:~$ 

```/

```

david@HTPC:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions

```

---

### Post by BicyclerBoy on 2011-01-15
This has been discussed in great exacting detail by the developer many times in the forums.

[http://www.gossamer-threads.com/lists/mythtv/](http://www.gossamer-threads.com/lists/mythtv/)

& by the nvidia guru in the nv forums..
[http://www.nvnews.net/vbulletin/showthread.php?t=154755](http://www.nvnews.net/vbulletin/showthread.php?t=154755)

search for hdmi audio in the last few weeks.

You fail to mention any facts about your nvidia driver version, MythTV version setup or log files..

Your alsa version looks okay.

I think you have not configured your mythtv audio correctly..

---

### Post by pharcycle on 2011-01-15
Apologies,

I'm fairly inexperienced with linux so just thought someone may have been able to say "turn on this..." and save me the rest of my weekend!

mythbuntu so no pulse, just alsa 1.0.23
nvidia driver 260.19.06
mythbuntu 10.10 x64

good point about the logs will have a look to see what myth outputs

---

### Post by BicyclerBoy on 2011-01-15
You are not far from having it sorted..
Concentrate your Myth audio efforts on the mythtv forum linked..

Look for any audio threads by J Y Avenard.

His recent posts will walk you thru' to a working solution BUT you must read the entire post thread.

Sorry I see little sense in regurgitating from the real information sources.
I mostly just try to help people to find stuff themselves.

---

