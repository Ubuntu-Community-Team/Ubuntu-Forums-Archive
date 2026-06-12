---
title: "ASUS PCIe audio card and command line configuration"
date: 2012-04-19
forum: Multimedia Software
---

### Post by MakOwner on 2012-04-19
I have an ASUS PCIe audio card and I need to configure it for analog two speaker output and simple microphone jack recording -- from the command line.

Is this possible in Ubuntu 64bit 10.04LTS?

This card works - ot at least I can record and get audio out of it when loading the full desktop version.  
esound, pulseaduo and alsa all get loaded, and I have no how to tell what if anything is actually in use.
I'm getting really tired of re-installing for yet another try at something that should be pretty simple...

My card 
```

02:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
	Subsystem: ASUSTeK Computer Inc. Device 8275
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at ec00 [size=256]
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: AV200
	Kernel modules: snd-virtuoso

```

---

### Post by cladisch on 2012-04-20
What do you mean with "configure"?
Setting mixer controls? This is possible with amixer.

---

### Post by MakOwner on 2012-04-20
> **cladisch said:**
> What do you mean with "configure"?
Setting mixer controls? This is possible with amixer.

Configure as in getting the system to output sound and record sound on the microphone or line in jack.

I can get it to work with a full desktop install.  This particular setup requires a minimal install.  The minimal install will detect the hardware and load an appripriate driver but loads no other applications or tools for sound.

I have loaded alsa and gone through the alsamixer application. While I'm not positive, I'm pretty sure I have set the capture device appropriately and turned up the output volumes.  And I still get no output from a known good mp3 (podcast from NPR) or am able to record from the line in or mic jack.

I use arecord to record to wav, lame to convert to mp3, aplay and play from sox for testing.

---

### Post by cladisch on 2012-04-20
Please show the output of "[FONT="Courier New"]amixer[/FONT]" and "[FONT="Courier New"]aplay -v something.wav[/FONT]".

---

### Post by MakOwner on 2012-04-20
> **cladisch said:**
> Please show the output of "[FONT="Courier New"]amixer[/FONT]" and "[FONT="Courier New"]aplay -v something.wav[/FONT]".
amixer 
```

amixer version 1.0.22

```

aplay -v (This particular wav is just silence - it was an attempt to record off the card...)

```

# aplay -v LINE_20120419.wav 
Playing WAVE 'LINE_20120419.wav' : Unsigned 8 bit, Rate 44100 Hz, Stereo
Plug PCM: Rate conversion PCM (48000, sformat=S32_LE)
Converter: libspeex (builtin)
Protocol version: 10002
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : U8
  subformat    : STD
  channels     : 2
  rate         : 44100
  exact rate   : 44100 (44100/1)
  msbits       : 8
  buffer_size  : 15052
  period_size  : 940
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 940
  period_event : 0
  start_threshold  : 15052
  stop_threshold   : 15052
  silence_threshold: 0
  silence_size : 0
  boundary     : 4236761349448794112
Slave: Direct Stream Mixing PCM
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 24
  buffer_size  : 16384
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 4611686018427387904
Hardware PCM card 0 'Xonar DX' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 24
  buffer_size  : 16384
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : ENABLE
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 1
  stop_threshold   : 4611686018427387904
  silence_threshold: 0
  silence_size : 4611686018427387904
  boundary     : 4611686018427387904
  appl_ptr     : 0
  hw_ptr       : 1024
#

```

---

### Post by cladisch on 2012-04-20
> amixer 
```

amixer version 1.0.22

```

This is the output of "[FONT="Courier New"]amixer --version[/FONT]". :confused:

Try "[FONT="Courier New"]amixer scontents[/FONT]".

---

### Post by MakOwner on 2012-04-20
> **cladisch said:**
> This is the output of "[FONT="Courier New"]amixer --version[/FONT]". :confused:

Try "[FONT="Courier New"]amixer scontents[/FONT]".

Like this?

```

# amixer scontents
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right
  Limits: Playback 67 - 127
  Mono:
  Front Left: Playback 121 [90%] [-6.00dB] [off]
  Front Right: Playback 121 [90%] [-6.00dB] [off]
  Rear Left: Playback 121 [90%] [-6.00dB] [off]
  Rear Right: Playback 121 [90%] [-6.00dB] [off]
  Front Center: Playback 121 [90%] [-6.00dB] [off]
  Woofer: Playback 121 [90%] [-6.00dB] [off]
  Side Left: Playback 121 [90%] [-6.00dB] [off]
  Side Right: Playback 121 [90%] [-6.00dB] [off]
Simple mixer control 'Front Panel',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Line',0
  Capabilities: cswitch cswitch-joined penum
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 31 [100%] [12.00dB] [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Aux',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [12.00dB] [off]
  Front Right: Capture 31 [100%] [12.00dB] [off]
Simple mixer control 'Analog Input Monitor',0
  Capabilities: volume volume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 1
  Mono: 1 [100%] [0.00dB] Playback [off]
Simple mixer control 'Stereo Upmixing',0
  Capabilities: enum
  Items: 'Front' 'Front+Surround' 'Front+Surround+Back'
  Item0: 'Front+Surround'


```

---

### Post by cladisch on 2012-04-20
> [FONT="Courier New"]Front Left: Playback 121 [90%] [-6.00dB] [off][/FONT]
The "Master" control is muted.
(And the selected capture source is line input.)

---

### Post by MakOwner on 2012-04-20
> **cladisch said:**
> The "Master" control is muted.
(And the selected capture source is line input.)

And that may be my problem -- I thought I had everything on and at full volume.  I flip the mute with the 'm' key?
Trying that now...

---

