---
title: "Flash and Pulseaudio problem"
date: 2010-02-28
forum: Multimedia Software
---

### Post by martinezlc99 on 2010-02-28
I am having a problem when using Flash.  Whenever I am listening to a Flash application (youtube primarily), I am unable to hear sound from any other applications (Rhythmbox, movie player, etc).  

The converse is also true, if I am using Rhythmbox, and then start youtube, the video plays...but with no sound.  

I have to manually kill the app and web browser (tried multiple...Firefox, Chrome, Swiftfox) to get sounds working correctly.  Sometimes, I am forced to reboot to get sounds working in the appropriate app.

I am my wits end with this problem, and have just putting up with it for several months now.  I am pretty new to linux, so any advice would be appreciated.  

Here is the output of aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 
```

---

### Post by VertexPusher on 2010-02-28
Let's run some tests to find out what's wrong. Open a terminal window and enter this command:
```
aplay -D default -t raw -c 2 -f S32_LE -r 48000 -d 1 -v /dev/zero
```
This will play back one second of silence and print the PCM structure of the default ALSA audio device. The output will show whether the default device is configured to use dmix, PulseAudio, or no stream mixer at all. Please post the output here.

Next, run Firefox and launch a YouTube video. While the video is playing (with sound), enter the following command into the terminal window:
```
lsof | grep dsp
```
The output will tell us whether Flash uses ALSA or OSS. Post the output here, too.

---

### Post by garvinrick4 on 2010-02-28
> **martinezlc99 said:**
> I am having a problem when using Flash.  Whenever I am listening to a Flash application (youtube primarily), I am unable to hear sound from any other applications (Rhythmbox, movie player, etc).  

The converse is also true, if I am using Rhythmbox, and then start youtube, the video plays...but with no sound.  

I have to manually kill the app and web browser (tried multiple...Firefox, Chrome, Swiftfox) to get sounds working correctly.  Sometimes, I am forced to reboot to get sounds working in the appropriate app.

I am my wits end with this problem, and have just putting up with it for several months now.  I am pretty new to linux, so any advice would be appreciated.  

Here is the output of aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 
```
Do what VertxPusher says and he will fix it for you. Stay away from other fixes.
It will tell him what you are using so he can give you a fix.

---

### Post by martinezlc99 on 2010-03-02
> **VertexPusher said:**
> Let's run some tests to find out what's wrong. Open a terminal window and enter this command:
```
aplay -D default -t raw -c 2 -f S32_LE -r 48000 -d 1 -v /dev/zero
```
This will play back one second of silence and print the PCM structure of the default ALSA audio device. The output will show whether the default device is configured to use dmix, PulseAudio, or no stream mixer at all. Please post the output here.

Next, run Firefox and launch a YouTube video. While the video is playing (with sound), enter the following command into the terminal window:
```
lsof | grep dsp
```
The output will tell us whether Flash uses ALSA or OSS. Post the output here, too.

Thanks for the reply!

Output of aplay -D default -t raw -c 2 -f S32_LE -r 48000 -d 1 -v /dev/zero is

```
Playing raw data '/dev/zero' : Signed 32 bit Little Endian, Rate 48000 Hz, Stereo
Plug PCM: Soft volume PCM
Control: PCM Playback Volume
min_dB: -51
max_dB: 0
resolution: 256
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 8192
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 8192
  stop_threshold   : 8192
  silence_threshold: 0
  silence_size : 0
  boundary     : 4611686018427387904
Slave: Direct Stream Mixing PCM
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 8192
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 8192
  stop_threshold   : 8192
  silence_threshold: 0
  silence_size : 0
  boundary     : 4611686018427387904
Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 8192
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : ENABLE
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 1
  stop_threshold   : 0
  silence_threshold: 0
  silence_size : 0
  boundary     : 4611686018427387904
  appl_ptr     : 0
  hw_ptr       : 8784309280
```

Output of lsof | grep dsp is

```
pulseaudi  2152 martinezlc99  mem       REG                8,6     81496       5054 /usr/lib/libspeexdsp.so.1.5.0
gconf-hel  2226 martinezlc99  mem       REG                8,6     81496       5054 /usr/lib/libspeexdsp.so.1.5.0
```

Thanks for any help!

---

### Post by martinezlc99 on 2010-03-03
Solved this problem by following the advice here:  [http://ubuntuforums.org/showthread.php?t=1412153](http://ubuntuforums.org/showthread.php?t=1412153)

Edited my /etc/asound.conf to include (it was blank):

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

No clue why this worked, but it did and I am happy.

---

### Post by VertexPusher on 2010-03-03
Your default device was configured to use dmix despite the fact that PulseAudio was installed and running. PulseAudio occupies the hardware audio device so that dmix can't access it. That's why the audio applications blocked each other.

The pulseaudio package comes with two files, /usr/share/alsa/pulse-alsa.conf and /usr/share/alsa/pulse.conf, which configure the pulse plugin. ALSA's main configuration file, /usr/share/alsa/alsa.conf, automatically links to those files if they are present.

The conclusion is that either those two files are missing, or the link was removed from alsa.conf. Either way, your system is not in "factory default state". Adding /etc/asound.conf is a possible workaround, but the more elegant way would be to reinstall the packages libasound2 and pulseaudio to bring the original configuration files back.

---

