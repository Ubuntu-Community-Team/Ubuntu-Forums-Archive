---
title: "Surround troubles"
date: 2017-05-03
forum: Multimedia Software
---

### Post by Roosje on 2017-05-03
I have searched everywhere, tried anything, ruined my system multiple times so a reinstall was needed, but nothing seems to fix my problem.

That first line was so i get all the obvious questions out of the way.

System Gigabyte Brix 6500U sound by Realktek ALC255, Audio by HDMI.
Ubuntu shows in config options for sound Digital Stereo, Digital 5.1, Digital 7.1.
But only left and right front speakers function. Alsa Mixer shows in any of these settings just one master slide.
Setting the number of speakers with default to 6 or 8 does nothing (in the config file /etc/pulse/daemon.conf) Trying to install the Realtek HD Audio driver threw a couple of errors and screwed my sound up to a Dummy device, and that's it. A total reinstall was needed to get sound back to where is started out from (16.04 and 16.10 give the same results)
How do i get the system to see the rest of the speakers?

I have uploaded my system info to [http://www.alsa-project.org/db/?f=8b018ddd2e71131e270a92b92fc0e571e46f347e]("http://www.alsa-project.org/db/?f=8b018ddd2e71131e270a92b92fc0e571e46f347e")

[Edit to Add extra info]
Strange thing is pavucontrol shows the sliders for all speakers when i disengage 'lock all channels together'

aplay -L shows:

```

~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
sysdefault:CARD=PCH
    HDA Intel PCH, ALC255 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    Front speakers
surround21:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
hdmi:CARD=PCH,DEV=1
    HDA Intel PCH, HDMI 1
    HDMI Audio Output
hdmi:CARD=PCH,DEV=2
    HDA Intel PCH, HDMI 2
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dmix:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample mixing device
dmix:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Hardware device with all software conversions

```

The sound test in Alsa shows this:
```
$ speaker-test -Dplug:surround71 -c8 -l1 -twav

speaker-test 1.1.3

Playback device is plug:surround71
Stream parameters are 48000Hz, S16_LE, 8 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
 2 - Unused
 3 - Unused
 4 - Unused
 5 - Unused
 6 - Unused
 7 - Unused
Time per period = 11,094628
```

This rhymes with the GUI sound test, only FL and FR give a sound :-(


Please help me, as i can not seem to fix this, and playing video sucks without center speaker for speech and such.
I can watch video but only with Stereo settings, otherwise voices disappear.

---

### Post by linuxyogi on 2017-05-03
> Alsa Mixer shows in any of these settings just one master slide.


With  alsamixer open press F6 and select your sound card. Then change the number of channels

Thats all I have done.

---

### Post by Roosje on 2017-05-03
> **linuxyogi said:**
> With  alsamixer open press F6 and select your sound card. Then change the number of channels

Thats all I have done.

[IMG]https://goo.gl/photos/a7THd7ZJpwYLPR8S8[/IMG]

I have done that, but how do i change the number of channels?

---

### Post by linuxyogi on 2017-05-03
Use the right arrow key to see if there are more options after SPDIF2. If not I am out of ideas.

---

### Post by Roosje on 2017-05-03
Nope, nothing more then loopback and capture

---

### Post by Roosje on 2017-05-04
I added this to the main msg body:
It is the result of speaker-test

```
$ speaker-test -Dplug:surround71 -c8 -l1 -twav

speaker-test 1.1.3

Playback device is plug:surround71
Stream parameters are 48000Hz, S16_LE, 8 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
0 - Front Left
1 - Front Right
2 - Unused
3 - Unused
4 - Unused
5 - Unused
6 - Unused
7 - Unused
Time per period = 11,094628
```

And the result from aplay -L

```

~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
sysdefault:CARD=PCH
    HDA Intel PCH, ALC255 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    Front speakers
surround21:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
hdmi:CARD=PCH,DEV=1
    HDA Intel PCH, HDMI 1
    HDMI Audio Output
hdmi:CARD=PCH,DEV=2
    HDA Intel PCH, HDMI 2
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dmix:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample mixing device
dmix:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC255 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Hardware device with all software conversions

```

Any clue as to how i can get ALSA to use all speakers (maybe Pulseaudio then also accepts it)?

---

### Post by slickymaster on 2017-05-04
*Thread moved to **Multimedia Software**.*

---

### Post by Roosje on 2017-05-06
What i have found out so far:

Bitstreaming of HD audio formats to an amplifier does not work on any Apollo Lake or Kaby Lake NUCs (problem exist on ASrock/MSI and other products with similar components as well) when connecting via the HDMI 2.0 port. There&#8217;s a long-running bug report here.
Add the Gigabyte Brix with i7 proc. to that list :-(

[https://bugs.freedesktop.org/show_bug.cgi?id=98797]("https://bugs.freedesktop.org/show_bug.cgi?id=98797")

---

