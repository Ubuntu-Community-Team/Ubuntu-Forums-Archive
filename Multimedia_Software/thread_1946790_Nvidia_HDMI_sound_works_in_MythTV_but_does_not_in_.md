---
title: "Nvidia HDMI sound works in MythTV but does not in other applications"
date: 2012-03-25
forum: Multimedia Software
---

### Post by manwithamission on 2012-03-25
Hi folks,

I have the following problem and hope that someone can help me here.

I have the following Nvidia graphic card with builtin audio controller:

```

$ lspci | grep -i "nvidia"
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

```I connected my mythbuntu-box (based on Ubuntu 11.10 with XFCE)  to an LG LCD TV via HDMI and tried to get sound working, too. Using MythTV, there is no problem, I just selected "ALSA:hdmi:CARD=NVidia,DEV=1" as audio output device and everything is fine (TV sound, Music sound, DVD sound etc.).

The problem is, that when I want to have sound in other applications, such as watching a youtube video with firefox, there is no sound to hear. How can I configure the sound card in mythbuntu just the way I can configure it in MythTV?

What I already tried / some more information which might be useful to you:
- onboard intel sound card is currently disabled in Bios
- alsamixer only shows 4 different S/PDIF channels I cannot configure anything there
- in xfce4-mixer, selected sound card is "HDA Nvidia (ALSA mixer)" but I can only activate the 4 switches "IEC958",  "IEC958 1", "IEC958 2" and ""IEC958 3"; no other options there
- At "Additional Drivers", I tried both, "version current" and "post-release updates"

Here is the output of aplay:
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
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

$ aplay -L
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
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions

```Via speaker-test, I found a functioning device (hearable noise on left and right speaker):

```

$ speaker-test -c 2 -r 44100 -D hdmi:0,1

speaker-test 1.0.24.2

Playback device is hdmi:0,1
Stream parameters are 44100Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 44100Hz (requested 44100Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
...

```

But how can I configure the sound in mythbuntu in general to use this device?

Any help is highly appreciated!

Best Regards.

---

### Post by manwithamission on 2012-04-04
I still need help with this point.

---

### Post by BicyclerBoy on 2012-04-04
The std desktop programs use pulse audio default device.

Run pavucontrol & set the default output device on the configuration tab.

It should be a simple as that because your 'working' audio sub-device is the 1st or 2nd sub-device (so old pulse can see it).
11.10 pulse audio probably does not have this above limitation anyway..

Did you get audio on sub-devices: ?
speaker-test -c 2 -r 48000 -D hw:0,9
speaker-test -c 2 -r 48000 -D hw:0,8

---

### Post by manwithamission on 2012-04-06
Thanks for your reply!

Running pavucontrol results in the following error (see attachment).

Moreover, I get audio only on the following subdevices:
$ speaker-test -c 2 -r 48000 -D hw:0,7
$ speaker-test -c 2 -r 48000 -D plughw:0,7
$ speaker-test -c 2 -r 48000 -D hdmi:0,1

Any other idea how I can set the default device to one of the above or how to get pavucontrol run again (the command start-pulseaudio-x11 does not exist on my box)?

**Edit:** Installed package "pulseaudio" and got pavucontrol up and working again. But still no sound on firefox/youtube. Attached are some images of pavucontrol which all look nice to me and I cant figure out the problem. Any ideas?

Best Regards!

---

### Post by BicyclerBoy on 2012-04-06
You can edit /etc/pulse/default.pa & make pulse enumerate the correct alsa device..

---

### Post by manwithamission on 2012-04-07
That did the trick!  I listed all available sinks with "pacmd list-sinks" to get the index of the working subdevice, then I added "set-default-sink " in the default.pa file.  Many thanks for this tip!  Best Regards.

---

### Post by BicyclerBoy on 2012-04-07
Glad your solution worked..
I meant to post this in previous post but got side tracked ..
#/etc/pulse/default.pa
load-module module-alsa-sink device=hw:1,7

I'm not sure is the newer versions of pulse audio have this under enumeration problem..
[http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html#_broken_multi_channel_audio](http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html#_broken_multi_channel_audio)
[http://www.mail-archive.com/pulseaudio-discuss@mail.0pointer.de/msg07433.html](http://www.mail-archive.com/pulseaudio-discuss@mail.0pointer.de/msg07433.html)

---

