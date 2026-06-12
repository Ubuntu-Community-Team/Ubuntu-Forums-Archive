---
title: "Bluetooth headset can't work with arecord -D bluetooth"
date: 2009-12-29
forum: Multimedia Software
---

### Post by eye1721 on 2009-12-29
Hi,
I'm testing my bluetooth headset recently,but here i got a problem to record sound using arecord. 

OS: ubuntu 9.10.
Bluetooth headset: Nokia BH-503 Bluetooth Stereo
I can play the sound via bluetooth headset perfectly, also I can record the sound via bluetooth headset with following command:
:~$ arecord -vvv -f s16_le -r 16000 [ww]("http://www.wav")
but if i specific the device "-D bluetooth", the record funciton can't work.
I don't know why there are Plug PCM and Slave, i'm really a newbie.
:~$ arecord -vvv -D bluetooth -r 16000 [ww]("http://www.wav")
[html]
Recording WAVE 'ww' : Unsigned 8 bit, Rate 16000 Hz, Mono
Plug PCM: Linear conversion PCM (S16_LE)
Its setup is:
  stream       : CAPTURE
  access       : RW_INTERLEAVED
  format       : U8
  subformat    : STD
  channels     : 1
  rate         : 16000
  exact rate   : 16000 (16000/1)
  msbits       : 8
  buffer_size  : 12288
  period_size  : 2048
  period_time  : 128000
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 2048
  period_event : 0
  start_threshold  : 1
  stop_threshold   : 12288
  silence_threshold: 0
  silence_size : 0
  boundary     : 1610612736
Slave: Bluetooth Audio Device
Its setup is:
  stream       : CAPTURE
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 16000
  exact rate   : 16000 (16000/1)
  msbits       : 16
  buffer_size  : 12288
  period_size  : 2048
  period_time  : 128000
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 2048
  period_event : 0
  start_threshold  : 1
  stop_threshold   : 12288
  silence_threshold: 0
  silence_size : 0
  boundary     : 1610612736
Max peak (2048 samples): 0x00000079 ###################  94%
c^CAborted by signal Interrupt...
[/html]I thought that the reason of the failure was incompatible format,so i tried this:
:~$:~$ arecord -vvv -f s16_le -D bluetooth -r 16000 [ww]("http://www.wav")
it got even worse!
```

Recording WAVE 'ww' : Signed 16 bit Little Endian, Rate 16000 Hz, Mono
Plug PCM: Bluetooth Audio Device
Its setup is:
  stream       : CAPTURE
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 16000
  exact rate   : 16000 (16000/1)
  msbits       : 16
  buffer_size  : 12288
  period_size  : 2048
  period_time  : 128000
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 2048
  period_event : 0
  start_threshold  : 1
  stop_threshold   : 12288
  silence_threshold: 0
  silence_size : 0
  boundary     : 1610612736

```/proc/asound/card0$ cat codec#0
```

Codec: Conexant ID 5069
Address: 0
Function Id: 0x1
Vendor Id: 0x14f15069
Subsystem Id: 0x17aa214c
Revision Id: 0x100301
No Modem Function Group found
Default PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x10 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x3a 0x3a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x3c 0x3c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power: setting=D0, actual=D0
Node 0x13 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0f, mute=0
  Amp-Out vals:  [0x00]
Node 0x14 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x3c 0x3c] [0x4a 0x4a] [0x40 0x40] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 4
     0x17 0x18 0x23* 0x24
Node 0x15 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x16 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x17 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x04 0x04]
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a 0x1b* 0x1d 0x1e
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x042110f0: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1a [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00001324: IN Detect
    Vref caps: HIZ 50 80
  Pin Default 0x61a190f0: [N/A] Mic at Sep Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00011334: IN OUT EAPD Detect
    Vref caps: HIZ 50 80
  EAPD 0x0:
  Pin Default 0x04a110f0: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1c [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x612140f0: [N/A] HP Out at Sep Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x0:
  Pin Default 0x40f001f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1e [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x40f001f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x901701f0: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f001f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power: setting=D0, actual=D0
Node 0x22 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f001f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
Node 0x23 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x04, stepsize=0x2f, mute=0
  Amp-In vals:  [0x04 0x04]
  Pincap 0x00000020: IN
  Pin Default 0x90a601f0: [Fixed] Mic at Int N/A
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power: setting=D0, actual=D0
Node 0x24 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11
Node 0x25 [Vendor Defined Widget] wcaps 0xf00000: Mono

``````

$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Dec  2 2009 for kernel 2.6.31-16-generic (SMP).

```would someone let me know what's wrong?Thanks in advance

---

### Post by pumo on 2010-01-05
How did you manage to pair headset with computer? 
I cant even see by scanning ( hcitool scan )
```

$ dpkg -la|grep blue
ii  blueman                               1.10-3ubuntu1                              A Graphical bluetooth manager
ii  bluetooth                             4.57-0ubuntu1                              Bluetooth support
ii  bluez                                 4.57-0ubuntu1                              Bluetooth tools and daemons
ii  bluez-alsa                            4.57-0ubuntu1                              Bluetooth audio support
ii  bluez-cups                            4.57-0ubuntu1                              Bluetooth printer driver for CUPS
ii  bluez-gstreamer                       4.57-0ubuntu1                              Bluetooth GStreamer support
ii  bluez-utils                           4.57-0ubuntu1                              Transitional package
ii  gnome-bluetooth                       2.28.1-0ubuntu2                            GNOME Bluetooth tools
ii  libbluetooth3                         4.57-0ubuntu1                              Library to use the BlueZ Linux Bluetooth sta
ii  libgnome-bluetooth7                   2.28.1-0ubuntu2                            GNOME Bluetooth tools - support library
ii  pulseaudio-module-bluetooth           1:0.9.19-0ubuntu4                          Bluetooth module for PulseAudio sound server


```

---

### Post by ktechman on 2010-01-05
Just asking, did either one of you install the other bluetooth software 'Blueman' it removes *gnome-bluetooth* here is the link to the PPA [http://blueman-project.org/downloads.htm]("http://blueman-project.org/downloads.htm") it works better IMHO
Ktechman

---

