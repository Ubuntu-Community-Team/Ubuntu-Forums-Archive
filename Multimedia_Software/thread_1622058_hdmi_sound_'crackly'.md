---
title: "hdmi sound 'crackly'"
date: 2010-11-15
forum: Multimedia Software
---

### Post by bric on 2010-11-15
After reading numerous posts on the forums I found 'system' > 'preferences' > 'sound' (should have been obvious) and set the hardware to 'digital stereo (hdmi) output'.

Presto, from no sound to sound via hdmi.  But the sound is terrible.

I tried playing a movie and when it should be silent there is crackly static.  When people talk or music plays, it is distorted with noise.  I'm not sure how to describe it.

I've just installed ubuntu on an MSI H55M E33 motherboard.

Am I out of luck or is there something more I can do to fix the sound?

note that this is a new install of Maverick

---

### Post by bric on 2010-11-15
I've also heard the sound described as scratchy or static(y).

Anyhow, I ran alsamixer and after going far to the right I encounter "S/PDIF 1".  If I mute this (m key) then the (scratchy) sound is muted ... so obviously that's the 'channel' on which the hdmi sound is being carried.

Can anyone use this info to help me diagnose the scratchy nature of the hdmi audio?

---

### Post by wonko on 2010-11-22
I too have this problem on Kubuntu 10.10 running on an Asus S1 with ION 2 graphics and Intel NM10 express chipset.

---

### Post by bric on 2010-11-22
I'm just using the analog outputs for now. Though that's not ideal it gets the job done.

If you figure anything out let me know. (or perhaps someone else will see this).

---

### Post by TicTak on 2010-11-25
I've been trying to fix this problem for myself and I think I've honed in a little on exactly what's breaking. I have an onboard NVidia as well possibly the same one as the OP.

First of all let me clarify the problem. The sound is **not** distorted intermittently, it sounds that way all the time. It is **not** skipping (which is why the tsched=0 fix doesn't work). I've gotten my sound to work properly in one case: using aplay with the -D flag. Everywhere else I've tried it is broken.

Try running 

```

aplay -v /usr/share/sounds/alsa/Front_Center.wav

```and

```

aplay -vD plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav

```For me the second command plays clean sound while the first is garbled. I used "plughw:0,3" because that is my hdmi sound device as you can see:

```

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Now if you look at the output from the two commands I ran earlier you'll notice the second is bypassing pulseaudio (I'm guessing based on the lines I bolded):

```

~$ aplay -v /usr/share/sounds/alsa/Front_Center.wav Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
**ALSA <-> PulseAudio PCM I/O Plugin**
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 24000
  period_size  : 6000
  period_time  : 125000
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 6000
  period_event : 0
  start_threshold  : 24000
  stop_threshold   : 24000
  silence_threshold: 0
  silence_size : 0
  boundary     : 1572864000

``````

~$ aplay -vD plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav 
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
[B]Plug PCM: Route conversion PCM (sformat=S16_LE)
  Transformation table:
    0 <- 0
    1 <- 0[/B]
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 24064
  period_size  : 6016
  period_time  : 125333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 6016
  period_event : 0
  start_threshold  : 24064
  stop_threshold   : 24064
  silence_threshold: 0
  silence_size : 0
  boundary     : 1577058304
Slave: Hardware PCM card 0 'HDA NVidia' device 3 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 24064
  period_size  : 6016
  period_time  : 125333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 6016
  period_event : 0
  start_threshold  : 24064
  stop_threshold   : 24064
  silence_threshold: 0
  silence_size : 0
  boundary     : 1577058304
  appl_ptr     : 0
  hw_ptr       : 0

```And if I edit my .asoundrc file with this:

```

pcm.!default {
       type plug
       slave.pcm {
               type hw
               card 0
               device 3
       }
} 

```then the aplay command works even without the -D flag. However, sound is still scratchy everywhere else.

The analogs work fine and apparently raw alsa for hdmi does too. So I think the problem is on the handoff of hdmi audio from alsa to pulse. Or possibly pulse alters the output format to something my tv can't handle.

---

### Post by bric on 2010-11-27
Well that gives me something to play with ... though I feel a bit like I'm just poking it with a stick (hoping something will happen but that it won't bite me).

I think the integrated graphics on the MSI board are the Intel HD variety ('GMA HD' or 'HD Graphics').

The computer is sitting at my folks place now so I'll play with this as soon as I get a chance.

-

Whoops, you said nvidia so I was thinking video for some reason (and haven't been dealing with this issue for a while).

I should have said, my integrated AUDIO is intel HD (and I've seen ALC892 listed too).

---

### Post by lidex on 2010-11-27
> **bric said:**
> Well that gives me something to play with ... though I feel a bit like I'm just poking it with a stick (hoping something will happen but that it won't bite me).

I think the integrated graphics on the MSI board are the Intel HD variety ('GMA HD' or 'HD Graphics').

The computer is sitting at my folks place now so I'll play with this as soon as I get a chance.

-

Whoops, you said nvidia so I was thinking video for some reason (and haven't been dealing with this issue for a while).

I should have said, my integrated AUDIO is intel HD (and I've seen ALC892 listed too).
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

