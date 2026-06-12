---
title: "alsa being weird"
date: 2009-12-14
forum: Multimedia Software
---

### Post by Sin@Sin-Sacrifice on 2009-12-14
So I just installed an 8.10 box and of course there's no sound. I go straight to the comprehensive sound solutions guide and skip the parts I have memorized (isn't that sad?) to move on to trying to get this stuff working. Using alc888 chipset which worked on everything prior. Weird thing though. In tty2 terminal the output of aplay -l is ```
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
```
But in KDE it's ```
aplay: device_list:215: no soundcards found...
```
Not having a very good time with this. lspci | grep audio gives me null. Opening alsamixer tells me ```
alsamixer: function snd_ctl_open failed for default: No such device
``` and kmix is empty. I'm in every group known to man... uhh... PC. I'm at a loss...

---

### Post by Sin@Sin-Sacrifice on 2009-12-15
Bump...

---

### Post by Ulysses361 on 2009-12-15
Please send us the output from step 3 and step 4 from this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Please also specify the exact model and make of your pc (if known)

---

### Post by Sin@Sin-Sacrifice on 2009-12-15
The make is my own (SinINC) and I named her Purgatory as the model. It's an XFX 750a SLI board (GeForce 8200 north bridge and 750a South), AMD Phenom 9500 CPU, 2 WD 500 GB HDDs, wmp300n wlan, Sony generic DVD-RW, Corsair (forget the model) 4GB RAM, Ultra 550w PSU, Ultra something or other Full tower, stole the 15-in-1 card reader from my mom's m8000n, WinTV hvr-1600 tv tuner also form the m8000n, and some "turbocharged" emblems from a Cobalt SS. Just come to find that I can play audio in vlc from a tty just not in KDE. I didn't think X had anything to do with audio... anyway here's the output of the script in section 3
```
name=sin&type=33&description=/tmp/alsa-info.txt&expiry=&s=Submit+Post&content=
!!################################
!!ALSA Information Script v 0.4.58
!!################################

!!Script ran on: Tue Dec 15 18:10:00 UTC 2009


!!Linux Distribution
!!------------------

DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 8.10"


!!DMI Information
!!---------------

Manufacturer:      To Be Filled By O.E.M.
Product Name:      To Be Filled By O.E.M.


!!Kernel Information
!!------------------

Kernel release:    2.6.29.4
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.18a
Library version:    1.0.17a
Utilities version:  1.0.17


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

aRts:
      Installed - Yes (/opt/kde3/bin/artsd)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf3f78000 irq 21


!!PCI Soundcards installed in the system
!!--------------------------------------

