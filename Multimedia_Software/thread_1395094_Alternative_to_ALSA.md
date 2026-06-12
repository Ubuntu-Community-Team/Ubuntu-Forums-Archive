---
title: "Alternative to ALSA"
date: 2010-01-31
forum: Multimedia Software
---

### Post by karmic-koala on 2010-01-31
Is there an alternative to ALSA? My microphone works, but the recorded sound is very weak and cracks. Same sound card works like a charm in Windows.

Skype is the only thing holding me back from ditching Windows. Skype in Ubuntu is just not the same audio quality.

Has anybody had any success with OSS?

---

### Post by ratcheer on 2010-01-31
Yes, the main alternative to ALSA is OSS. I have never used OSS, but those who do, swear by it.

[http://www.opensound.com/oss.html](http://www.opensound.com/oss.html)

Tim

---

### Post by kronictokr on 2010-01-31
this fixed pretty much all my sound problems, and made it sound better even, give it a try if you like
[http://ubuntuforums.org/showthread.php?t=1395089](http://ubuntuforums.org/showthread.php?t=1395089)

---

### Post by Psumi on 2010-01-31
I've used OSS as well, but quite frankly, I had issues with it, static, buzzing noises, and much louder sound altogether. If you can fix alsa, I would go with that.

---

### Post by karmic-koala on 2010-02-05
Just installed OSS. No sound after about an hour's tweeking effort. I can get osstest to play some sample sounds but no application can output any sound. Volume control is also missing from panel.

Any OSS users know what might be going wrong. 

=====================Output from ossmix===================

Selected mixer 0/High Definition Audio ALC883
Known controls are:
jack.black.mode <front|rear|center/LFE|side|pcm4|input> (currently front)
jack.black [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.black.mute ON|OFF (currently OFF)
jack.pink.mode <front|rear|center/LFE|side|pcm4|input> (currently front)
jack.pink [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.pink.mute ON|OFF (currently OFF)
jack.green.mode <front|rear|center/LFE|side|pcm4|input> (currently input)
jack.green [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.green.mute ON|OFF (currently OFF)
record.mix.mute.mic1 ON|OFF (currently OFF)
record.mix.mute.linein1 ON|OFF (currently OFF)
record.mix.mute.int-cd1 ON|OFF (currently OFF)
record.mix.mute.int-linein1 ON|OFF (currently OFF)
record.mix.mute.black1 ON|OFF (currently OFF)
record.mix.mute.input-mix1 ON|OFF (currently OFF)
record.mix1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
record.mix.mute.mic2 ON|OFF (currently OFF)
record.mix.mute.linein2 ON|OFF (currently OFF)
record.mix.mute.int-cd2 ON|OFF (currently OFF)
record.mix.mute.int-linein2 ON|OFF (currently OFF)
record.mix.mute.black2 ON|OFF (currently OFF)
record.mix.mute.input-mix2 ON|OFF (currently OFF)
record.mix2 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.mic [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.linein [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.int-cd [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.int-linein [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.black [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.input-mix <mic|linein|int-cd|int-linein> (currently mic)
misc.front-mute ON|OFF (currently OFF)
misc.input-mix-mute1 ON|OFF (currently OFF)
misc.front1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.front2 <front|input-mix> (currently front)
misc.rear-mute ON|OFF (currently OFF)
misc.input-mix-mute2 ON|OFF (currently OFF)
misc.rear1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.rear2 <rear|input-mix> (currently rear)
misc.center/lfe-mute ON|OFF (currently OFF)
misc.input-mix-mute3 ON|OFF (currently OFF)
misc.center/lfe1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.center/lfe2 <center/LFE|input-mix> (currently center/LFE)
misc.side-mute ON|OFF (currently OFF)
misc.input-mix-mute4 ON|OFF (currently OFF)
misc.side1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.side2 <side|input-mix> (currently side)
misc.pcm4-mute ON|OFF (currently OFF)
misc.input-mix-mute5 ON|OFF (currently OFF)
misc.pcm41 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.pcm42 <pcm4|input-mix> (currently pcm4)
vmix0-enable ON|OFF (currently ON)
vmix0-rate <decimal value> (currently 48000) (Read-only)
vmix0-channels <Stereo|Multich> (currently Stereo)
vmix0-src <Fast|High|OFF> (currently Fast)
vmix0-outvol <monovol> (currently 25.0 dB)
vmix0-invol <monovol> (currently 25.0 dB)
vmix0.pcm10 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm11 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm12 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm13 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)

==============output from ossinfo -v3====================

Version info: OSS 4.2 (b 2002/200911060720) (0x00040100) TRIAL
Platform: Linux/x86_64 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 (linuxbook)

Number of audio devices:	10
Number of audio engines:	14
Number of MIDI devices:		0
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 ATI HD Audio interrupts=1159 (1159)
    HD Audio controller ATI HD Audio
    Vendor ID    0x1002437b
    Subvendor ID 0x1025009f
     Codec  0: ALC883 (0x10ec0883/0x1025140d)
     Codec  1: Conexant2bfa (0x14f12bfa)
     Codec  3: Not present
 2: oss_usb0 USB audio core services

MIDI devices (/dev/midi*)

Mixer devices
 0: High Definition Audio ALC883 (Mixer 0 of device object 1)
    Device file /dev/oss/oss_hdaudio0/mix0, Legacy device /dev/mixer0
    Priority: 10
    Caps: 
    Device handle: PCI009f1025-0000:00:14.2-mx01
    Device priority: 10


Audio devices
HD Audio play front               /dev/oss/oss_hdaudio0/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Out engine  1: 0/HD Audio play front
                     Available for use 
      Engine      2: 10/HD Audio play front (vmix)
                     Available for use 
      Engine      3: 11/HD Audio play front (vmix)
                     Available for use 
      Engine      4: 12/HD Audio play front (vmix)
                     Available for use 
      Engine      5: 13/HD Audio play front (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au01
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 8
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play rear                /dev/oss/oss_hdaudio0/pcm1  (device index 1)
    Legacy device /dev/dsp1
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 1/HD Audio play rear
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au02
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play center/LFE          /dev/oss/oss_hdaudio0/pcm2  (device index 2)
    Legacy device /dev/dsp2
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 2/HD Audio play center/LFE
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au03
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play side                /dev/oss/oss_hdaudio0/pcm3  (device index 3)
    Legacy device /dev/dsp3
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 3/HD Audio play side
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au04
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm4                /dev/oss/oss_hdaudio0/pcm4  (device index 4)
    Legacy device /dev/dsp4
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 4/HD Audio play pcm4
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au05
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play modem-out           /dev/oss/oss_hdaudio0/pcm5  (device index 5)
    Legacy device /dev/dsp5
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 5/HD Audio play modem-out
                     Available for use 
    Input formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Output formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au06
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 16000 - 48000 (16000,48000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play spdif-out           /dev/oss/oss_hdaudio0/spdout0  (device index 6)
    Legacy device /dev/dsp6
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 6/HD Audio play spdif-out
                     Available for use 
    Input formats (0x00001410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au07
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin0  (device index 7)
    Legacy device /dev/dsp7
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      In engine   1: 7/HD Audio rec mix
                     Available for use 
      Engine      2: 10/HD Audio play front (vmix)
                     Available for use 
      Engine      3: 11/HD Audio play front (vmix)
                     Available for use 
      Engine      4: 12/HD Audio play front (vmix)
                     Available for use 
      Engine      5: 13/HD Audio play front (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au08
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin1  (device index 8)
    Legacy device /dev/dsp8
    Caps: TRIGGER MMAP 
    Modes: INPUT  
      In engine   1: 8/HD Audio rec mix
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au09
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec modem-out            /dev/oss/oss_hdaudio0/pcmin2  (device index 9)
    Legacy device /dev/dsp9
    Caps: TRIGGER MMAP 
    Modes: INPUT  
      In engine   1: 9/HD Audio rec modem-out
                     Available for use 
    Input formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Output formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au10
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 16000 - 48000 (16000,48000)
    HW Type: Not indicated.
    Minimum latency: Not indicated


Nodes
  /dev/dsp -> /dev/oss/oss_sbxfi0/pcm0
  /dev/dsp_in -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_out -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_ac3 -> /dev/oss/oss_hdaudio0/spdout0
  /dev/dsp_mmap -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_multich -> /dev/oss/oss_hdaudio0/pcm0

---

### Post by karmic-koala on 2010-02-05
Just installed OSS. No sound after about an hour's tweeking effort. I can get osstest to play some sample sounds but no application can output any sound. Volume control is also missing from panel.

Any OSS users know what might be going wrong. 
```

=====================Output from ossmix===================

Selected mixer 0/High Definition Audio ALC883
Known controls are:
jack.black.mode <front|rear|center/LFE|side|pcm4|input> (currently front)
jack.black [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.black.mute ON|OFF (currently OFF)
jack.pink.mode <front|rear|center/LFE|side|pcm4|input> (currently front)
jack.pink [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.pink.mute ON|OFF (currently OFF)
jack.green.mode <front|rear|center/LFE|side|pcm4|input> (currently input)
jack.green [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.green.mute ON|OFF (currently OFF)
record.mix.mute.mic1 ON|OFF (currently OFF)
record.mix.mute.linein1 ON|OFF (currently OFF)
record.mix.mute.int-cd1 ON|OFF (currently OFF)
record.mix.mute.int-linein1 ON|OFF (currently OFF)
record.mix.mute.black1 ON|OFF (currently OFF)
record.mix.mute.input-mix1 ON|OFF (currently OFF)
record.mix1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
record.mix.mute.mic2 ON|OFF (currently OFF)
record.mix.mute.linein2 ON|OFF (currently OFF)
record.mix.mute.int-cd2 ON|OFF (currently OFF)
record.mix.mute.int-linein2 ON|OFF (currently OFF)
record.mix.mute.black2 ON|OFF (currently OFF)
record.mix.mute.input-mix2 ON|OFF (currently OFF)
record.mix2 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.mic [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.linein [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.int-cd [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.int-linein [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.black [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.input-mix <mic|linein|int-cd|int-linein> (currently mic)
misc.front-mute ON|OFF (currently OFF)
misc.input-mix-mute1 ON|OFF (currently OFF)
misc.front1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.front2 <front|input-mix> (currently front)
misc.rear-mute ON|OFF (currently OFF)
misc.input-mix-mute2 ON|OFF (currently OFF)
misc.rear1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.rear2 <rear|input-mix> (currently rear)
misc.center/lfe-mute ON|OFF (currently OFF)
misc.input-mix-mute3 ON|OFF (currently OFF)
misc.center/lfe1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.center/lfe2 <center/LFE|input-mix> (currently center/LFE)
misc.side-mute ON|OFF (currently OFF)
misc.input-mix-mute4 ON|OFF (currently OFF)
misc.side1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.side2 <side|input-mix> (currently side)
misc.pcm4-mute ON|OFF (currently OFF)
misc.input-mix-mute5 ON|OFF (currently OFF)
misc.pcm41 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.pcm42 <pcm4|input-mix> (currently pcm4)
vmix0-enable ON|OFF (currently ON)
vmix0-rate <decimal value> (currently 48000) (Read-only)
vmix0-channels <Stereo|Multich> (currently Stereo)
vmix0-src <Fast|High|OFF> (currently Fast)
vmix0-outvol <monovol> (currently 25.0 dB)
vmix0-invol <monovol> (currently 25.0 dB)
vmix0.pcm10 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm11 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm12 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm13 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)

==============output from ossinfo -v3====================

Version info: OSS 4.2 (b 2002/200911060720) (0x00040100) TRIAL
Platform: Linux/x86_64 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 (linuxbook)

Number of audio devices:	10
Number of audio engines:	14
Number of MIDI devices:		0
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 ATI HD Audio interrupts=1159 (1159)
    HD Audio controller ATI HD Audio
    Vendor ID    0x1002437b
    Subvendor ID 0x1025009f
     Codec  0: ALC883 (0x10ec0883/0x1025140d)
     Codec  1: Conexant2bfa (0x14f12bfa)
     Codec  3: Not present
 2: oss_usb0 USB audio core services

MIDI devices (/dev/midi*)

Mixer devices
 0: High Definition Audio ALC883 (Mixer 0 of device object 1)
    Device file /dev/oss/oss_hdaudio0/mix0, Legacy device /dev/mixer0
    Priority: 10
    Caps: 
    Device handle: PCI009f1025-0000:00:14.2-mx01
    Device priority: 10


Audio devices
HD Audio play front               /dev/oss/oss_hdaudio0/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Out engine  1: 0/HD Audio play front
                     Available for use 
      Engine      2: 10/HD Audio play front (vmix)
                     Available for use 
      Engine      3: 11/HD Audio play front (vmix)
                     Available for use 
      Engine      4: 12/HD Audio play front (vmix)
                     Available for use 
      Engine      5: 13/HD Audio play front (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au01
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 8
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play rear                /dev/oss/oss_hdaudio0/pcm1  (device index 1)
    Legacy device /dev/dsp1
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 1/HD Audio play rear
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au02
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play center/LFE          /dev/oss/oss_hdaudio0/pcm2  (device index 2)
    Legacy device /dev/dsp2
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 2/HD Audio play center/LFE
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au03
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play side                /dev/oss/oss_hdaudio0/pcm3  (device index 3)
    Legacy device /dev/dsp3
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 3/HD Audio play side
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au04
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm4                /dev/oss/oss_hdaudio0/pcm4  (device index 4)
    Legacy device /dev/dsp4
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 4/HD Audio play pcm4
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au05
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play modem-out           /dev/oss/oss_hdaudio0/pcm5  (device index 5)
    Legacy device /dev/dsp5
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 5/HD Audio play modem-out
                     Available for use 
    Input formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Output formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au06
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 16000 - 48000 (16000,48000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play spdif-out           /dev/oss/oss_hdaudio0/spdout0  (device index 6)
    Legacy device /dev/dsp6
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 6/HD Audio play spdif-out
                     Available for use 
    Input formats (0x00001410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au07
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin0  (device index 7)
    Legacy device /dev/dsp7
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      In engine   1: 7/HD Audio rec mix
                     Available for use 
      Engine      2: 10/HD Audio play front (vmix)
                     Available for use 
      Engine      3: 11/HD Audio play front (vmix)
                     Available for use 
      Engine      4: 12/HD Audio play front (vmix)
                     Available for use 
      Engine      5: 13/HD Audio play front (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au08
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin1  (device index 8)
    Legacy device /dev/dsp8
    Caps: TRIGGER MMAP 
    Modes: INPUT  
      In engine   1: 8/HD Audio rec mix
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au09
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec modem-out            /dev/oss/oss_hdaudio0/pcmin2  (device index 9)
    Legacy device /dev/dsp9
    Caps: TRIGGER MMAP 
    Modes: INPUT  
      In engine   1: 9/HD Audio rec modem-out
                     Available for use 
    Input formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Output formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au10
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 16000 - 48000 (16000,48000)
    HW Type: Not indicated.
    Minimum latency: Not indicated


Nodes
  /dev/dsp -> /dev/oss/oss_sbxfi0/pcm0
  /dev/dsp_in -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_out -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_ac3 -> /dev/oss/oss_hdaudio0/spdout0
  /dev/dsp_mmap -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_multich -> /dev/oss/oss_hdaudio0/pcm0
```

Edit - added code tags - please use them for long outputs like this - [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by VertexPusher on 2010-02-05
> **karmic-koala said:**
> Is there an alternative to ALSA?
Not really, but there's an alternative to PulseAudio + ALSA, which is what you were using before you installed OSS. One of the more obscure "features" of PulseAudio is that it adjusts your ALSA mixer settings in ways you don't expect. And the new Gnome mixer panel is unable to modify these settings because all it can do is control PulseAudio's own (software) volume level. Of course, even if you set that to maximum, it will never exceed the hardware volume level of the sound card which is only accessible through ALSA.

To many users this isn't obvious. So they blame ALSA, install OSS ... and end up with an even greater mess.

You probably want to revert from OSS to ALSA and get rid of PulseAudio. Fortunately the latter is quite easy to do:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse
```

---

### Post by Yellow Pasque on 2010-02-05
You probably just need to set your applications to use OSS.
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)

Also, if you get apps working, then subscribe to this PPA to get your GNOME audio functionality back: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

### Post by karmic-koala on 2010-02-05
> **VertexPusher said:**
> 
You probably want to revert from OSS to ALSA and get rid of PulseAudio. Fortunately the latter is quite easy to do:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse
```

Very well, but after removing pulseaudio I have no way to increase or decrease volume without calling gnome-alsamixer or alsamixer. Keyboard keys ( Fn + vol ) don't work and there's no icon in the panel tray to change volume. Did I miss something here?

---

### Post by Yellow Pasque on 2010-02-05
> **karmic-koala said:**
> Did I miss something here?
[https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

### Post by VertexPusher on 2010-02-05
> **karmic-koala said:**
> Keyboard keys ( Fn + vol ) don't work and there's no icon in the panel tray to change volume.
You can put the gnome-alsamixer icon into the tray area, but for the Fn keys to work you need the old Gnome mixer applet from the repository mentioned in Temüjin's post.

---

### Post by markbuntu on 2010-02-05
If your recordings are low level and noisy there is usually a mic-boost switch in the alsa mixer which will fix that problem. I defintely reccomend the gnome-alsamixer for controlling alsa drivers.

---

### Post by karmic-koala on 2010-02-08
I've already tried fumbling around with recording level and boost level in alsamixer, no joy there.

---

### Post by kronictokr on 2010-02-08
if your comited to fixing it with everything working. i really suggest you back up your data, do a fresh install and update, and use the following.
[http://ubuntuforums.org/showthread.php?t=1395089](http://ubuntuforums.org/showthread.php?t=1395089)

i had previously tried the method adding packages and removing pulse, although it was faster. i lost some of the functionalities of the system. such as volume control. i have since changed and updated it, keeps pulse, as well as the function keys, and i get sound from everything. best sound ive got off my old speakers for a while ;)

---

