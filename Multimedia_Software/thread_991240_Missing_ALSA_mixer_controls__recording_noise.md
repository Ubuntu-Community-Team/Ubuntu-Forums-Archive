---
title: "Missing ALSA mixer controls / recording noise"
date: 2008-11-23
forum: Multimedia Software
---

### Post by EasyRiderOnTheStorm on 2008-11-23
Audio seems to work for me by and large, but controls seem to be missing from the ALSA mixer: There's no +20dB Mic Boost switch and no controls at all for the Aux input (these exist in hardware of course, and are visible under Windows). I'm not even mentioning SPDIF access (of which I see no trace even though it's supposed to also exist), since I'm not using it (yes, no IEC958 stuff either).

The other **very** annoying thing is a fairly loud noise on recording; It's affecting CD-in, in record mode (CD-in capture volume down or capture-some-other-input gets rid of it), yet it's not coming throuh CD-in, as directly listening to that input as playback-only is perfectly noise-free. Everything else is of course set to volume zero and don't-capture during this...

amixer output: 
```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [-35.00dB] [off]
  Front Right: Playback 0 [0%] [-35.00dB] [off]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-64.00dB] [off]
  Front Right: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [-35.00dB] [off]
  Front Right: Playback 0 [0%] [-35.00dB] [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [-35.00dB] [off]
  Front Right: Playback 0 [0%] [-35.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [-35.00dB] [off]
  Front Right: Playback 0 [0%] [-35.00dB] [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [-35.00dB] [off]
  Front Right: Playback 0 [0%] [-35.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 35
  Front Left: Capture 28 [80%] [28.00dB] [on]
  Front Right: Capture 28 [80%] [28.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 35
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 35
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'CD'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'CD'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'CD'
```

lspci -v output:
```
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device e310
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

```

contents of /proc/asound/card0/codec#2:
```
Codec: Realtek ALC880
Address: 2
Vendor Id: 0x10ec0880
Subsystem Id: 0x0
Revision Id: 0x70400
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0
Node 0x02 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x23, stepsize=0x03, mute=1
  Amp-In vals:  [0x1c 0x1c] [0x1c 0x1c] [0x1c 0x1c] [0x1c 0x1c] [0x1c 0x1c] [0x1c 0x1c] [0x1c 0x1c]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 7
     0x18 0x19 0x1a 0x1b 0x1c* 0x14 0x15
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x23, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 7
     0x18 0x19 0x1a 0x1b 0x1c* 0x14 0x15
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x23, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c* 0x0b 0x14 0x15 0x16 0x17
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x23, nsteps=0x41, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 8
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 4
     0x0c 0x0d 0x0e* 0x0f
Node 0x11 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 4
     0x0c* 0x0d 0x0e 0x0f
Node 0x12 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 4
     0x0c 0x0d 0x0e 0x0f*
Node 0x13 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 4
     0x0c* 0x0d 0x0e 0x0f
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x083f: IN OUT HP Detect Trigger ImpSense
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0c
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x083f: IN OUT HP Detect Trigger ImpSense
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0d
Node 0x16 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x083f: IN OUT HP Detect Trigger ImpSense
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x083f: IN OUT HP Detect Trigger ImpSense
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08133f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 80
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x10
Node 0x19 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x08133f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 80
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x11
Node 0x1a [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08133f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 80
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x12
Node 0x1b [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08133f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 80
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x13
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x99331000: [Fixed] CD at Int ATAPI
    Conn = ATAPI, Color = Black
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x0820: IN
  Pin Default 0x907f1000: [Fixed] Modem Hand at Int N/A
    Conn = Other, Color = Black
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x0810: OUT
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x0820: IN
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=10
Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono
  Volume-Knob: delta=0, steps=64, direct=0, val=25
  Unsolicited: tag=00, enabled=0
  Connection: 0

```

---

### Post by AliTabuger7 on 2008-11-23
I am not too experienced with ALSA sound, but I'd just like to throw out there that the static/noise could be caused by poor wiring or poor connections.

How was it working before?

---

### Post by EasyRiderOnTheStorm on 2008-11-23
> **AliTabuger7 said:**
> I am not too experienced with ALSA sound, but I'd just like to throw out there that the static/noise could be caused by poor wiring or poor connections.

That's not likely, for as I said, in replay mode of the same channel no noise is present, therefore the noise must originate on some other channel left open by the alsa mixer or on the motherboard itself - it cannot be coming in on that input.

> **AliTabuger7 said:**
> How was it working before?

There is no 'before'. This is a mythbuntu box I've just put together; because of the noise, I'm constrained to record through /dev/dsp1 (instead of /dev/dsp) which I presume is the PCI-bus-data alsa-DMA output of my TV tuner card, since it seems not to pass through the mobo mixer. I'd much rather record through the audio cable (which now enters as the CD-in, since as I mentioned my AUX input is nowhere to be found under mythbuntu), but the noise is prohibitive.

---

### Post by markbuntu on 2008-11-23
The noise is most likely from an capture input left on. It may be that you need to configure the alsa-base with some option for that sound chip to work properly since acer has most likely tewaked the firmware. more on that and other general troubleshooting and setup tips here:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by EasyRiderOnTheStorm on 2008-12-02
> **markbuntu said:**
> The noise is most likely from an capture input left on. It may be that you need to configure the alsa-base with some option for that sound chip to work properly since acer has most likely tewaked the firmware.

That's what I thought at first too. However, the capture ADC takes it's input from a MUX switch in the codec, and in theory, once the CD input is selected, the state of any other inputs is irrelevant. 

Curiously, the codec status in /proc lists a volume control for each input coming into the MUX, and they are **all** unmuted when capturing, regardless of which one is selected by the MUX. The curious part is that the datasheet lists a single gain/mute control for the output of the MUX, not one for **each input**. 

This might be an interpretation error though: I tried to modify an individual volume/mute of the MUX (quick'n'ugly(TM) source hack) and all values got modified, so either (a) I'm doing something woefully wrong and Alsa applies the setting to all controls in spite of my intentions or (b) there's just one physical register, as the datasheet says, but for some reason Alsa sees it multiple times, once for each input.

Furthermore, just to make thing even more confusing, the source of the noise just got more mysterious. Let me explain:

Monitoring of levels that go to a capture input is not trivial - you need something to start capturing that input and show you the results either as an on-screen vu-level meter, or play the sound right back on the playback output (**and** you need a tuner app active, so sound is coming in on CD-in from the tuner). MythTv did just that (well, after compressing-decompressing it), so I used that to gauge the noise, and never thought to check otherwise. Remember, the TV tuner's DMA output was/is noise-free with this method.

However, while using said TV tuner-DMA-output in mythtv, the "noisy" through-the-sound-card capture input remained free, and I tried to record it briefly (using arecord). To my surprise, it *seems* noise-free. The same thing, if I point MythTv to use it, is again noisy. The tuner-DMA-output is still noise-free.

The fact is, I've been messing with all this quite a bit now, including compiling different version of Alsa, so everything must be thoroughly re-tested and re-verified before I can attempt any conclusions; but right now, that's the way it looks. No single element can logically be blamed for the noise, yet it's there when MythTv captures that input. So stay tuned, I'll get back to this when I know more...

---

### Post by markbuntu on 2008-12-02
Mythtv might be making faulty assumptions about the sound driver which is a big big no-no since applications are not supposed to make ANY assumptions about the low level drivers or address them directly, this is the job of the sound server. 

Many application devs, wine, flash, skype among others have fallen into this trap so I would suspect something wrong with how Mythtv goes about its business with the sound drivers/servers.

---

