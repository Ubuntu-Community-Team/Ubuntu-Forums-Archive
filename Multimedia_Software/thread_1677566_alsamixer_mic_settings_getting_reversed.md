---
title: "alsamixer mic settings getting reversed"
date: 2011-01-28
forum: Multimedia Software
---

### Post by badnaam on 2011-01-28
I installed linux conexant drivers and uninstall alsa backports to get  my internal laptop mic to work. I tried several other things which didn't resolve the situation, this was the solution that is working..almost.

One thing I notice is that I need to set the input source to mic_f in the capture settings inside alsa mixer and boost the mic to 30db. however, for some reason this settings keeps getting reset to dmic_j, not sure how that is happening (no reboots, no fiddling with sound preferences etc). The only thing I actually use the mic for is google voice.

Any ideas?

Thanks

---

### Post by badnaam on 2011-01-28
OK, That's not all, now it seems my output is jacked  too. My headphones don't work when plugged in my port A jack in somehow being set to line-in, even if I set it to headphones, the sound is very strange and ..thin.

I have wasted 4 days trying to get this sound working..it's either the mic or the output. I have to say, I want to be a believer in linux/ubuntu..but it seems quite a lot of effort (debug, run commands, install driver, read long long long long long long bug reports..with no definitive solution)..windows with all it's crappiness..still seems better sometimes. I know some of you will say..just go back to windows..but then that does not solve this problem.

---

### Post by lidex on 2011-01-29
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by badnaam on 2011-01-29
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Here is the output. Thanks for your help.



upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Jan 29 18:08:20 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      HP G60 Notebook PC
Product Version:   0392120000200C10000020000


!!Kernel Information
!!------------------

Kernel release:    2.6.32-27-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd4700000 irq 30


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 103c:360b


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: power_save=10 power_save_controller=N
snd-hda-intel: position_fix=0 enable=yes


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1
	model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0
	power_save : 10
	power_save_controller : N
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Conexant CX20583 (Pebble 56-LQFP)
Address: 0
Function Id: 0x2
Vendor Id: 0x14f15067
Subsystem Id: 0x103c360b
Revision Id: 0x100301
Modem Function Group: 0x2
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
  BIOS Profile: 1
Node 0x10 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x4a 0x4a]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x3c 0x3c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x13 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0f, mute=0
  Amp-Out vals:  [0x00]
