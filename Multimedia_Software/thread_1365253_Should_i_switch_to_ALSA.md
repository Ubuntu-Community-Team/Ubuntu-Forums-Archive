---
title: "Should i switch to ALSA?"
date: 2009-12-27
forum: Multimedia Software
---

### Post by higashi on 2009-12-27
i remember switching to Pulseaudio while using jaunty because ALSA wasn't able to play sound for more than one application at a time. Now that i've upgraded to karmic, it already has pulseaudio set up, but the sound quality is REALLY bad. 

Now i'm wondering if switching to ALSA would fix the quality of my sound, and if you think it's worth it to only be able to listen to one application at a time.

Or is there a way that i can keep pulseaudio but not have crappy sound?

---

### Post by higashi on 2009-12-30
bumo

---

### Post by VertexPusher on 2009-12-30
> **higashi said:**
> ALSA wasn't able to play sound for more than one application at a time.
I can't fix your PulseAudio problem, but I can show you how to set up ALSA so that many applications can use the sound card simultaneously.

---

### Post by higashi on 2009-12-30
please do
hopefully alsa will sound better..

---

### Post by VertexPusher on 2009-12-31
OK, I need some info about your sound card(s). Enter these commands, one after another, into a terminal window and copy their output here.
```
aplay -l
arecord -l
aplay -v -D plughw:0 -f S32_LE -r 48000 -c 6 -t raw -d 1 /dev/zero
aplay -v -D plughw:0 -f S16_LE -r 48000 -c 6 -t raw -d 1 /dev/zero
```
The first two commands will return a list of all the sound cards in your computer. The third and fourth command will play back one second of silence on the first sound card (card 0) and print info about any conversions (sample format, sample rate, number of channels) that need to take place. There will also be info about the audio buffer sizes of the card.

We're going to use that info to create a .asoundrc file that you can put into your user home directory. This file will reconfigure ALSA's default PCM in a way that enables stream mixing so that multiple applications can share the sound card.

---

### Post by higashi on 2010-01-01
aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

arecord -l
```
**** List of CAPTURE Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 1: Intel ICH - MIC ADC [Intel ICH5 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 2: Intel ICH - MIC2 ADC [Intel ICH5 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 3: Intel ICH - ADC2 [Intel ICH5 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

aplay -v -D plughw:0 -f S32_LE -r 48000 -c 6 -t raw -d 1 /dev/zero
```
Playing raw data '/dev/zero' : Signed 32 bit Little Endian, Rate 48000 Hz, Channels 6
Plug PCM: Route conversion PCM (sformat=S32_LE)
  Transformation table:
    0 <- 0
    1 <- 1
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 6
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 8192
  period_size  : 2048
  period_time  : 42666
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 2048
  period_event : 0
  start_threshold  : 8192
  stop_threshold   : 8192
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Slave: Hardware PCM card 0 'Intel ICH5' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 20
  buffer_size  : 8192
  period_size  : 2048
  period_time  : 42666
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 2048
  period_event : 0
  start_threshold  : 8192
  stop_threshold   : 8192
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
  appl_ptr     : 0
  hw_ptr       : 0

```

aplay -v -D plughw:0 -f S16_LE -r 48000 -c 6 -t raw -d 1 /dev/zero
```
Playing raw data '/dev/zero' : Signed 16 bit Little Endian, Rate 48000 Hz, Channels 6
Plug PCM: Route conversion PCM (sformat=S16_LE)
  Transformation table:
    0 <- 0
    1 <- 1
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 6
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 4096
  period_time  : 85333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 4096
  period_event : 0
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Slave: Hardware PCM card 0 'Intel ICH5' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 4096
  period_time  : 85333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 4096
  period_event : 0
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
  appl_ptr     : 0
  hw_ptr       : 0

```

---

### Post by VertexPusher on 2010-01-04
Try this:
```
pcm.!default {
    type plug
    slave.pcm {
        type asym
        playback.pcm {
            type dmix
            ipc_key 10001
            slave {
                pcm {
                    type hw
                    card ICH5
                    device 0
                }
                format S32_LE
                rate 48000
                channels 2
                period_size 2048
                buffer_size 8192
            }
        }
        capture.pcm {
            type hw
            card ICH5
            device 0
        }
    }
}
```
Save this as ".asoundrc" in your user home directory, then log out and log in again. Now the ALSA device "default" will mix audio streams from multiple applications and output them at 48kHz stereo.

---

### Post by higashi on 2010-01-06
ugh, i switched to ALSA and my sound quality problems havent been solved at all. I have no idea what i'm going to do about this.

Does anyone have any other suggestions? My sound is TERRIBLE. The bass is fuzzy... almost as if i'm listening to some 8bit song (although.. not quite). Pulseaudio and ALSA sound exactly the same, I dont know what to do! D:

---

### Post by 3rdalbum on 2010-01-06
> **higashi said:**
> ugh, i switched to ALSA and my sound quality problems havent been solved at all. I have no idea what i'm going to do about this.

Does anyone have any other suggestions? My sound is TERRIBLE. The bass is fuzzy... almost as if i'm listening to some 8bit song (although.. not quite). Pulseaudio and ALSA sound exactly the same, I dont know what to do! D:

If I'd gotten to this thread first, I would have advised you to go to the "alsamixer" volume control (in the terminal) and turned down the "PCM" channel to around 90%.

---

