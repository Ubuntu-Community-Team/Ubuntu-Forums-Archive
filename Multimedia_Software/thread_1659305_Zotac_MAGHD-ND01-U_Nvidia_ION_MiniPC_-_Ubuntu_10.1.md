---
title: "Zotac MAGHD-ND01-U Nvidia ION MiniPC - Ubuntu 10.10 sound not working"
date: 2011-01-03
forum: Multimedia Software
---

### Post by jsmkbunch2000 on 2011-01-03
Ok, I have searched all the forums and I am seing multiple discussions like what I am experiencing,but I am completely lost.  I am a noobie and need step by step instrux on how to fix my Nvidia sound driver for my Zotac MAGHD-ND01-U Nvidia ION MiniPC I bought from tiger direct.  I have absolutely NO sound.  Can anyone help me to get my sound working.  Thanks.  if you need me to post some information here on my computer, please walk me through how to do that as well - Sorry, I'm an absolute noob  :(

---

### Post by lidex on 2011-01-04
Can you pull up a terminal? Copy and paste this command into it and press enter. Let it do its thing until it asks for input from you: something like do you want to upload y/n. Key in y (for yes) and press enter. The terminal will output a link to your info. Include that link in your next post.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by jsmkbunch2000 on 2011-01-04
Ok here is the link and information: [http://www.alsa-project.org/db/?f=440d3c3aa8160f9f8100f44682798043d2e0f01b](http://www.alsa-project.org/db/?f=440d3c3aa8160f9f8100f44682798043d2e0f01b)
 

[PHP]
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Wed Jan  5 00:10:30 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      To Be Filled By O.E.M.
Product Name:      To Be Filled By O.E.M.


!!Kernel Information
!!------------------

Kernel release:    2.6.35-24-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


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

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfae78000 irq 20


!!PCI Soundcards installed in the system
!!--------------------------------------

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:08.0 0403: 10de:0ac0 (rev b1)
	Subsystem: 10de:a113


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC888
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0888
Subsystem Id: 0x10eca113
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
  Device: name="ALC888 Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC888 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC888 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x12 0x12]
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
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x18 0x18]
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
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19c30: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x0
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
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
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
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40020601: [N/A] Line Out at Ext N/A
    Conn = 1/4, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01441120: [Jack] SPDIF Out at Ext Rear
    Conn = RCA, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
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
Codec: Nvidia MCP79/7A HDMI
Address: 3
Function Id: 0x1
Vendor Id: 0x10de0007
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=3
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
  Pin-ctls: 0x40: OUT
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
  Pin-ctls: 0x40: OUT
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
  Pin-ctls: 0x40: OUT
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
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0c
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 10 Jan  3 17:58 /dev/snd/controlC0
crw-rw----  1 root audio 116,  9 Jan  3 17:58 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  8 Jan  3 17:58 /dev/snd/hwC0D3
crw-rw----  1 root audio 116,  7 Jan  3 18:34 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  6 Jan  3 18:08 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  5 Jan  3 18:16 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  4 Jan  4 17:09 /dev/snd/pcmC0D3p
crw-rw----  1 root audio 116,  3 Jan  3 17:58 /dev/snd/seq
crw-rw----  1 root audio 116,  2 Jan  3 17:58 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jan  3 17:58 .
drwxr-xr-x 3 root root 240 Jan  3 17:58 ..
lrwxrwxrwx 1 root root  12 Jan  3 17:58 pci-0000:00:08.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

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

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [NVidia]