Node 0x14 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x50 0x50] [0x80 0x80] [0x50 0x50] [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
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
  Power states:  D0 D1 D2 D3 D3cold
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
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x17 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a 0x1b 0x1d 0x1e*
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x042140f0: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Green
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=37, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1a [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00001324: IN Detect
    Vref caps: HIZ 50 80
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=38, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00011334: IN OUT EAPD Detect
    Vref caps: HIZ 50 80
  EAPD 0x2: EAPD
  Pin Default 0x04a190f0: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=39, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1c [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=3a, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=3b, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1e [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x95a701f0: [Fixed] Mic at Int Top
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=3c, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x921701f0: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=3d, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="Conexant Digital Audio", type="SPDIF", device=1
  Converter: stream=5, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x22 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=3e, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
Node 0x23 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x04, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x24 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11
Node 0x25 [Vendor Defined Widget] wcaps 0xf00000: Mono
Codec: Intel G45 DEVCTG
Address: 2
Function Id: 0x1
Vendor Id: 0x80862802
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6211: 8-Channels Digital
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Device: name="INTEL HDMI 0", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
Node 0x03 [Pin Complex] wcaps 0x40739d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=03, enabled=1
  Connection: 1
     0x02
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  0 Jan 27 20:54 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  4 Jan 27 20:54 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  6 Jan 27 20:54 /dev/snd/hwC0D2
crw-rw----+ 1 root audio 116, 24 Jan 28 21:57 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 16 Jan 29 09:39 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 17 Jan 27 21:11 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 19 Jan 27 21:11 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116, 30 Jan 27 20:54 /dev/snd/pcmC0D6c
crw-rw----+ 1 root audio 116, 22 Jan 27 20:54 /dev/snd/pcmC0D6p
crw-rw----+ 1 root audio 116,  1 Jan 27 20:54 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jan 27 20:54 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jan 27 20:54 .
drwxr-xr-x 3 root root 280 Jan 27 20:54 ..
lrwxrwxrwx 1 root root  12 Jan 27 20:54 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital Audio [Conexant Digital Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Conexant HSF Modem [Conexant HSF Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Conexant HSF Modem [Conexant HSF Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xd4700000 irq 30'
  Mixer name	: 'Intel G45 DEVCTG'
  Components	: 'HDA:14f15067,103c360b,00100301 HDA:80862802,80860101,00100000'
  Controls      : 24
  Simple ctrls  : 16
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '0dB'
Simple mixer control 'Automute',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'DMIC1 Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '12dB' '24dB' '36dB' '48dB'
  Item0: '0dB'
Simple mixer control 'Input',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [on]
  Front Right: Capture 80 [100%] [6.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic_F' 'LineIn_F' 'Mic_B' 'LineIn_B' 'Mic_C' 'LineIn_C' 'LineIn_E' 'DMIC_J'
  Item0: 'DMIC_J'
Simple mixer control 'PortA Jack Mode',0
  Capabilities: enum
  Items: 'Off' 'Line out' 'Headphone out'
  Item0: 'Headphone out'
Simple mixer control 'PortB Jack Mode',0
  Capabilities: enum
  Items: 'Off' 'Mic 50pc bias' 'Mic 80pc bias' 'Line in'
  Item0: 'Mic 80pc bias'
Simple mixer control 'PortC Jack Mode',0
  Capabilities: enum
  Items: 'Off' 'Mic 50pc bias' 'Mic 80pc bias' 'Line in' 'Line out' 'Headphone out'
  Item0: 'Mic 80pc bias'
Simple mixer control 'PortD Jack Mode',0
  Capabilities: enum
  Items: 'Off' 'Line out' 'Headphone out'
  Item0: 'Off'
Simple mixer control 'PortE Jack Mode',0
  Capabilities: enum
  Items: 'Off' 'Line in' 'Line out' 'Headphone out'
  Item0: 'Line in'
Simple mixer control 'PortG Jack Mode',0
  Capabilities: enum
  Items: 'Off' 'Line out' 'Headphone out'
  Item0: 'Line out'


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 74'
		comment.dbmin -7400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 74
		value.1 74
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Automute Switch'
		value false
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic_F
		comment.item.1 LineIn_F
		comment.item.2 Mic_B
		comment.item.3 LineIn_B
		comment.item.4 Mic_C
		comment.item.5 LineIn_C
		comment.item.6 LineIn_E
		comment.item.7 DMIC_J
		iface MIXER
		name 'Input Source Capture Route'
		value DMIC_J
	}
	control.5 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '0dB'
		comment.item.1 '10dB'
		comment.item.2 '20dB'
		comment.item.3 '30dB'
		comment.item.4 '40dB'
		iface MIXER
		name 'Analog Mic Boost Capture Enum'
		value '0dB'
	}
	control.6 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '0dB'
		comment.item.1 '12dB'
		comment.item.2 '24dB'
		comment.item.3 '36dB'
		comment.item.4 '48dB'
		iface MIXER
		name 'DMIC1 Mic Boost Capture Enum'
		value '0dB'
	}
	control.7 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Off
		comment.item.1 'Mic 50pc bias'
		comment.item.2 'Mic 80pc bias'
		comment.item.3 'Line in'
		iface MIXER
		name 'PortB Jack Mode'
		value 'Mic 80pc bias'
	}
	control.8 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Off
		comment.item.1 'Mic 50pc bias'
		comment.item.2 'Mic 80pc bias'
		comment.item.3 'Line in'
		comment.item.4 'Line out'
		comment.item.5 'Headphone out'
		iface MIXER
		name 'PortC Jack Mode'
		value 'Mic 80pc bias'
	}
	control.9 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Off
		comment.item.1 'Line in'
		comment.item.2 'Line out'
		comment.item.3 'Headphone out'
		iface MIXER
		name 'PortE Jack Mode'
		value 'Line in'
	}
	control.10 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Off
		comment.item.1 'Line out'
		comment.item.2 'Headphone out'
		iface MIXER
		name 'PortA Jack Mode'
		value 'Headphone out'
	}
	control.11 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Off
		comment.item.1 'Line out'
		comment.item.2 'Headphone out'
		iface MIXER
		name 'PortG Jack Mode'
		value 'Line out'
	}
	control.12 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Off
		comment.item.1 'Line out'
		comment.item.2 'Headphone out'
		iface MIXER
		name 'PortD Jack Mode'
		value Off
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 80'
		comment.dbmin -7400
		comment.dbmax 600
		iface MIXER
		name 'Input Capture Volume'
		value.0 80
		value.1 80
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Input Capture Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.16 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.17 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.20 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 1
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.21 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 1
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.22 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		index 1
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.23 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		index 1
		value true
	}
	control.24 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
