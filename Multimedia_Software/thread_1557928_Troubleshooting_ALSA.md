---
title: "Troubleshooting ALSA"
date: 2010-08-21
forum: Multimedia Software
---

### Post by EricJonsson on 2010-08-21
After much troubleshooting, I still can't figure out what's wrong -- I simply can't make ALSA play 5.1 audio, though OSS4 works. (but ALSA emulation also fails)

Without any custom alsa.conf's or .asoundrc's, this is what the ALSA tools report:

```
eric@gimli:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=NVidia
    HDA NVidia, ALC662 rev1 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
```Note the "surround51" device, this is the one I want to use.

```
eric@gimli:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```The soundchip also has digital and HDMI audio, but for now I'm trying to use analog out.

```
eric@gimli:~$ speaker-test -c 2 -t wav

speaker-test 1.0.22

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 16384
Period size range from 1024 to 1024
Using max buffer size 16384
Periods = 4
was set period_size = 1024
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 2.705572
```Outputting analog audio in stereo works nicely.

```
eric@gimli:~$ speaker-test -c 2 -t wav -D surround51

speaker-test 1.0.22

Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 1048576
Period size range from 32 to 524288
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 10.974781
```Stereo (two channels) even works when I specify the "surround51" device.

```
eric@gimli:~$ speaker-test -c 6 -t wav -D surround51

speaker-test 1.0.22

Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument
```When I up the ante to six channels however, the surround51-device fails and the error messages doesn't make any sense to me.

Any ALSA wizard out there? Where do I go from here to get fully working 5.1 surround sound?

---

### Post by EricJonsson on 2010-08-21
More info, I just built and installed a fresh ALSA (modules and library) from source:

```
eric@gimli:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Aug 21 2010 for kernel 2.6.32-24-generic (SMP).
eric@gimli:~$
```No change, I still can't play six channel audio...

---

### Post by EricJonsson on 2010-08-22
[Solved it!]("http://www.acc.umu.se/%7Eericj/?q=node/32")

Turns out /etc/modprobe.d/alsa-base.conf needed one additional line:

```
options snd-hda-intel model=3stack-6ch-dig
```(Don't ask me where "Intel" gets into this, the audio chip's a Realtek ALC662)

Nonetheless, after a reboot an additional control turned up on alsamixer, enabling me to switch to 6 channel sound. speaker-test (and the rest of my ALSA apps) now works like they should. Marking thread solved.

---