00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
01:08.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:07.0 0403: 10de:0774 (rev a1)
	Subsystem: 10de:cb84


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : 0
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC888
Address: 0
Vendor Id: 0x10ec0888
Subsystem Id: 0x10ec0000
Revision Id: 0x100001
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=5, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x13 0x13]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01014410: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01011412: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01016411: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01012414: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19c40: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19c50: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181344f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x4, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02214c20: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x593301f0: [N/A] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4005e601: [N/A] Line Out at Ext N/A
    Conn = Optical, Color = White
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x014b5130: [Jack] SPDIF Out at Ext Rear
    Conn = Comb, Color = Red
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x01c47160: [Jack] SPDIF In at Ext Rear
    Conn = RCA, Color = Yellow
    DefAssociation = 0x6, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
  Processing Coefficient: 0x6000
  Coefficient Index: 0x09
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x25 0x0b
Codec: Nvidia MCP78 HDMI
Address: 3
Vendor Id: 0x10de0002
Subsystem Id: 0x10de0101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x18560110: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x07 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560121: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x08 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x09 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560122: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x2
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x08
Node 0x0a [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0b [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560123: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x3
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0a
Node 0x0c [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0d [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560124: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x4
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0c
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 12 Dec 15 12:46 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 11 Dec 15 12:46 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 10 Dec 15 12:46 /dev/snd/hwC0D3
crw-rw----+ 1 root audio 116,  9 Dec 15 12:46 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  8 Dec 15 12:46 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  7 Dec 15 12:46 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116,  6 Dec 15 12:46 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  5 Dec 15 12:46 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116,  4 Dec 15 12:46 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  3 Dec 15 12:46 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Dec 15 12:46 /dev/snd/timer


!!ALSA configuration files
!!------------------------

!!User specific config file (~/.asoundrc)

# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/sin/.asoundrc.asoundconf>



!!asoundconf-generated config file

# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card alc888
defaults.ctl.card alc888
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format "unchanged"
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.pcm.file_format "raw"
defaults.pcm.file_truncate true
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:215: no soundcards found...

ARECORD

arecord: device_list:215: no soundcards found...

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [NVidia]

Invalid card number.
Usage: amixer <options> [command]

Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially

Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]

Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially

Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
ipv6
ppdev
video
output
sbs
sbshc
cpufreq_conservative
cpufreq_performance
cpufreq_stats
cpufreq_powersave
cpufreq_ondemand
freq_table
iptable_filter
ip_tables
x_tables
parport_pc
lp
parport
snd_hda_codec_nvhdmi
snd_hda_codec_realtek
mxl5005s
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_pcm
s5h1409
snd_mixer_oss
tuner_simple
tuner_types
snd_seq_dummy
tda9887
tda8290
snd_seq_oss
snd_seq_midi
snd_rawmidi
cs5345
snd_seq_midi_event
tuner
snd_seq
nvidia
cx18
wmi
dvb_core
agpgart
rndis_host
cdc_ether
usbnet
rtc_cmos
rtc_core
rtc_lib
cx2341x
v4l2_common
videodev
v4l1_compat
tveeprom
snd_timer
snd_seq_device
serio_raw
snd
psmouse
evdev
soundcore
shpchp
snd_page_alloc
sky2
sg
ata_generic
pata_acpi
pata_amd
fuse


!!ALSA/HDA dmesg
!!------------------

input: ImPS/2 Generic Wheel Mouse as /class/input/input4
HDA Intel 0000:00:07.0: power state changed by ACPI to D0
ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
HDA Intel 0000:00:07.0: setting latency timer to 64
MXL5005S: Attached at address 0x63
--
usb-storage: device scan complete
hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
scsi 9:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
```

And in 4 we have cat /proc/asound/cards: ```
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf3f78000 irq 21
```

```
sudo aptitude install paman gnome-alsamixer alsa-utils flashplugin-nonfree-extrasound
[sudo] password for sin:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  flashplugin-nonfree-extrasound gnome-alsamixer libgconfmm-2.6-1c2{a}
  libglademm-2.4-1c2a{a} libpulse-mainloop-glib0{a} padevchooser{a} paman
  paprefs{a} pavucontrol{a} pavumeter{a} pulseaudio-module-gconf{a}
  pulseaudio-module-zeroconf{a}
0 packages upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 395kB of archives. After unpacking 2572kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.offensive-security.com pwnsauce/multiverse flashplugin-nonfree-extrasound 0.0.svn2431-3 [8160B]
Get:2 http://archive.offensive-security.com pwnsauce/universe gnome-alsamixer 0.9.7~cvs.20060916.ds.1-1 [55.6kB]
Get:3 http://archive.offensive-security.com pwnsauce/main libgconfmm-2.6-1c2 2.24.0-0ubuntu1 [31.1kB]
Get:4 http://archive.offensive-security.com pwnsauce/main libglademm-2.4-1c2a 2.6.6-1 [21.1kB]
Get:5 http://archive.offensive-security.com pwnsauce/main libpulse-mainloop-glib0 0.9.10-2ubuntu9.4 [23.9kB]
Get:6 http://archive.offensive-security.com pwnsauce/universe paman 0.9.4-1ubuntu1 [95.3kB]
Get:7 http://archive.offensive-security.com pwnsauce/main pulseaudio-module-gconf 0.9.10-2ubuntu9.4 [10.3kB]
Get:8 http://archive.offensive-security.com pwnsauce/main pulseaudio-module-zeroconf 0.9.10-2ubuntu9.4 [17.8kB]
Get:9 http://archive.offensive-security.com pwnsauce/universe paprefs 0.9.6-2ubuntu1 [31.6kB]
Get:10 http://archive.offensive-security.com pwnsauce/universe pavucontrol 0.9.6+svn20080426-1ubuntu1 [51.1kB]
Get:11 http://archive.offensive-security.com pwnsauce/universe pavumeter 0.9.3-1ubuntu1 [29.2kB]
Get:12 http://archive.offensive-security.com pwnsauce/universe padevchooser 0.9.3-2ubuntu3 [20.2kB]
Fetched 395kB in 4s (83.0kB/s)
Selecting previously deselected package flashplugin-nonfree-extrasound.
(Reading database ... 250350 files and directories currently installed.)
Unpacking flashplugin-nonfree-extrasound (from .../flashplugin-nonfree-extrasound_0.0.svn2431-3_i386.deb) ...
Selecting previously deselected package gnome-alsamixer.
Unpacking gnome-alsamixer (from .../gnome-alsamixer_0.9.7~cvs.20060916.ds.1-1_i386.deb) ...
Selecting previously deselected package libgconfmm-2.6-1c2.
Unpacking libgconfmm-2.6-1c2 (from .../libgconfmm-2.6-1c2_2.24.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libglademm-2.4-1c2a.
Unpacking libglademm-2.4-1c2a (from .../libglademm-2.4-1c2a_2.6.6-1_i386.deb) ...
Selecting previously deselected package libpulse-mainloop-glib0.
Unpacking libpulse-mainloop-glib0 (from .../libpulse-mainloop-glib0_0.9.10-2ubuntu9.4_i386.deb) ...
Selecting previously deselected package paman.
Unpacking paman (from .../paman_0.9.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package pulseaudio-module-gconf.
Unpacking pulseaudio-module-gconf (from .../pulseaudio-module-gconf_0.9.10-2ubuntu9.4_i386.deb) ...
Selecting previously deselected package pulseaudio-module-zeroconf.
Unpacking pulseaudio-module-zeroconf (from .../pulseaudio-module-zeroconf_0.9.10-2ubuntu9.4_i386.deb) ...
Selecting previously deselected package paprefs.
Unpacking paprefs (from .../paprefs_0.9.6-2ubuntu1_i386.deb) ...
Selecting previously deselected package pavucontrol.
Unpacking pavucontrol (from .../pavucontrol_0.9.6+svn20080426-1ubuntu1_i386.deb) ...
Selecting previously deselected package pavumeter.
Unpacking pavumeter (from .../pavumeter_0.9.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package padevchooser.
Unpacking padevchooser (from .../padevchooser_0.9.3-2ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up flashplugin-nonfree-extrasound (0.0.svn2431-3) ...
Setting up gnome-alsamixer (0.9.7~cvs.20060916.ds.1-1) ...

Setting up libgconfmm-2.6-1c2 (2.24.0-0ubuntu1) ...

Setting up libglademm-2.4-1c2a (2.6.6-1) ...

Setting up libpulse-mainloop-glib0 (0.9.10-2ubuntu9.4) ...

Setting up paman (0.9.4-1ubuntu1) ...

Setting up pulseaudio-module-gconf (0.9.10-2ubuntu9.4) ...
Setting up pulseaudio-module-zeroconf (0.9.10-2ubuntu9.4) ...
Setting up paprefs (0.9.6-2ubuntu1) ...

Setting up pavucontrol (0.9.6+svn20080426-1ubuntu1) ...

Setting up pavumeter (0.9.3-1ubuntu1) ...

Setting up padevchooser (0.9.3-2ubuntu3) ...

Processing triggers for menu ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
localepurge: Disk space freed in /usr/share/locale: 144K
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
```

aplay -l: ```
aplay: device_list:215: no soundcards found...
```

sudo lshw -C sound: ```
  *-multimedia
       description: Audio device
       product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
  *-multimedia
       description: Multimedia video controller
       product: CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vpd pm bus_master cap_list
       configuration: driver=cx18 latency=64 maxlatency=200 mingnt=2 module=cx18
```

ls -lart /dev/snd: ```
total 0
crw-rw----+  1 root audio 116,  2 2009-12-15 12:46 timer
crw-rw----+  1 root audio 116,  3 2009-12-15 12:46 seq
crw-rw----+  1 root audio 116,  4 2009-12-15 12:46 pcmC0D3p
crw-rw----+  1 root audio 116,  5 2009-12-15 12:46 pcmC0D2c
crw-rw----+  1 root audio 116,  6 2009-12-15 12:46 pcmC0D1p
crw-rw----+  1 root audio 116,  7 2009-12-15 12:46 pcmC0D1c
crw-rw----+  1 root audio 116,  8 2009-12-15 12:46 pcmC0D0p
crw-rw----+  1 root audio 116,  9 2009-12-15 12:46 pcmC0D0c
crw-rw----+  1 root audio 116, 12 2009-12-15 12:46 controlC0
crw-rw----+  1 root audio 116, 10 2009-12-15 12:46 hwC0D3
crw-rw----+  1 root audio 116, 11 2009-12-15 12:46 hwC0D0
drwxr-xr-x   2 root root      260 2009-12-15 12:46 .
drwxr-xr-x  16 root root    14740 2009-12-15 13:27 ..
```

cat /dev/sndstat: ```
Sound Driver:3.8.1a-980706 (ALSA v1.0.18a emulation code)
Kernel: Linux hellonearth 2.6.29.4 #1 SMP Thu Jun 18 10:57:32 EDT 2009 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
HDA NVidia at 0xf3f78000 irq 21

Audio devices:
0: ALC888 Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Nvidia MCP78 HDMI
```

lspci -nn: ```
00:00.0 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0754] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation nForce 750a LPC Bridge [10de:075d] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP78S [GeForce 8200] SMBus [10de:0752] (rev a1)
00:01.2 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0751] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP78S [GeForce 8200] Co-Processor [10de:0753] (rev a2)
00:01.4 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0568] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077b] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077c] (rev a1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077d] (rev a1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077e] (rev a1)
00:06.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] IDE [10de:0759] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio [10de:0774] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:075a] (rev a1)
00:09.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) [10de:0ad0] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0569] (rev a1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0778] (rev a1)
00:12.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:075b] (rev a1)
00:13.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
00:14.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]
01:07.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)
01:08.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder [14f1:5b7a]
02:00.0 VGA compatible controller [0300]: nVidia Corporation C77 [nForce 750a SLI] [10de:084d] (rev a2)
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 14)
```

sudo which alsactl: ```
/sbin/alsactl
```

sudo fuser -v /dev/dsp /dev/snd/*: Null

dpkg -S bin/slmodemd: ```
dpkg: *bin/slmodemd* not found.
```

sudo /etc/init.d/sl-modem-daemon status: ```
sudo: /etc/init.d/sl-modem-daemon: command not found
```

lsmod | grep snd : ```
snd_hda_codec_nvhdmi     2764  1
snd_hda_codec_realtek   189712  1
snd_hda_intel          24200  0
snd_hda_codec          53932  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6736  1 snd_hda_codec
snd_pcm_oss            37664  0
snd_pcm                68144  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_mixer_oss          14156  1 snd_pcm_oss
snd_seq_dummy           2416  0
snd_seq_oss            29728  0
snd_seq_midi            5952  0
snd_rawmidi            19104  1 snd_seq_midi
snd_seq_midi_event      5964  2 snd_seq_oss,snd_seq_midi
snd_seq                47536  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19124  2 snd_pcm,snd_seq
snd_seq_device          6008  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    50276  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               5856  1 snd
snd_page_alloc          7924  2 snd_hda_intel,snd_pcm
```

The output from aplay -l in any tty is listed in my OP so confused. I can start a playlist by hitting ctrl+alt+F2 and vlc ./siklist.m3u then switch back with ctrl+alt+F7 and it keeps playing but this is becoming real bothersome. Thanks for the help man...

---

### Post by Ulysses361 on 2009-12-15
The reason why you are getting the error

"aplay: device_list:215: no soundcards found..."

is probably due to the following ALSA configuration issue:

!!ALSA Version
!!------------

Driver version:     1.0.18a
Library version:    1.0.17a
Utilities version:  1.0.17

As you can see in your ALSA output, the ALSA driver, library and utilities versions are NOT the same.

I recommend upgrading ALSA to version 1.0.21, using this procedure:

[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

After upgrading ALSA, reboot and retest sound. If it does not help, please resend the output from step 3 and step 4 from this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by Sin@Sin-Sacrifice on 2009-12-16
Well... I actually found the problem. It was permissions. I actually plan on compiling the newest drivers here soon but for now I have it working. Thanks for the help.

---

### Post by Fitch on 2009-12-21
Permissions?

I get a constant hiss. I don't know how to tell the computer that the PCTV Rave tuner is a TDA9887.
I did a sudo chown -R [blah]:[blah] /etc if that's what you mean.
still get hiss.
I have version 1.0.20
If I do the upgrade, stopping alsa comes up:
sudo: /etc/sudoers is owned by uid 1000, should be 0
Segmentation fault

My aplay -l gives:
**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

It still hisses

---