cryptd
aes_x86_64
aes_generic
binfmt_misc
vmnet
ppdev
parport_pc
vmblock
vsock
vmci
vmmon
ipt_REJECT
xt_multiport
xt_limit
xt_tcpudp
ipt_addrtype
xt_state
ip6table_filter
ip6_tables
nf_nat_irc
snd_hda_codec_intelhdmi
nf_conntrack_irc
snd_hda_codec_conexant
nf_nat_ftp
fbcon
snd_hda_intel
tileblit
snd_hda_codec
nf_nat
font
snd_hwdep
bitblit
snd_pcm_oss
snd_mixer_oss
nf_conntrack_ipv4
nf_defrag_ipv4
softcursor
snd_pcm
vga16fb
snd_seq_dummy
snd_seq_oss
vgastate
snd_seq_midi
joydev
nf_conntrack_ftp
snd_rawmidi
snd_seq_midi_event
nf_conntrack
arc4
snd_seq
i915
snd_timer
iptable_filter
snd_seq_device
ip_tables
drm_kms_helper
drm
i2c_algo_bit
video
x_tables
psmouse
output
uvcvideo
snd
videodev
soundcore
snd_page_alloc
intel_agp
serio_raw
iwlagn
iwlcore
mac80211
v4l1_compat
led_class
v4l2_compat_ioctl32
cfg80211
lp
parport
ahci
r8169
mii


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x19 0x042140f0
0x1a 0x400001f0
0x1b 0x04a190f0
0x1c 0x400001f0
0x1d 0x400001f0
0x1e 0x95a701f0
0x1f 0x921701f0
0x20 0x400001f0
0x22 0x400001f0
0x23 0x400001f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D2/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D2/driver_pin_configs:

/sys/class/sound/hwC0D2/user_pin_configs:

/sys/class/sound/hwC0D2/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   12.956932]   alloc kstat_irqs on node -1
[   12.956940] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.957044]   alloc irq_desc for 30 on node -1
[   12.957046]   alloc kstat_irqs on node -1
[   12.957058] HDA Intel 0000:00:1b.0: irq 30 for MSI/MSI-X
[   12.957094] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.094322] Console: switching to colour frame buffer device 170x48
--
[ 9866.460081] pciehp 0000:00:1c.0:pcie04: pciehp_suspend ENTRY
[ 9866.570450] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 9866.570502] ACPI handle has no context!
[ 9866.590025] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 129.938 msecs
[ 9866.590033] ehci_hcd 0000:00:1a.7: PCI INT D disabled
--
[ 9867.880487] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[ 9867.880532] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 9867.880537] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 9867.880579] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
--
[ 9868.450357] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 9868.450383] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 9868.450388] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 9868.450425] HDA Intel 0000:00:1b.0: irq 30 for MSI/MSI-X
[ 9868.450451] pciehp 0000:00:1c.0:pcie04: pciehp_resume ENTRY
--
[60022.405665] Hardware name: HP G60 Notebook PC
[60022.405667] Modules linked in: cryptd aes_x86_64 aes_generic binfmt_misc vmnet ppdev parport_pc vmblock vsock vmci vmmon ipt_REJECT xt_multiport xt_limit xt_tcpudp ipt_addrtype xt_state ip6table_filter ip6_tables nf_nat_irc snd_hda_codec_intelhdmi nf_conntrack_irc snd_hda_codec_conexant nf_nat_ftp fbcon snd_hda_intel tileblit snd_hda_codec nf_nat font snd_hwdep bitblit snd_pcm_oss snd_mixer_oss nf_conntrack_ipv4 nf_defrag_ipv4 softcursor snd_pcm vga16fb snd_seq_dummy snd_seq_oss vgastate snd_seq_midi joydev nf_conntrack_ftp snd_rawmidi snd_seq_midi_event nf_conntrack arc4 snd_seq i915 snd_timer iptable_filter snd_seq_device ip_tables drm_kms_helper drm i2c_algo_bit video x_tables psmouse output uvcvideo snd videodev soundcore snd_page_alloc intel_agp serio_raw iwlagn iwlcore mac80211 v4l1_compat led_class v4l2_compat_ioctl32 cfg80211 lp parport ahci r8169 mii
[60022.405728] Pid: 5730, comm: events/1 Not tainted 2.6.32-27-generic #49-Ubuntu
--
[60029.430070] pciehp 0000:00:1c.0:pcie04: pciehp_suspend ENTRY
[60029.540427] HDA Intel 0000:00:1b.0: PCI INT A disabled
[60029.540471] ACPI handle has no context!
[60029.560021] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 129.945 msecs
[60029.560028] ehci_hcd 0000:00:1a.7: PCI INT D disabled
--
[60030.770419] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[60030.770462] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[60030.770468] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[60030.770510] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
--
[60031.230362] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[60031.230388] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[60031.230394] HDA Intel 0000:00:1b.0: setting latency timer to 64
[60031.230432] HDA Intel 0000:00:1b.0: irq 30 for MSI/MSI-X
[60031.230460] pciehp 0000:00:1c.0:pcie04: pciehp_resume ENTRY

