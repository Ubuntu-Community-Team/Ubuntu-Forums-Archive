---
title: "No HDMI Audio with nVidia GeForce 210"
date: 2012-10-07
forum: Multimedia Software
---

### Post by alanrbryant on 2012-10-07
I have seen several posts about this on various forums & blogs, but none of the solutions help in my case.

I have two old Dell Dimension PC's that I am using as HTPC machines at two TV's (Different brands & sizes). I am using an identical PNY GeForce 210 video cards connecting to the TV's via HDMI.

I have used the following distributions (all based on Ubuntu), Mythbuntu 12.04 & 11.04, XBMCbuntu 11 (Ubuntu 11.10), Xubuntu 12.04, & OpenELEC 1.99.1 (somehow based on Ubuntu).

All but Mythbuntu 11.04, which I can only assume all other versions of Ubuntu 11.04, do not have audio through HDMI, except with MythTV.

MythTV works fine, but XBMC, system sounds, Flash, & anything else do not. On 11.04, everything seems to work fine, XBMC included.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output
```

```
aplay -D plughw:0,3 /storage/Front_Center.wav
aplay: main:696: audio open error: Device or resource busy
```

The above command but with 0,7-9 results in the following, but no sound is played:

```
Playing WAVE '/storage/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
```

```
speaker-test -c 2 -Dplughw:0,3
speaker-test 1.0.26

Playback device is plughw:0,3
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy
```

The same command but with 0,7-9 results in the following but no sound is played:
```
speaker-test 1.0.26

Playback device is plughw:0,7
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5.638334
 0 - Front Left
```

I have tried all possible options of plughw: x,y & hw: x,y in XBMC audio settings and rebooting between every change. It all seems kind of useless considering the aplay & speaker-test commands were not working.

I have run alsamixer and verified every channel/device was not muted.

I have not created an asound.conf as I did not think that it would help due to the aplay & speaker-test failures, but please correct me if I am wrong. I also have not modified the modules settings either.

I am stumped. Any help, guidance, pointers, etc. will be greatly appreciated!

---

### Post by alanrbryant on 2012-10-07
Quick update. I tried a Frodo (development version) of OpenELEC as suggested by a moderator on their forum and it works.

They are using Audio Engine for the sound and it worked right away without any configuration needed.

---

### Post by BicyclerBoy on 2012-10-07
Can you post the hot plug event..
dmesg | grep HDA

ls -al /proc/asound/card0/eld*

find a "not-empty" eld#n.m   file & post that...

It is best to allow speaker-test to cleanly stop..ctrl-c locks the audio device. Alternative is close/open terminal each cmd.

speaker-test -l 2 -c 2 -r 44100 -D hw:0,9
try 9, 8, 7..not plughw please..

---

