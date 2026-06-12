---
title: "OSS v4 sound problems with PortAudio (revisited)"
date: 2009-12-07
forum: Multimedia Software
---

### Post by Artifakt on 2009-12-07
The problem is that no PortAudio apps will recognize any OSS(v4.2) devices. For example audacity shows OSS as a host sound system, but no devices attached to it. I got sound working through alsa emulation, but that is not the solution I was looking for. I was also lacking mic support for both programs. I got both of the programs mentioned above working in my last install, but after doing a clean install (Ubuntu 9.10). Please help me, I'm fed up with booting to Windows just to use audacity. The mic+audio works fine with Wine, nothing else I've tried so far has worked. 

Ossinfo:
```
Version info: OSS 4.2 (b 2001/200910230633) (0x00040100) TRIAL
Platform: Linux/x86_64 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 (anton-desktop)

Number of audio devices:	4
Number of audio engines:	8
Number of MIDI devices:		0
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: oss_cmpci0 CMedia CM8738 interrupts=318046 (659383)
 2: oss_usb0 USB audio core services
 3: usb08bb2902-0 USB sound device
 4: usb08bb2902-1 USB sound device
 5: usb08bb2902-2 USB sound device

MIDI devices (/dev/midi*)

Mixer devices
 0: CMedia CMPCI (Mixer 0 of device object 1)
 1: USB sound device (Mixer 0 of device object 3)

Audio devices
CMedia CM8768 (rev 68)            /dev/oss/oss_cmpci0/pcm0  (device index 0)
CMedia CM8768 (playback only)     /dev/oss/oss_cmpci0/pcm1  (device index 1)
USB sound device play             /dev/oss/usb08bb2902-1/pcm0  (device index 2)
USB sound device rec              /dev/oss/usb08bb2902-2/pcmin0  (device index 3)

Nodes
  /dev/dsp -> /dev/oss/oss_cmpci0/pcm0
  /dev/dsp_in -> /dev/oss/oss_cmpci0/pcm0
  /dev/dsp_out -> /dev/oss/oss_cmpci0/pcm0
  /dev/dsp_ac3 -> /dev/oss/oss_cmpci0/pcm0
  /dev/dsp_mmap -> /dev/oss/oss_cmpci0/pcm0
  /dev/dsp_multich -> /dev/oss/oss_cmpci0/pcm0
  /dev/dsp_spdifout -> /dev/oss/oss_cmpci0/pcm0
  /dev/dsp_spdifin -> /dev/oss/oss_cmpci0/pcm0

```
Ossinfo -v3:
```
Version info: OSS 4.2 (b 2001/200910230633) (0x00040100) TRIAL
Platform: Linux/x86_64 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 (anton-desktop)

Number of audio devices:	4
Number of audio engines:	8
Number of MIDI devices:		0
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: oss_cmpci0 CMedia CM8738 interrupts=318046 (663106)
 2: oss_usb0 USB audio core services
 3: usb08bb2902-0 USB sound device
 4: usb08bb2902-1 USB sound device
 5: usb08bb2902-2 USB sound device

MIDI devices (/dev/midi*)

Mixer devices
 0: CMedia CMPCI (Mixer 0 of device object 1)
    Device file /dev/oss/oss_cmpci0/mix0, Legacy device /dev/mixer0
    Priority: 1
    Caps: 
    Device handle: PCI3741584d-0000:04:06.0-mx01
    Device priority: 1

 1: USB sound device (Mixer 0 of device object 3)
    Device file /dev/oss/usb08bb2902-0/mix0, Legacy device /dev/mixer1
    Priority: 0
    Caps: 
    Device handle: USB-usb08bb2902-0-mx01
    Device priority: 0


Audio devices
CMedia CM8768 (rev 68)            /dev/oss/oss_cmpci0/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Engine      1: 0/CMedia CM8768 (rev 68)
                     Available for use 
      Engine      2: 1/CMedia CM8768 (rev 68) (vmix)
                     Available for use 
      Engine      3: 2/CMedia CM8768 (rev 68) (vmix)
                     Available for use 
      Engine      4: 3/CMedia CM8768 (rev 68) (vmix)
                     Available for use 
      Engine      5: 4/CMedia CM8768 (rev 68) (vmix)
                     Available for use 
    Input formats (0x00000418):
      AFMT_U8		- 8 bit unsigned
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
    Output formats (0x00000418):
      AFMT_U8		- 8 bit unsigned
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
    Device handle: PCI3741584d-0000:04:06.0-au01
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 8
    Native sample rates (min - max): 5000 - 48000
    HW Type: ANALOG_OUT ANALOG_IN DIGITAL_OUT DIGITAL_IN     Minimum latency: Not indicated

CMedia CM8768 (playback only)     /dev/oss/oss_cmpci0/pcm1  (device index 1)
    Legacy device /dev/dsp1
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 5/CMedia CM8768 (playback only)
                     Available for use 
    Input formats (0x00000418):
      AFMT_U8		- 8 bit unsigned
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
    Output formats (0x00000418):
      AFMT_U8		- 8 bit unsigned
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
    Device handle: PCI3741584d-0000:04:06.0-au02
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 8
    Native sample rates (min - max): 5000 - 48000
    HW Type: ANALOG_OUT ANALOG_IN DIGITAL_OUT DIGITAL_IN     Minimum latency: Not indicated

USB sound device play             /dev/oss/usb08bb2902-1/pcm0  (device index 2)
    Legacy device /dev/dsp2
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 6/USB sound device play
                     Available for use 
    Input formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Output formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Device handle: USB-usb08bb2902-1-au01
    Related mixer dev: 1
    Sample rate source: 6
    Preferred channel configuration: STEREO
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 32000 - 48000 (32000,44100,48000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

USB sound device rec              /dev/oss/usb08bb2902-2/pcmin0  (device index 3)
    Legacy device /dev/dsp3
    Caps: TRIGGER MMAP 
    Modes: INPUT  
      In engine   1: 7/USB sound device rec
                     Available for use 
    Input formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Output formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Device handle: USB-usb08bb2902-2-au01
    Related mixer dev: 1
    Sample rate source: 6
    Preferred channel configuration: MONO
    Supported number of channels (min - max): 1 - 1
    Native sample rates (min - max): 48000 - 48000 (48000)
    HW Type: Not indicated.
    Minimum latency: Not indicated


Nodes
  /dev/dsp -> /dev/oss/oss_cmpci0/pcm0
  /dev/dsp_in -> /dev/oss/oss_cmpci0/pcm0
  /dev/dsp_out -> /dev/oss/oss_cmpci0/pcm0
  /dev/dsp_ac3 -> /dev/oss/oss_cmpci0/pcm0
  /dev/dsp_mmap -> /dev/oss/oss_cmpci0/pcm0
  /dev/dsp_multich -> /dev/oss/oss_cmpci0/pcm0
  /dev/dsp_spdifout -> /dev/oss/oss_cmpci0/pcm0
  /dev/dsp_spdifin -> /dev/oss/oss_cmpci0/pcm0
```

System specs:
Ubuntu 9.10/ OSS4 from mercurial source
Auzentech X-Plosion 7.1 DTS Connect (SPDIF)
(the second device listed in the ossinfo outputs above is my amplifier (Pioneer VSX-AX5) connected through USB, which BTW doesn't work (works fine in Windows))

---

### Post by Artifakt on 2009-12-08
ttt, please help me!

---