---

### Post by lidex on 2011-01-29
Try removing these entries from alsa-base.conf:
```
snd-hda-intel: power_save=10 power_save_controller=N
snd-hda-intel: position_fix=0 enable=yes

```
Reboot.
If you're using the conexant patched driver you shouldn't need model quirks and power save is unneeded as well.

---

### Post by badnaam on 2011-01-29
> **lidex said:**
> Try removing these entries from alsa-base.conf:
```
snd-hda-intel: power_save=10 power_save_controller=N
snd-hda-intel: position_fix=0 enable=yes

```
Reboot.
If you're using the conexant patched driver you shouldn't need model quirks and power save is unneeded as well.

I commented those two lines. Now when I plugin the headphone the sound comes out of the laptop speaker and the headphone, the laptop speakers don't get muted.

Here is the updated alsa-info.txt after running the alsa diagnostic script again.

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Jan 29 19:07:04 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      HP G60 Notebook PC
Product Version:   0392120000200C10000020000


!!Kernel Information
!!------------------

Kernel release:    2.6.32-27-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd4700000 irq 30


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 103c:360b


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1
	model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Conexant CX20583 (Pebble 56-LQFP)
Address: 0
Function Id: 0x2
Vendor Id: 0x14f15067
Subsystem Id: 0x103c360b
Revision Id: 0x100301
Modem Function Group: 0x2
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
  BIOS Profile: 1
Node 0x10 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x4a 0x4a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x13 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0f, mute=0
  Amp-Out vals:  [0x00]
