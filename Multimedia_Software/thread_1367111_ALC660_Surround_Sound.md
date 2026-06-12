---
title: "ALC660 Surround Sound"
date: 2009-12-29
forum: Multimedia Software
---

### Post by chazco on 2009-12-29
Hi,

I'm trying to add 5.1 surround sound to my Ubuntu 9.10 desktop using the on-board soundcard. Everything is connected correctly using the Line-out/Mic/Line-in sockets.

On Ubuntu I do have stereo output, but nothing I've tried will make it support surround. I installed XP, where the same configuration works fine, so it's not a hardware problem.

The motherboard is a GeForce6100SM-M and the codec is a Realtek ALC660 (according to both the XP driver and Alsamixer).

Any ideas?

Thanks in advance :)

---

### Post by n3had on 2009-12-29
This worked for me

[http://ubuntuforums.org/showpost.php?p=6752073&postcount=2](http://ubuntuforums.org/showpost.php?p=6752073&postcount=2)

and then you have to choose 6ch setup on alsamixer

---

### Post by chazco on 2009-12-29
Thanks :)

Tried adding various model options to alsa-base.conf but no luck so far. It seems that Ubuntu just can't detect that the card is surround capable.

---

### Post by VertexPusher on 2009-12-29
The appropriate procedure to enable surround sound depends on which sound system you are using, ALSA or PulseAudio.

No matter which one you use, do not change the ALSA base configuration files. If you need to reconfigure ALSA, use an ".asoundrc" file in your user home directory.

---

### Post by chazco on 2009-12-29
I'm using the default setup for Ubuntu 9.10, which I think is PulseAudio. However, there are no profiles for surround in the volume control applet and editing the default-sample-channels value in /etc/pulse/daemon.conf has no effect.

---

### Post by VertexPusher on 2009-12-29
You can use speaker-test to find out if surround sound works at the ALSA level. For example, if your default sound card is card 0:
```
speaker-test -c 6 -D plughw:0
```

---

### Post by chazco on 2009-12-29
I've been using the speaker test utility (although with a different command that actually speaks the words "Front Left" etc). I only get audio from the front-left and front-right with the utility.

---

### Post by VertexPusher on 2009-12-29
> **chazco said:**
> I've been using the speaker test utility (although with a different command that actually speaks the words "Front Left" etc). I only get audio from the front-left and front-right with the utility.
I don't know the parameters you used for the previous tests, but if the command above doesn't give you 6 channel sound, your sound card is not 5.1 capable.

---

### Post by chazco on 2009-12-29
The command you gave doesn't give 5.1 surround...

The hardware supports it (as was confirmed by installing XP), so I'm guessing its a Linux support problem.

---

### Post by n3had on 2009-12-29
> **chazco said:**
> The command you gave doesn't give 5.1 surround...

The hardware supports it (as was confirmed by installing XP), so I'm guessing its a Linux support problem.

i had the same problem as i've said that already above and after doing the above trick and choosing 6ch setup on alsamixer i finally got the 6ch option on pulseaudio

EDIT: it works for ALC662 chip so i thought it may work for you too

---

### Post by VertexPusher on 2009-12-29
> **chazco said:**
> I'm guessing its a Linux support problem.
Unlikely. I've had several RealTek ALCxxx interfaces, and all of them were 5.1 capable on Linux.

Please run this command and copy its output here.
```
aplay -v -D plughw:0 -f S32_LE -r 48000 -c 6 -t raw -d 1 /dev/zero
```
It will play one second of silence and show a detailed description of the ALSA PCM chain used. Here's what I see (on a RealTek ALC889):
```
Playing raw data '/dev/zero' : Signed 32 bit Little Endian, Rate 48000 Hz, Channels 6
Plug PCM: **Hardware PCM card 0 'HDA Intel' device 0 subdevice 0**
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  **channels     : 6**
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 2688
  period_size  : 672
  period_time  : 14000
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 672
  period_event : 0
  start_threshold  : 2688
  stop_threshold   : 2688
  silence_threshold: 0
  silence_size : 0
  boundary     : 6052837899185946624
  appl_ptr     : 0
  hw_ptr       : 0
```

---

### Post by chazco on 2009-12-29
The output is:

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
Slave: Hardware PCM card 0 'HDA NVidia' device 0 subdevice 0
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

It works under Windows (each speaker can be tested individually) and the motherboard documentation says it's supported.

---

### Post by VertexPusher on 2009-12-29
Interesting. Apparently the plug PCM automatically performs a route conversion from 5.1 surround to 2.0 stereo. This could be due to a bug in the driver. Or it means that the card does not support 32bit samples and 5.1 output at the same time.

In case of a driver bug there is not much we can do right now, but if the card supports 5.1 with 16bit samples, there may be a way to force mixdown to 16bit/5.1 instead of 32bit/2.0.

Please try the following command:
```
aplay -v -D hw:0 -f S16_LE -r 48000 -c 6 -t raw -d 1 /dev/zero
```
This one bypasses the conversion plugin and talks straight to the H/W device, using 16bit samples instead of 32bit ones. Please copy and paste its output here.

---

### Post by chazco on 2009-12-29
Thanks for the help :)

```
Playing raw data '/dev/zero' : Signed 16 bit Little Endian, Rate 48000 Hz, Channels 6
aplay: set_params:984: Channels count not available

```

Doesn't look promising.

---

### Post by VertexPusher on 2009-12-29
Here's what I found about shared input/output connectors:

[http://groups.google.com/group/comp.os.linux.hardware/browse_thread/thread/9f8cb693378130e0?hl=en](http://groups.google.com/group/comp.os.linux.hardware/browse_thread/thread/9f8cb693378130e0?hl=en)
> Date: Wed, 10 Nov 2004 15:11:48 +0100


Oleg Lucha wrote:
> I am on SuSe 9.0 and I have P4P800S motherboard with integrated sound.

This motherboard has shared input/output connectors, hasn't it?

> *** THERE IS NO SOUND FROM MY HEADPHONES !!! ***

The default hardware configuration is to use the shared jacks as
inputs. There are mixer controls "Surround Jack as Input" and
"Center/LFE Jack as Input" to change this.

You need at least ALSA version 1.0.3 for this; I don't know what
ships with your SuSE. (see /proc/asound/version)

HTH
Clemens
Can you find those controls in alsamixer?

---

### Post by chazco on 2009-12-29
Nope, no options related to surround in alsamixer.

---

### Post by chazco on 2009-12-29
Seems like 5.1 isn't supported on Ubuntu...

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/174203](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/174203)

Thanks for the help anyway :)

Update: I've purchased and installed a new sound card, 5.1 surround is now working.

---

