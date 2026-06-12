---
title: "No sound"
date: 2009-02-16
forum: Multimedia Software
---

### Post by f00sh on 2009-02-16
Hey thanks for looking

I have a creative X-Fi fatal1ty sound card

i downloaded and installed Creative ALSA X-fi driver last week and it was working fine.

i just restarted my computer and had no sound when it reloaded.

i checked my sound settings and it displays

**Sound Events **
Sound playback: Creative ALSA Driver X-Fi WaveOut/WaveIn (OSS) (Not Connected)

**Music and Movies**
Sound playback: Creative ALSA Driver X-Fi WaveOut/WaveIn (OSS) (Not Connected)

**Audio Conferencing**
Sound playback: Creative ALSA Driver X-Fi WaveOut/WaveIn (OSS) (Not Connected)

Sound Capture: ALSA - Advanced Linux Sound Architecture

**Default Mixer Tracks**

Device: Capture: ALSA PCM on front:0 (ALC888 Analog) via DMA (PulseAudio Mixer)


im pretty sure that before restart i didnt have (Not Connected) on any of the sounds.


i edited etc/group from audio:x:29:pulse to audio:x:29:reuben

but it didnt do anything,

It detects my card

:reuben@reuben-desktop:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
05:00.0 Multimedia audio controller: Creative Labs SB X-Fi
reuben@reuben-desktop:~$ 

but i dont see my creative here

reuben@reuben-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
reuben@reuben-desktop:~$ 

i just ran this command: lspci -v 

it finds my creative but says access denied?

05:00.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 0023
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at ec00 [size=32]
	Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>



thanks for help

---

### Post by f00sh on 2009-02-16
bump

anyone that can help?

also right now im playing sound through my motherboard soundcard (which turns out to be pretty good never used it before). 

Still problem with my x-fi though!help

:-({|=:-({|=:-({|=

---

### Post by f00sh on 2009-02-17
bump):

---

### Post by f00sh on 2009-02-17
): bump

---