Node 0x14 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x50 0x50] [0x80 0x80] [0x50 0x50] [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x15 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x16 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x17 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x03 0x03]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a 0x1b 0x1d 0x1e*
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x042140f0: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Green
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=37, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1a [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00001324: IN Detect
    Vref caps: HIZ 50 80
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=38, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00011334: IN OUT EAPD Detect
    Vref caps: HIZ 50 80
  EAPD 0x2: EAPD
  Pin Default 0x04a190f0: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=39, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1c [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=3a, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=3b, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1e [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x95a701f0: [Fixed] Mic at Int Top
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=3c, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x921701f0: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=3d, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="Conexant Digital Audio", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x22 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=3e, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
Node 0x23 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x04, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x24 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11
Node 0x25 [Vendor Defined Widget] wcaps 0xf00000: Mono
Codec: Intel G45 DEVCTG
Address: 2
Function Id: 0x1
Vendor Id: 0x80862802
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6211: 8-Channels Digital
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Device: name="INTEL HDMI 0", type="HDMI", device=3
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
Node 0x03 [Pin Complex] wcaps 0x40739d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=03, enabled=1
  Connection: 1
     0x02
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  0 Jan 29 11:05 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  4 Jan 29 11:05 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  6 Jan 29 11:05 /dev/snd/hwC0D2
crw-rw----+ 1 root audio 116, 24 Jan 29 11:05 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 16 Jan 29 11:06 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 17 Jan 29 11:05 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 19 Jan 29 11:05 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116, 30 Jan 29 11:05 /dev/snd/pcmC0D6c
crw-rw----+ 1 root audio 116, 22 Jan 29 11:05 /dev/snd/pcmC0D6p
crw-rw----+ 1 root audio 116,  1 Jan 29 11:05 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jan 29 11:05 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jan 29 11:05 .
drwxr-xr-x 3 root root 280 Jan 29 11:05 ..
lrwxrwxrwx 1 root root  12 Jan 29 11:05 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital Audio [Conexant Digital Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Conexant HSF Modem [Conexant HSF Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Conexant HSF Modem [Conexant HSF Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xd4700000 irq 30'
  Mixer name	: 'Intel G45 DEVCTG'
  Components	: 'HDA:14f15067,103c360b,00100301 HDA:80862802,80860101,00100000'
  Controls      : 24
  Simple ctrls  : 16
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '30dB'
Simple mixer control 'Automute',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'DMIC1 Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '12dB' '24dB' '36dB' '48dB'
  Item0: '0dB'
Simple mixer control 'Input',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [on]
  Front Right: Capture 80 [100%] [6.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic_F' 'LineIn_F' 'Mic_B' 'LineIn_B' 'Mic_C' 'LineIn_C' 'LineIn_E' 'DMIC_J'
  Item0: 'Mic_F'
Simple mixer control 'PortA Jack Mode',0
  Capabilities: enum
  Items: 'Off' 'Line out' 'Headphone out'
  Item0: 'Headphone out'
Simple mixer control 'PortB Jack Mode',0
  Capabilities: enum
  Items: 'Off' 'Mic 50pc bias' 'Mic 80pc bias' 'Line in'
  Item0: 'Mic 80pc bias'
Simple mixer control 'PortC Jack Mode',0
  Capabilities: enum
  Items: 'Off' 'Mic 50pc bias' 'Mic 80pc bias' 'Line in' 'Line out' 'Headphone out'
  Item0: 'Mic 80pc bias'
Simple mixer control 'PortD Jack Mode',0
  Capabilities: enum
  Items: 'Off' 'Line out' 'Headphone out'
  Item0: 'Off'
Simple mixer control 'PortE Jack Mode',0
  Capabilities: enum
  Items: 'Off' 'Line in' 'Line out' 'Headphone out'
  Item0: 'Line in'
Simple mixer control 'PortG Jack Mode',0
  Capabilities: enum
  Items: 'Off' 'Line out' 'Headphone out'
  Item0: 'Line out'


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 74'
		comment.dbmin -7400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 74
		value.1 74
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Automute Switch'
		value false
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic_F
		comment.item.1 LineIn_F
		comment.item.2 Mic_B
		comment.item.3 LineIn_B
		comment.item.4 Mic_C
		comment.item.5 LineIn_C
		comment.item.6 LineIn_E
		comment.item.7 DMIC_J
		iface MIXER
		name 'Input Source Capture Route'
		value Mic_F
	}
	control.5 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '0dB'
		comment.item.1 '10dB'
		comment.item.2 '20dB'
		comment.item.3 '30dB'
		comment.item.4 '40dB'
		iface MIXER
		name 'Analog Mic Boost Capture Enum'
		value '30dB'
	}
	control.6 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '0dB'
		comment.item.1 '12dB'
		comment.item.2 '24dB'
		comment.item.3 '36dB'
		comment.item.4 '48dB'
		iface MIXER
		name 'DMIC1 Mic Boost Capture Enum'
		value '0dB'
	}
	control.7 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Off
		comment.item.1 'Mic 50pc bias'
		comment.item.2 'Mic 80pc bias'
		comment.item.3 'Line in'
		iface MIXER
		name 'PortB Jack Mode'
		value 'Mic 80pc bias'
	}
	control.8 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Off
		comment.item.1 'Mic 50pc bias'
		comment.item.2 'Mic 80pc bias'
		comment.item.3 'Line in'
		comment.item.4 'Line out'
		comment.item.5 'Headphone out'
		iface MIXER
		name 'PortC Jack Mode'
		value 'Mic 80pc bias'
	}
	control.9 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Off
		comment.item.1 'Line in'
		comment.item.2 'Line out'
		comment.item.3 'Headphone out'
		iface MIXER
		name 'PortE Jack Mode'
		value 'Line in'
	}
	control.10 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Off
		comment.item.1 'Line out'
		comment.item.2 'Headphone out'
		iface MIXER
		name 'PortA Jack Mode'
		value 'Headphone out'
	}
	control.11 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Off
		comment.item.1 'Line out'
		comment.item.2 'Headphone out'
		iface MIXER
		name 'PortG Jack Mode'
		value 'Line out'
	}
	control.12 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Off
		comment.item.1 'Line out'
		comment.item.2 'Headphone out'
		iface MIXER
		name 'PortD Jack Mode'
		value Off
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 80'
		comment.dbmin -7400
		comment.dbmax 600
		iface MIXER
		name 'Input Capture Volume'
		value.0 80
		value.1 80
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Input Capture Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.16 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.17 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.20 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 1
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.21 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 1
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.22 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		index 1
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.23 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		index 1
		value true
	}
	control.24 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