Card hw:0 'NVidia'/'HDA NVidia at 0xfae78000 irq 20'
  Mixer name	: 'Nvidia MCP79/7A HDMI'
  Components	: 'HDA:10ec0888,10eca113,00100001 HDA:10de0007,10de0101,00100100'
  Controls      : 19
  Simple ctrls  : 9
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 24 [77%] [-10.50dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 228 [89%] [-5.40dB]
  Front Right: Playback 228 [89%] [-5.40dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
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
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 18 [58%] [10.50dB] [on]
  Front Right: Capture 18 [58%] [10.50dB] [on]


!!Alsactl output
!!-------------

--startcollapse--
state.NVidia {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 31
		value.1 31
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Mic Boost'
		value.0 0
		value.1 0
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1650
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		value.0 18
		value.1 18
	}
	control.8 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.9 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.10 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 24
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.15 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 1
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.16 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 1
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.17 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		index 1
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		index 1
		value false
	}
	control.19 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 228
		value.1 228
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
parport_pc
ppdev
nvidia
snd_hda_codec_nvhdmi
snd_hda_codec_realtek
arc4
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
ath9k
snd_seq_midi
ath9k_common
snd_rawmidi
snd_seq_midi_event
snd_seq
ath9k_hw
ath
mac80211
snd_timer
snd_seq_device
cfg80211
snd
led_class
joydev
i2c_nforce2
psmouse
serio_raw
soundcore
shpchp
snd_page_alloc
agpgart
lp
parport
hid_logitech
ff_memless
usbhid
hid
usb_storage
ahci
forcedeth
libahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x14 0x01014410
0x15 0x411111f0
0x16 0x411111f0
0x17 0x411111f0
0x18 0x01a19c30
0x19 0x411111f0
0x1a 0x411111f0
0x1b 0x411111f0
0x1c 0x411111f0
0x1d 0x40020601
0x1e 0x01441120
0x1f 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D3/init_pin_configs:
0x05 0x18560110
0x07 0x58560121
0x09 0x58560122
0x0b 0x58560123
0x0d 0x58560124

/sys/class/sound/hwC0D3/driver_pin_configs:

/sys/class/sound/hwC0D3/user_pin_configs:

/sys/class/sound/hwC0D3/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   15.737570]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.544393] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   16.544531] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   16.545749] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   16.545766] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[   16.545776] hda_intel: Disable MSI for Nvidia chipset
[   16.545846] HDA Intel 0000:00:08.0: setting latency timer to 64
[   16.743102] nvidia: module license 'NVIDIA' taints kernel.
--
[   17.327958] type=1400 audit(1294102700.918:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=880 comm="apparmor_parser"
[   17.620039] hda_codec: ALC888: BIOS auto-probing.
[   19.976521] eth0: no link during initialization.
--
[10301.504083] ehci_hcd 0000:00:06.1: PCI INT B disabled
[10301.792049] HDA Intel 0000:00:08.0: PCI INT A disabled
[10301.808499] HDA Intel 0000:00:08.0: power state changed by ACPI to D3
[10301.808512] PM: suspend of drv:HDA Intel dev:0000:00:08.0 complete after 332.624 msecs
[10302.328971] PM: suspend of drv:sd dev:0:0:0:0 complete after 855.966 msecs
--
[10303.205045] ehci_hcd 0000:00:06.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[10303.205090] HDA Intel 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[10303.205153] forcedeth 0000:00:0a.0: restoring config space at offset 0x7 (was 0x0, writing 0xfae7e000)
--
[10303.207601] ehci_hcd 0000:00:06.1: setting latency timer to 64
[10303.207842] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[10303.207854] pci 0000:00:09.0: setting latency timer to 64
[10303.208080] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[10303.208423] pci 0000:00:10.0: setting latency timer to 64
--
[10303.209652] ahci 0000:00:0b.0: setting latency timer to 64
[10303.210121] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[10303.210233] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[10303.210257] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[10303.210273] HDA Intel 0000:00:08.0: setting latency timer to 64
[10303.211370] sd 0:0:0:0: [sda] Starting disk
--
[15031.204062] ehci_hcd 0000:00:06.1: PCI INT B disabled
[15031.380058] HDA Intel 0000:00:08.0: PCI INT A disabled
[15031.396207] HDA Intel 0000:00:08.0: power state changed by ACPI to D3
[15031.396219] PM: suspend of drv:HDA Intel dev:0000:00:08.0 complete after 220.135 msecs
[15032.021727] PM: suspend of drv:sd dev:0:0:0:0 complete after 848.747 msecs
--
[15032.897049] ehci_hcd 0000:00:06.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[15032.897094] HDA Intel 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[15032.897158] forcedeth 0000:00:0a.0: restoring config space at offset 0x7 (was 0x0, writing 0xfae7e000)
--
[15032.899468] ehci_hcd 0000:00:06.1: setting latency timer to 64
[15032.899603] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[15032.899725] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[15032.899739] pci 0000:00:09.0: setting latency timer to 64
[15032.899901] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[15032.900080] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[15032.900188] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[15032.900200] HDA Intel 0000:00:08.0: setting latency timer to 64
[15032.900270] ahci 0000:00:0b.0: setting latency timer to 64
--
[20201.720122] ehci_hcd 0000:00:04.1: PCI INT B disabled
[20201.900055] HDA Intel 0000:00:08.0: PCI INT A disabled
[20201.916209] HDA Intel 0000:00:08.0: power state changed by ACPI to D3
[20201.916221] PM: suspend of drv:HDA Intel dev:0000:00:08.0 complete after 223.181 msecs
[20202.084265] PM: suspend of drv:sd dev:0:0:0:0 complete after 395.726 msecs
--
[20202.917054] ehci_hcd 0000:00:06.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[20202.917100] HDA Intel 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[20202.917163] forcedeth 0000:00:0a.0: restoring config space at offset 0x7 (was 0x0, writing 0xfae7e000)
--
[20202.919863] pci 0000:00:09.0: setting latency timer to 64
[20202.920313] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[20202.920354] pci 0000:00:10.0: setting latency timer to 64
[20202.920401] ahci 0000:00:0b.0: setting latency timer to 64
[20202.920698] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[20202.920819] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[20202.920935] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[20202.920958] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[20202.920973] HDA Intel 0000:00:08.0: setting latency timer to 64
[20202.921084] ath9k 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
--
[27026.532104] ehci_hcd 0000:00:06.1: PCI INT B disabled
[27026.824049] HDA Intel 0000:00:08.0: PCI INT A disabled
[27026.840206] HDA Intel 0000:00:08.0: power state changed by ACPI to D3
[27026.840218] PM: suspend of drv:HDA Intel dev:0000:00:08.0 complete after 334.308 msecs
[27026.894352] PM: suspend of drv:sd dev:0:0:0:0 complete after 392.376 msecs
--
[27027.829011] ehci_hcd 0000:00:06.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[27027.829056] HDA Intel 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[27027.829120] forcedeth 0000:00:0a.0: restoring config space at offset 0x7 (was 0x0, writing 0xfae7e000)
--
[27027.831469] ehci_hcd 0000:00:06.1: setting latency timer to 64
[27027.831602] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[27027.831769] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[27027.831780] pci 0000:00:09.0: setting latency timer to 64
[27027.831910] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[27027.832061] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[27027.832084] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[27027.832097] HDA Intel 0000:00:08.0: setting latency timer to 64
[27027.832164] ahci 0000:00:0b.0: setting latency timer to 64


[/PHP]

---

### Post by lidex on 2011-01-04
Yeah, OK...How about these outputs then:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by jsmkbunch2000 on 2011-01-04
[PHP]livingroom@livingroom-desktop:~$ sudo dmidecode -t bios
[sudo] password for livingroom: 
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: 080015 
	Release Date: 10/09/2009
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 8.15

Handle 0x0022, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

livingroom@livingroom-desktop:~$ sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: To be filled by O.E.M.
	Product Name: To be filled by O.E.M.
	Version: To be filled by O.E.M.
	Serial Number: To be filled by O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To Be Filled By O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

livingroom@livingroom-desktop:~$ 
[/PHP]

---

### Post by lidex on 2011-01-04
For now see if a bios update is available while I try to figure something out.

---

### Post by jsmkbunch2000 on 2011-01-05
I ran the update manager if that is what you meant and my system is up to date.  Otherwise, please tell me how to do that.

---

### Post by lidex on 2011-01-05
The drivers are here:
[http://www.zotacusa.com/downloads/?cat=210](http://www.zotacusa.com/downloads/?cat=210)

---

### Post by jsmkbunch2000 on 2011-01-05
How do I install the updated drivers???  Sorry, not really experienced on Linux with this.  I know in Windows (which I am glad to be rid of) you can just double click an .exe file and it will auto install.  How do I do this for these updates.  I would prefer to use the terminal if at all possible.  Thanks.

---

### Post by tjones00 on 2011-01-05
[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

The above link is a bit outdated but it should get you on the right track. The safest way is to use a bootdisk this can be done with a USB stick.

Just be careful and triple check to make sure you are using the proper bios file from the manufacturer.

---

### Post by jsmkbunch2000 on 2011-01-05
hmm, I am not a techno geek here, so with all the "warnings" from that thread, I think it is safer to go back to windows xp for now.  (again, Linux fails me, and I keep trying...  I'll try again to see if it's better in a year or so.  :frown:

---

### Post by tjones00 on 2011-01-05
The warnings are the same as in windows flashing a bios is a very delicate thing and you need to be careful. Windows just doesn't fully disclose how important it is to do it properly.

When flashing using windows the bootdisk procedure is pretty much the same as with linux. 

1) create bootable dos FAT32 floppy/usb including some flash utilities.

2) copy bios .bin file to the bootdisk

3) boot from the bootdisk and flash.

Follow up question does your sound work in windows? If so a bios update shouldn't be required.

---

### Post by BicyclerBoy on 2011-01-05
The OP was talking about nvidia audio so did they mean HDMI audio ?

They could just need an updated nvidia graphics driver (260) ? & alsa 1.0.23

---

### Post by qr25de on 2011-01-06
Also to mention, to get my HDMI audio working I have to manually change the output device when I plug in the HDMI cable. So with that said, pull up Sound from System -> Preferences -> Sound. Check your output device. Test with what you see (have a song or movie playing).

... are your speakers plugged in and turned on? Also is the volume up/not on mute... heh heh

---