cryptd
aes_x86_64
aes_generic
binfmt_misc
ppdev
vmnet
parport_pc
vmblock
vsock
vmci
vmmon
snd_hda_codec_intelhdmi
snd_hda_codec_conexant
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
joydev
ipt_REJECT
xt_multiport
xt_limit
xt_tcpudp
ipt_addrtype
xt_state
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
ip6table_filter
snd_seq_oss
ip6_tables
snd_seq_midi
snd_rawmidi
nf_nat_irc
nf_conntrack_irc
snd_seq_midi_event
nf_nat_ftp
snd_seq
arc4
nf_nat
nf_conntrack_ipv4
nf_defrag_ipv4
nf_conntrack_ftp
nf_conntrack
snd_timer
snd_seq_device
iptable_filter
iwlagn
i915
ip_tables
x_tables
snd
drm_kms_helper
iwlcore
mac80211
led_class
uvcvideo
videodev
v4l1_compat
v4l2_compat_ioctl32
cfg80211
psmouse
serio_raw
intel_agp
drm
i2c_algo_bit
soundcore
snd_page_alloc
video
output
lp
parport
r8169
mii
ahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x19 0x042140f0
0x1a 0x400001f0
0x1b 0x04a190f0
0x1c 0x400001f0
0x1d 0x400001f0
0x1e 0x95a701f0
0x1f 0x921701f0
0x20 0x400001f0
0x22 0x400001f0
0x23 0x400001f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D2/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D2/driver_pin_configs:

/sys/class/sound/hwC0D2/user_pin_configs:

/sys/class/sound/hwC0D2/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   14.884594]   alloc kstat_irqs on node -1
[   14.884601] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.884675]   alloc irq_desc for 30 on node -1
[   14.884677]   alloc kstat_irqs on node -1
[   14.884690] HDA Intel 0000:00:1b.0: irq 30 for MSI/MSI-X
[   14.884724] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.887511] vga16fb: initializing

---

### Post by badnaam on 2011-01-29
> **lidex said:**
> Try removing these entries from alsa-base.conf:
```
snd-hda-intel: power_save=10 power_save_controller=N
snd-hda-intel: position_fix=0 enable=yes

```
Reboot.
If you're using the conexant patched driver you shouldn't need model quirks and power save is unneeded as well.

Also, here are the screenshots of alsamixer

---

### Post by lidex on 2011-01-29
Seems this has been ongoing issue and the bug report has gotten nowhere. Try using a later kernel to see if it's fixed upstream:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by badnaam on 2011-01-29
> **lidex said:**
> Seems this has been ongoing issue and the bug report has gotten nowhere. Try using a later kernel to see if it's fixed upstream:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

Here is my kernel version


Linux ubuntu 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux

I don't even think there is an update version available is there?

---

### Post by lidex on 2011-01-29
If you follow that link it explains how you can do it easily.

---

