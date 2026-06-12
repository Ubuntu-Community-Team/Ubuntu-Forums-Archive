---
title: "No Sound"
date: 2009-12-07
forum: Multimedia Software
---

### Post by sevenfactorial on 2009-12-07
Hello,

I know there are already tons of threads on no sound, and I have tried some of those solutions to no avail.

I recently upgraded to 9.10, and I'm running on a Dell Optiplex 760.

Does anyone have any advice?  I'm sorry I can't be more specific about the symptoms.

Thank you,

H.

---

### Post by Rockanium on 2009-12-07
No sound in what?

When you turn your computer on do u get a sound? same when u log on and off?

or is it just youtube and movie player, other things like that.

---

### Post by FalloutMan on 2009-12-07
I have the same issue but I did a little research first.  This is what I get when I do the aplay -l:
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

So ubuntu knows that theres a device but when I go into Sound Preferences and go to the Hardware tab it doesnt have ANY devices listed to configure.  My sound will work *sometimes* and I can't figure out what makes it work and not work.  When it does work everything works like normal but when it doesnt then nothing works at all.  Even reboots dont fix it. It either works or doesnt work : /  
When I mouse over the volume button on the top toolbar it says Dummy Output when sound works and doesnt work.  Under Output in sound pref it says Dummy Output and and nothing under Input even though 9.04 had the correct thing in both tabs from the getgo.  This 9.10 install is a clean install fresh from a MD5 checksum verified ISO of 32bit 9.10 that was downloaded roughly 5 days after launch.

---

### Post by sevenfactorial on 2009-12-09
My output is


$ aplay -l
aplay: device_list:223: no soundcards found...


$ sudo lspci |grep udio

00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)


Does anyone know what I should do?  Many thanks,

Also, in response to the person who kindly responded:  I get no sound whatsoever at any time.

H.

---

### Post by sevenfactorial on 2009-12-10
Here's some more info on my machine. 

 Two things I think are ominous.   One is that while my alsa utils and alsa lib version are 1.0.21, my driver is still 1.0.18; I tried to update all three of them today, but only two succeeded.

Another thing is that according to uname -r, my kernel version is 2.6.28-15-generic.  However, a lot of my headers seem to be for other versions; I don't have any headers for the above mentioned version, only 2.6.31-15 and 2.6.31-16.   This may have caused problems during my alsa upgrade; there were no errors, but I had to create /usr/src/linux  and stuff it with some of the (non-version-appropriate) header material.

Any help is very much appreciated,

H.




**Thursday, December  10th, 2009 at 4:34:52pm MST **

[CENTER]Font: [Small]("javascript:void(0)") - [Normal]("javascript:void(0)") - [Large]("javascript:void(0)")[/CENTER]
 	[FONT=monospace]
[LIST=1]
[*][COLOR=brown][FONT=monospace]**################################**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**ALSA Information Script v 0.4.58**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**################################**[/FONT][/COLOR]
[*]
[*][COLOR=brown][FONT=monospace]**Script ran on: Thu Dec 10 23:34:35 UTC 2009**[/FONT][/COLOR]
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Linux Distribution**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------------**[/FONT][/COLOR]
[*]
[*]Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"
[*]
[*]
[*][COLOR=brown][FONT=monospace]**DMI Information**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**---------------**[/FONT][/COLOR]
[*]
[*]Manufacturer:      Dell Inc.
[*]Product Name:      OptiPlex 760                 
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Kernel Information**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------------**[/FONT][/COLOR]
[*]
[*]Kernel release:    2.6.28-15-generic
[*]Operating System:  GNU/Linux
[*]Architecture:      i686
[*]Processor:         unknown
[*]SMP Enabled:       Yes
[*]
[*]
[*][COLOR=brown][FONT=monospace]**ALSA Version**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------**[/FONT][/COLOR]
[*]
[*]Driver version:     1.0.18rc3
[*]Library version:    1.0.21a
[*]Utilities version:  1.0.21
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Loaded ALSA modules**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-------------------**[/FONT][/COLOR]
[*]
[*]snd_hda_intel
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Sound Servers on this system**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**----------------------------**[/FONT][/COLOR]
[*]
[*]No sound servers found.
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Soundcards recognised by ALSA**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-----------------------------**[/FONT][/COLOR]
[*]
[*] 0 [Intel          ]: HDA-Intel - HDA Intel
[*]                      HDA Intel at 0xfebdc000 irq 16
[*]
[*]
[*][COLOR=brown][FONT=monospace]**PCI Soundcards installed in the system**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**--------------------------------------**[/FONT][/COLOR]
[*]
[*]00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Advanced information - PCI Vendor/Device/Susbsystem ID's**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**--------------------------------------------------------**[/FONT][/COLOR]
[*]
[*]00:1b.0 0403: 8086:3a6e (rev 02)
[*]        Subsystem: 1028:027f
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Modprobe options (Sound related)**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**--------------------------------**[/FONT][/COLOR]
[*]
[*]snd-atiixp-modem: index=-2
[*]snd-intel8x0m: index=-2
[*]snd-via82xx-modem: index=-2
[*]snd-usb-audio: index=-2
[*]snd-usb-us122l: index=-2
[*]snd-usb-usx2y: index=-2
[*]snd-usb-caiaq: index=-2
[*]snd-cmipci: mpu_port=0x330 fm_port=0x388
[*]snd-pcsp: index=-2
[*]snd-hda-intel: power_save=10 power_save_controller=N
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Loaded sound module options**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**--------------------------**[/FONT][/COLOR]
[*]
[*][COLOR=brown][FONT=monospace]**Module: snd_hda_intel**[/FONT][/COLOR]
[*]        bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
[*]        enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
[*]        enable_msi : 0
[*]        id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
[*]        index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
[*]        model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
[*]        position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
[*]        power_save : 10
[*]        power_save_controller : N
[*]        probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
[*]        single_cmd : N
[*]
[*]
[*][COLOR=brown][FONT=monospace]**HDA-Intel Codec information**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**---------------------------**[/FONT][/COLOR]
[*][(following section hidden - click to display)]("javascript:showColl(1)")
[/LIST]

[LIST]
[*]
[*]Codec: Analog Devices AD1984A
[*]Address: 2
[*]Vendor Id: 0x11d4194a
[*]Subsystem Id: 0x1028027f
[*]Revision Id: 0x100400
[*]No Modem Function Group found
[*]Default PCM:
[*]    rates [0x7ff]: 8000 11025 16000 22050 32000 44100 48000 88200 96000 176400 192000
[*]    bits [0xe]: 16 20 24
[*]    formats [0x1]: PCM
[*]Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]Default Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
[*]GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
[*]  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0
[*]  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=1
[*]  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0
[*]Node 0x02 [Audio Output] wcaps 0x30211: Stereo Digital
[*]  Converter: stream=0, channel=0
[*]  Digital:
[*]  Digital category: 0x0
[*]  PCM:
[*]    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
[*]    bits [0xe]: 16 20 24
[*]    formats [0x5]: PCM AC3
[*]  Delay: 3 samples
[*]Node 0x03 [Audio Output] wcaps 0x405: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
[*]  Amp-Out vals:  [0x27 0x27]
[*]  Converter: stream=0, channel=0
[*]  Power: setting=D0, actual=D3
[*]Node 0x04 [Audio Output] wcaps 0x405: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
[*]  Amp-Out vals:  [0x27 0x27]
[*]  Converter: stream=0, channel=0
[*]  Power: setting=D0, actual=D3
[*]Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
[*]Node 0x06 [Vendor Defined Widget] wcaps 0xf00000: Mono
[*]Node 0x07 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x00 0x00]
[*]  Connection: 2
[*]     0x22 0x21
[*]Node 0x08 [Audio Input] wcaps 0x100501: Stereo
[*]  Converter: stream=0, channel=0
[*]  SDI-Select: 0
[*]  Power: setting=D0, actual=D3
[*]  Connection: 1
[*]     0x0c
[*]Node 0x09 [Audio Input] wcaps 0x100501: Stereo
[*]  Converter: stream=0, channel=0
[*]  SDI-Select: 0
[*]  Power: setting=D0, actual=D3
[*]  Connection: 1
[*]     0x0d
[*]Node 0x0a [Audio Mixer] wcaps 0x200103: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x00 0x00]
[*]  Connection: 2
[*]     0x04 0x21
[*]Node 0x0b [Audio Mixer] wcaps 0x200103: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x80 0x80]
[*]  Connection: 2
[*]     0x0f 0x21
[*]Node 0x0c [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
[*]  Amp-Out vals:  [0x80 0x80]
[*]  Connection: 6
[*]     0x14* 0x15 0x16 0x20 0x25 0x17
[*]Node 0x0d [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
[*]  Amp-Out vals:  [0x80 0x80]
[*]  Connection: 6
[*]     0x14* 0x15 0x16 0x20 0x25 0x17
[*]Node 0x0e [Audio Selector] wcaps 0x300101: Stereo
[*]  Connection: 2
[*]     0x03* 0x04
[*]Node 0x0f [Audio Selector] wcaps 0x300101: Stereo
[*]  Connection: 2
[*]     0x03* 0x04
[*]Node 0x10 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
[*]  Amp-Out caps: ofs=0x0f, nsteps=0x0f, stepsize=0x0b, mute=1
[*]  Amp-Out vals:  [0x00]
[*]Node 0x11 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x80 0x80]
[*]  Pincap 0x0000001f: OUT HP Detect Trigger ImpSense
[*]  Pin Default 0x02214040: [Jack] HP Out at Ext Front
[*]    Conn = 1/8, Color = Green
[*]    DefAssociation = 0x4, Sequence = 0x0
[*]  Pin-ctls: 0xc0: OUT HP
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 1
[*]     0x07
[*]Node 0x12 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x80 0x80]
[*]  Pincap 0x0001001f: OUT HP EAPD Detect Trigger ImpSense
[*]  EAPD 0x0:
[*]  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
[*]    Conn = 1/8, Color = Green
[*]    DefAssociation = 0x1, Sequence = 0x0
[*]  Pin-ctls: 0xc0: OUT HP
[*]  Unsolicited: tag=00, enabled=0
[*]  Power: setting=D0, actual=D0
[*]  Connection: 1
[*]     0x0a
[*]Node 0x13 [Pin Complex] wcaps 0x40050c: Mono Amp-Out
[*]  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
[*]  Amp-Out vals:  [0x00]
[*]  Pincap 0x00010010: OUT EAPD
[*]  EAPD 0x0:
[*]  Pin Default 0x991301f0: [Fixed] Speaker at Int ATAPI
[*]    Conn = ATAPI, Color = Unknown
[*]    DefAssociation = 0xf, Sequence = 0x0
[*]    Misc = NO_PRESENCE
[*]  Pin-ctls: 0x40: OUT
[*]  Power: setting=D0, actual=D0
[*]  Connection: 1
[*]     0x1f
[*]Node 0x14 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
[*]  Amp-In vals:  [0x00 0x00]
[*]  Pincap 0x00003727: IN Detect Trigger ImpSense
[*]    Vref caps: HIZ 50 GRD 80 100
[*]  Pin Default 0x02a19020: [Jack] Mic at Ext Front
[*]    Conn = 1/8, Color = Pink
[*]    DefAssociation = 0x2, Sequence = 0x0
[*]  Pin-ctls: 0x24: IN VREF_80
[*]  Unsolicited: tag=00, enabled=0
[*]Node 0x15 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
[*]  Amp-In vals:  [0x00 0x00]
[*]  Pincap 0x00003727: IN Detect Trigger ImpSense
[*]    Vref caps: HIZ 50 GRD 80 100
[*]  Pin Default 0x01813030: [Jack] Line In at Ext Rear
[*]    Conn = 1/8, Color = Blue
[*]    DefAssociation = 0x3, Sequence = 0x0
[*]  Pin-ctls: 0x20: IN VREF_HIZ
[*]  Unsolicited: tag=00, enabled=0
[*]Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x80 0x80]
[*]  Pincap 0x00010037: IN OUT EAPD Detect Trigger ImpSense
[*]  EAPD 0x0:
[*]  Pin Default 0x413301f0: [N/A] CD at Ext Rear
[*]    Conn = ATAPI, Color = Unknown
[*]    DefAssociation = 0xf, Sequence = 0x0
[*]    Misc = NO_PRESENCE
[*]  Pin-ctls: 0x20: IN
[*]  Unsolicited: tag=00, enabled=0
[*]  Power: setting=D0, actual=D0
[*]  Connection: 1
[*]     0x0b
[*]Node 0x17 [Pin Complex] wcaps 0x40020b: Stereo Digital Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x17, mute=0
[*]  Amp-In vals:  [0x00 0x00]
[*]  Pincap 0x00000020: IN
[*]  Pin Default 0x41a601f0: [N/A] Mic at Ext Rear
[*]    Conn = Digital, Color = Unknown
[*]    DefAssociation = 0xf, Sequence = 0x0
[*]    Misc = NO_PRESENCE
[*]  Pin-ctls: 0x24: IN
[*]Node 0x18 [Vendor Defined Widget] wcaps 0xf00100: Mono
[*]  Connection: 1
[*]     0x06
[*]Node 0x19 [Power Widget] wcaps 0x500500: Mono
[*]  Power: setting=D0, actual=D0
[*]  Connection: 2
[*]     0x20* 0x21
[*]Node 0x1a [Pin Complex] wcaps 0x400000: Mono
[*]  Pincap 0x00000020: IN
[*]  Pin Default 0x41f301f0: [N/A] Other at Ext Rear
[*]    Conn = ATAPI, Color = Unknown
[*]    DefAssociation = 0xf, Sequence = 0x0
[*]    Misc = NO_PRESENCE
[*]  Pin-ctls: 0x20: IN
[*]Node 0x1b [Pin Complex] wcaps 0x40038d: Stereo Digital Amp-Out
[*]  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=1
[*]  Amp-Out vals:  [0x27 0x27]
[*]  Pincap 0x00000014: OUT Detect
[*]  Pin Default 0x414501f0: [N/A] SPDIF Out at Ext Rear
[*]    Conn = Optical, Color = Unknown
[*]    DefAssociation = 0xf, Sequence = 0x0
[*]    Misc = NO_PRESENCE
[*]  Pin-ctls: 0x00:
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 1
[*]     0x02
[*]Node 0x1c [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x80 0x80]
[*]  Pincap 0x00003737: IN OUT Detect Trigger ImpSense
[*]    Vref caps: HIZ 50 GRD 80 100
[*]  Pin Default 0x413301f0: [N/A] CD at Ext Rear
[*]    Conn = ATAPI, Color = Unknown
[*]    DefAssociation = 0xf, Sequence = 0x0
[*]    Misc = NO_PRESENCE
[*]  Pin-ctls: 0x24: IN VREF_80
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 1
[*]     0x24
[*]Node 0x1d [Vendor Defined Widget] wcaps 0xf00100: Mono
[*]  Connection: 25
[*]     0x07* 0x0a 0x0b 0x0c 0x0d 0x0e 0x0f 0x11 0x12 0x13 0x14 0x15 0x16 0x19 0x1a 0x1c 0x1e 0x1f 0x20 0x21 0x22 0x23 0x24 0x25 0x26
[*]Node 0x1e [Audio Mixer] wcaps 0x200103: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x00 0x00]
[*]  Connection: 2
[*]     0x0e 0x21
[*]Node 0x1f [Audio Mixer] wcaps 0x200100: Mono
[*]  Connection: 1
[*]     0x1e
[*]Node 0x20 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
[*]  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x97 0x97]
[*]  Connection: 7
[*]     0x14 0x15 0x16 0x1a 0x25 0x03 0x04
[*]Node 0x21 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
[*]  Amp-Out vals:  [0x80 0x80]
[*]  Connection: 1
[*]     0x20
[*]Node 0x22 [Audio Selector] wcaps 0x300101: Stereo
[*]  Connection: 2
[*]     0x03* 0x04
[*]Node 0x23 [Audio Selector] wcaps 0x300101: Stereo
[*]  Connection: 2
[*]     0x03* 0x04
[*]Node 0x24 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x80 0x80]
[*]  Connection: 2
[*]     0x23 0x21
[*]Node 0x25 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Connection: 1
[*]     0x1c
[*]Node 0x26 [Vendor Defined Widget] wcaps 0xf00100: Mono
[*]  Connection: 3
[*]     0x14* 0x15 0x1c
[*]Node 0x27 [Vendor Defined Widget] wcaps 0xf00301: Stereo Digital
[*]  Connection: 2
[*]     0x08* 0x09
[*]Node 0x28 [Vendor Defined Widget] wcaps 0xf0030d: Stereo Digital Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x80 0x80]
[*]  Connection: 2
[*]     0x08* 0x09
[*]Node 0x29 [Vendor Defined Widget] wcaps 0xf0030d: Stereo Digital Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x80 0x80]
[*]  Connection: 2
[*]     0x08* 0x09
[*]Node 0x2a [Vendor Defined Widget] wcaps 0xf00301: Stereo Digital
[*]  Connection: 2
[*]     0x01* 0x27
[*](end collapsed section)
[/LIST]

[LIST]
[*]
[*]
[*][COLOR=brown][FONT=monospace]**ALSA Device nodes**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-----------------**[/FONT][/COLOR]
[*]
[*]total 0
[*]drwxr-xr-x 2 root root 60 Dec 10 18:24 .
[*]drwxr-xr-x 3 root root 60 Dec 10 18:24 ..
[*]lrwxrwxrwx 1 root root 15 Dec 10 18:24 pci-0000:00:1b.0 -> ../../controlC0
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Aplay/Arecord output**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------**[/FONT][/COLOR]
[*]
[*]APLAY
[*]
[*]aplay: device_list:223: no soundcards found...
[*]
[*]ARECORD
[*]
[*]arecord: device_list:223: no soundcards found...
[*]
[*][COLOR=brown][FONT=monospace]**Amixer output**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-------------**[/FONT][/COLOR]
[*]
[*][COLOR=brown][FONT=monospace]**-------Mixer controls for card 0 [Intel]**[/FONT][/COLOR]
[*]
[*]Invalid card number.
[*]Usage: amixer <options> [command]
[*]
[*]Available options:
[*]  -h,--help       this help
[*]  -c,--card N     select the card
[*]  -D,--device N   select the device, default 'default'
[*]  -d,--debug      debug mode
[*]  -n,--nocheck    do not perform range checking
[*]  -v,--version    print version of this program
[*]  -q,--quiet      be quiet
[*]  -i,--inactive   show also inactive controls
[*]  -a,--abstract L select abstraction level (none or basic)
[*]  -s,--stdin      Read and execute commands from stdin sequentially
[*]
[*]Available commands:
[*]  scontrols       show all mixer simple controls
[*]  scontents          show contents of all mixer simple controls (default command)
[*]  sset sID P      set contents for one mixer simple control
[*]  sget sID        get contents for one mixer simple control
[*]  controls        show all controls for given card
[*]  contents        show contents of all controls for given card
[*]  cset cID P      set control contents for one control
[*]  cget cID        get control contents for one control
[*]Invalid card number.
[*]Usage: amixer <options> [command]
[*]
[*]Available options:
[*]  -h,--help       this help
[*]  -c,--card N     select the card
[*]  -D,--device N   select the device, default 'default'
[*]  -d,--debug      debug mode
[*]  -n,--nocheck    do not perform range checking
[*]  -v,--version    print version of this program
[*]  -q,--quiet      be quiet
[*]  -i,--inactive   show also inactive controls
[*]  -a,--abstract L select abstraction level (none or basic)
[*]  -s,--stdin      Read and execute commands from stdin sequentially
[*]
[*]Available commands:
[*]  scontrols       show all mixer simple controls
[*]  scontents          show contents of all mixer simple controls (default command)
[*]  sset sID P      set contents for one mixer simple control
[*]  sget sID        get contents for one mixer simple control
[*]  controls        show all controls for given card
[*]  contents        show contents of all controls for given card
[*]  cset cID P      set control contents for one control
[*]  cget cID        get control contents for one control
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Alsactl output**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-------------**[/FONT][/COLOR]
[*]
[*][(following section hidden - click to display)]("javascript:showColl(2)")
[/LIST]

[LIST]
[*](end collapsed section)
[/LIST]

[LIST]
[*]
[*]
[*][COLOR=brown][FONT=monospace]**All Loaded Modules**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------------**[/FONT][/COLOR]
[*]
[*]Module
[*]nls_iso8859_1
[*]nls_cp437
[*]vfat
[*]fat
[*]radeon
[*]drm
[*]binfmt_misc
[*]ppdev
[*]usblp
[*]snd_hda_intel
[*]snd_pcm_oss
[*]snd_mixer_oss
[*]snd_pcm
[*]snd_seq_dummy
[*]snd_seq_oss
[*]snd_seq_midi
[*]snd_rawmidi
[*]snd_seq_midi_event
[*]snd_seq
[*]snd_timer
[*]iptable_filter
[*]snd_seq_device
[*]ip_tables
[*]snd
[*]soundcore
[*]x_tables
[*]snd_page_alloc
[*]lp
[*]psmouse
[*]parport
[*]dcdbas
[*]serio_raw
[*]usbhid
[*]usb_storage
[*]e1000e
[*]intel_agp
[*]agpgart
[*]
[*]
[*][COLOR=brown][FONT=monospace]**ALSA/HDA dmesg**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------------**[/FONT][/COLOR]
[*]
[*][   14.667173] ip_tables: (C) 2000-2006 Netfilter Core Team
[*][   15.689975] HDA Intel 0000:00:1b.0: setting latency timer to 64
[*][   16.039745] usb-storage: device scan complete
[/LIST]
[/FONT]


[CENTER]                     **advertising**

  [/CENTER]
        **Update the Post**

Either update this post and resubmit it with changes, or [make a new post]("http://pastebin.ca/index.php?a=n").
You may also [comment on this post]("http://pastebin.ca/cmt.php?bin_id=1710295").
		         update paste below 		[CENTER] 			!!################################ !!ALSA Information Script v 0.4.58 !!################################ !!Script ran on: Thu Dec 10 23:34:35 UTC 2009 !!Linux Distribution !!------------------ Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10" !!DMI Information !!--------------- Manufacturer: Dell Inc. Product Name: OptiPlex 760 !!Kernel Information !!------------------ Kernel release: 2.6.28-15-generic Operating System: GNU/Linux Architecture: i686 Processor: unknown SMP Enabled: Yes !!ALSA Version !!------------ Driver version: 1.0.18rc3 Library version: 1.0.21a Utilities version: 1.0.21 !!Loaded ALSA modules !!------------------- snd_hda_intel !!Sound Servers on this system !!---------------------------- No sound servers found. !!Soundcards recognised by ALSA !!----------------------------- 0 [Intel ]: HDA-Intel - HDA Intel HDA Intel at 0xfebdc000 irq 16 !!PCI Soundcards installed in the system !!-------------------------------------- 00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02) !!Advanced information - PCI Vendor/Device/Susbsystem ID's !!-------------------------------------------------------- 00:1b.0 0403: 8086:3a6e (rev 02) Subsystem: 1028:027f !!Modprobe options (Sound related) !!-------------------------------- snd-atiixp-modem: index=-2 snd-intel8x0m: index=-2 snd-via82xx-modem: index=-2 snd-usb-audio: index=-2 snd-usb-us122l: index=-2 snd-usb-usx2y: index=-2 snd-usb-caiaq: index=-2 snd-cmipci: mpu_port=0x330 fm_port=0x388 snd-pcsp: index=-2 snd-hda-intel: power_save=10 power_save_controller=N !!Loaded sound module options !!-------------------------- !!Module: snd_hda_intel bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1  enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y enable_msi : 0 id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>  index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1  model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>  position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0 power_save : 10 power_save_controller : N probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1  single_cmd : N !!HDA-Intel Codec information !!--------------------------- --startcollapse-- Codec: Analog Devices AD1984A Address: 2 Vendor Id: 0x11d4194a Subsystem Id: 0x1028027f Revision Id: 0x100400 No Modem Function Group found Default PCM: rates [0x7ff]: 8000 11025 16000 22050 32000 44100 48000 88200 96000 176400 192000 bits [0xe]: 16 20 24 formats [0x1]: PCM Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1 Default Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0 GPIO: io=3, o=0, i=0, unsolicited=1, wake=0 IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0 IO[1]: enable=0, dir=0, wake=0, sticky=0, data=1 IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0 Node 0x02 [Audio Output] wcaps 0x30211: Stereo Digital Converter: stream=0, channel=0 Digital: Digital category: 0x0 PCM: rates [0x7e0]: 44100 48000 88200 96000 176400 192000 bits [0xe]: 16 20 24 formats [0x5]: PCM AC3 Delay: 3 samples Node 0x03 [Audio Output] wcaps 0x405: Stereo Amp-Out Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0 Amp-Out vals: [0x27 0x27] Converter: stream=0, channel=0 Power: setting=D0, actual=D3 Node 0x04 [Audio Output] wcaps 0x405: Stereo Amp-Out Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0   Amp-Out vals:  [0x27 0x27]   Converter: stream=0, channel=0   Power: setting=D0, actual=D3 Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono Node 0x06 [Vendor Defined Widget] wcaps 0xf00000: Mono Node 0x07 [Audio Mixer] wcaps 0x200103: Stereo Amp-In   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-In vals:  [0x80 0x80] [0x00 0x00]   Connection: 2      0x22 0x21 Node 0x08 [Audio Input] wcaps 0x100501: Stereo   Converter: stream=0, channel=0   SDI-Select: 0   Power: setting=D0, actual=D3   Connection: 1      0x0c Node 0x09 [Audio Input] wcaps 0x100501: Stereo   Converter: stream=0, channel=0   SDI-Select: 0   Power: setting=D0, actual=D3   Connection: 1      0x0d Node 0x0a [Audio Mixer] wcaps 0x200103: Stereo Amp-In   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-In vals:  [0x80 0x80] [0x00 0x00]   Connection: 2      0x04 0x21 Node 0x0b [Audio Mixer] wcaps 0x200103: Stereo Amp-In   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-In vals:  [0x80 0x80] [0x80 0x80]   Connection: 2      0x0f 0x21 Node 0x0c [Audio Selector] wcaps 0x30010d: Stereo Amp-Out   Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1   Amp-Out vals:  [0x80 0x80]   Connection: 6      0x14* 0x15 0x16 0x20 0x25 0x17 Node 0x0d [Audio Selector] wcaps 0x30010d: Stereo Amp-Out   Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1   Amp-Out vals:  [0x80 0x80]   Connection: 6      0x14* 0x15 0x16 0x20 0x25 0x17 Node 0x0e [Audio Selector] wcaps 0x300101: Stereo   Connection: 2      0x03* 0x04 Node 0x0f [Audio Selector] wcaps 0x300101: Stereo   Connection: 2      0x03* 0x04 Node 0x10 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out   Amp-Out caps: ofs=0x0f, nsteps=0x0f, stepsize=0x0b, mute=1   Amp-Out vals:  [0x00] Node 0x11 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-Out vals:  [0x80 0x80]   Pincap 0x0000001f: OUT HP Detect Trigger ImpSense   Pin Default 0x02214040: [Jack] HP Out at Ext Front     Conn = 1/8, Color = Green     DefAssociation = 0x4, Sequence = 0x0   Pin-ctls: 0xc0: OUT HP   Unsolicited: tag=00, enabled=0   Connection: 1      0x07 Node 0x12 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-Out vals:  [0x80 0x80]   Pincap 0x0001001f: OUT HP EAPD Detect Trigger ImpSense   EAPD 0x0:   Pin Default 0x01014010: [Jack] Line Out at Ext Rear     Conn = 1/8, Color = Green     DefAssociation = 0x1, Sequence = 0x0   Pin-ctls: 0xc0: OUT HP   Unsolicited: tag=00, enabled=0   Power: setting=D0, actual=D0   Connection: 1      0x0a Node 0x13 [Pin Complex] wcaps 0x40050c: Mono Amp-Out   Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1   Amp-Out vals:  [0x00]   Pincap 0x00010010: OUT EAPD   EAPD 0x0:   Pin Default 0x991301f0: [Fixed] Speaker at Int ATAPI     Conn = ATAPI, Color = Unknown     DefAssociation = 0xf, Sequence = 0x0     Misc = NO_PRESENCE   Pin-ctls: 0x40: OUT   Power: setting=D0, actual=D0   Connection: 1      0x1f Node 0x14 [Pin Complex] wcaps 0x40008b: Stereo Amp-In   Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0   Amp-In vals:  [0x00 0x00]   Pincap 0x00003727: IN Detect Trigger ImpSense     Vref caps: HIZ 50 GRD 80 100   Pin Default 0x02a19020: [Jack] Mic at Ext Front     Conn = 1/8, Color = Pink     DefAssociation = 0x2, Sequence = 0x0   Pin-ctls: 0x24: IN VREF_80   Unsolicited: tag=00, enabled=0 Node 0x15 [Pin Complex] wcaps 0x40008b: Stereo Amp-In   Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0   Amp-In vals:  [0x00 0x00]   Pincap 0x00003727: IN Detect Trigger ImpSense     Vref caps: HIZ 50 GRD 80 100   Pin Default 0x01813030: [Jack] Line In at Ext Rear     Conn = 1/8, Color = Blue     DefAssociation = 0x3, Sequence = 0x0   Pin-ctls: 0x20: IN VREF_HIZ   Unsolicited: tag=00, enabled=0 Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-Out vals:  [0x80 0x80]   Pincap 0x00010037: IN OUT EAPD Detect Trigger ImpSense   EAPD 0x0:   Pin Default 0x413301f0: [N/A] CD at Ext Rear Conn = ATAPI, Color = Unknown DefAssociation = 0xf, Sequence = 0x0 Misc = NO_PRESENCE Pin-ctls: 0x20: IN Unsolicited: tag=00, enabled=0 Power: setting=D0, actual=D0 Connection: 1 0x0b Node 0x17 [Pin Complex] wcaps 0x40020b: Stereo Digital Amp-In Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x17, mute=0 Amp-In vals: [0x00 0x00] Pincap 0x00000020: IN Pin Default 0x41a601f0: [N/A] Mic at Ext Rear Conn = Digital, Color = Unknown DefAssociation = 0xf, Sequence = 0x0 Misc = NO_PRESENCE Pin-ctls: 0x24: IN Node 0x18 [Vendor Defined Widget] wcaps 0xf00100: Mono Connection: 1 0x06 Node 0x19 [Power Widget] wcaps 0x500500: Mono Power: setting=D0, actual=D0 Connection: 2 0x20* 0x21 Node 0x1a [Pin Complex] wcaps 0x400000: Mono Pincap 0x00000020: IN Pin Default 0x41f301f0: [N/A] Other at Ext Rear Conn = ATAPI, Color = Unknown DefAssociation = 0xf, Sequence = 0x0 Misc = NO_PRESENCE Pin-ctls: 0x20: IN Node 0x1b [Pin Complex] wcaps 0x40038d: Stereo Digital Amp-Out Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=1 Amp-Out vals: [0x27 0x27] Pincap 0x00000014: OUT Detect Pin Default 0x414501f0: [N/A] SPDIF Out at Ext Rear Conn = Optical, Color = Unknown DefAssociation = 0xf, Sequence = 0x0 Misc = NO_PRESENCE Pin-ctls: 0x00: Unsolicited: tag=00, enabled=0 Connection: 1 0x02 Node 0x1c [Pin Complex] wcaps 0x40018d: Stereo Amp-Out Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1 Amp-Out vals: [0x80 0x80] Pincap 0x00003737: IN OUT Detect Trigger ImpSense Vref caps: HIZ 50 GRD 80 100 Pin Default 0x413301f0: [N/A] CD at Ext Rear Conn = ATAPI, Color = Unknown DefAssociation = 0xf, Sequence = 0x0 Misc = NO_PRESENCE Pin-ctls: 0x24: IN VREF_80 Unsolicited: tag=00, enabled=0 Connection: 1 0x24 Node 0x1d [Vendor Defined Widget] wcaps 0xf00100: Mono Connection: 25 0x07* 0x0a 0x0b 0x0c 0x0d 0x0e 0x0f 0x11 0x12 0x13 0x14 0x15 0x16 0x19 0x1a 0x1c 0x1e 0x1f 0x20 0x21 0x22 0x23 0x24 0x25 0x26 Node 0x1e [Audio Mixer] wcaps 0x200103: Stereo Amp-In Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1 Amp-In vals: [0x80 0x80] [0x00 0x00] Connection: 2 0x0e 0x21 Node 0x1f [Audio Mixer] wcaps 0x200100: Mono Connection: 1 0x1e Node 0x20 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1 Amp-In vals: [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x97 0x97] Connection: 7 0x14 0x15 0x16 0x1a 0x25 0x03 0x04 Node 0x21 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1 Amp-Out vals: [0x80 0x80] Connection: 1 0x20 Node 0x22 [Audio Selector] wcaps 0x300101: Stereo Connection: 2 0x03* 0x04 Node 0x23 [Audio Selector] wcaps 0x300101: Stereo Connection: 2 0x03* 0x04 Node 0x24 [Audio Mixer] wcaps 0x200103: Stereo Amp-In Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1 Amp-In vals: [0x80 0x80] [0x80 0x80] Connection: 2 0x23 0x21 Node 0x25 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0 Amp-Out vals: [0x00 0x00] Connection: 1 0x1c Node 0x26 [Vendor Defined Widget] wcaps 0xf00100: Mono Connection: 3 0x14* 0x15 0x1c Node 0x27 [Vendor Defined Widget] wcaps 0xf00301: Stereo Digital Connection: 2 0x08* 0x09 Node 0x28 [Vendor Defined Widget] wcaps 0xf0030d: Stereo Digital Amp-Out Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1 Amp-Out vals: [0x80 0x80] Connection: 2 0x08* 0x09 Node 0x29 [Vendor Defined Widget] wcaps 0xf0030d: Stereo Digital Amp-Out Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1 Amp-Out vals: [0x80 0x80] Connection: 2 0x08* 0x09 Node 0x2a [Vendor Defined Widget] wcaps 0xf00301: Stereo Digital Connection: 2 0x01* 0x27 --endcollapse-- !!ALSA Device nodes !!----------------- total 0 drwxr-xr-x 2 root root 60 Dec 10 18:24 . drwxr-xr-x 3 root root 60 Dec 10 18:24 .. lrwxrwxrwx 1 root root 15 Dec 10 18:24 pci-0000:00:1b.0 -> ../../controlC0 !!Aplay/Arecord output !!------------ APLAY aplay: device_list:223: no soundcards found... ARECORD arecord: device_list:223: no soundcards found... !!Amixer output !!------------- !!-------Mixer controls for card 0 [Intel] Invalid card number. Usage: amixer <options> [command] Available options: -h,--help this help -c,--card N select the card -D,--device N select the device, default 'default' -d,--debug debug mode -n,--nocheck do not perform range checking -v,--version print version of this program -q,--quiet be quiet -i,--inactive show also inactive controls -a,--abstract L select abstraction level (none or basic) -s,--stdin Read and execute commands from stdin sequentially Available commands: scontrols show all mixer simple controls scontents show contents of all mixer simple controls (default command) sset sID P set contents for one mixer simple control sget sID get contents for one mixer simple control controls show all controls for given card contents show contents of all controls for given card cset cID P set control contents for one control cget cID get control contents for one control Invalid card number. Usage: amixer <options> [command] Available options: -h,--help this help -c,--card N select the card -D,--device N select the device, default 'default' -d,--debug debug mode -n,--nocheck do not perform range checking -v,--version print version of this program -q,--quiet be quiet -i,--inactive show also inactive controls -a,--abstract L select abstraction level (none or basic) -s,--stdin Read and execute commands from stdin sequentially Available commands: scontrols show all mixer simple controls scontents show contents of all mixer simple controls (default command) sset sID P set contents for one mixer simple control sget sID get contents for one mixer simple control controls show all controls for given card contents show contents of all controls for given card cset cID P set control contents for one control cget cID get control contents for one control !!Alsactl output !!------------- --startcollapse-- --endcollapse-- !!All Loaded Modules !!------------------ Module nls_iso8859_1 nls_cp437 vfat fat radeon drm binfmt_misc ppdev usblp snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer iptable_filter snd_seq_device ip_tables snd soundcore x_tables snd_page_alloc lp psmouse parport dcdbas serio_raw usbhid usb_storage e1000e intel_agp agpgart !!ALSA/HDA dmesg !!------------------ [ 14.667173] ip_tables: (C) 2000-2006 Netfilter Core Team [ 15.689975] HDA Intel 0000:00:1b.0: setting latency timer to 64 [ 16.039745] usb-storage: device scan complete 		 		  		
 		[/CENTER]
 		 		details of the post (optional) 		 		**Note:** Only the paste content is required, though the following information can be useful to others.
 		          		Name / Title:  Save name / title?
			Description / Question:
		Tags: *(space separated, optional)*
		Content Type: Action Script Ada Source Apache Configuration ASP Assembly (NASM) Asterisk Configuration BASH Script C Source C# Source C++ Source CSS Delphi Source Diff / Patch HTML 4.0 Strict JavaScript Java Source LISP Source Lua Source Microprocessor ASM mIRC Script Objective C Pascal Source Perl Source PHP Source PL/I Source Python Source Raw Ruby Source Scheme Source Script Log SQL Statement Visual Basic .NET Visual Basic Source XML Document 		
		Expire this post in: 	Never5 minutes10 minutes15 minutes30 minutes45 minutes1 hour2 hours4 hours8 hours12 hours1 day2 days3 days1 week2 weeks3 weeks1 month2 months3 months4 months5 months6 months1 year		 
				Encrypt this paste. Password: 
				  		

 		 		 		 				Please note that information posted here **will** expire by default in one month. If you do not want it to expire, please set the expiry time above. If it is set to expire, web search engines will not be allowed to index it prior to it expiring. Items that are not marked to expire will be indexable by search engines. Be careful with your passwords. All illegal activities will be reported and any information will be handed over to the authorities, so be good.
 

    
 [worth-right]("http://pastebin.ca/structural.php") [worth-right]("http://pastebin.ca/structural.php")
   	
[IMG]http://w.pastebin.ca/mozilla_blu.gif[/IMG]

 [W3CXHTML]("http://validator.w3.org/check?uri=referer")
 [W3CCSS]("http://jigsaw.w3.org/css-validator/")
 
services provided and written by [Stephen Olesen]("http://blog.slepp.ca/") - all layout and non-paste text copyright © 2003-2009 - lygo	 
         	     	 Feedback for Pastebin.ca[close]("http://pastebin.ca/1710295#")
Cancel

---

### Post by buffalojr on 2009-12-10
> **FalloutMan said:**
> I have the same issue but I did a little research first.  This is what I get when I do the aplay -l:
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

So ubuntu knows that theres a device but when I go into Sound Preferences and go to the Hardware tab it doesnt have ANY devices listed to configure.  My sound will work *sometimes* and I can't figure out what makes it work and not work.  When it does work everything works like normal but when it doesnt then nothing works at all.  Even reboots dont fix it. It either works or doesnt work : /  
When I mouse over the volume button on the top toolbar it says Dummy Output when sound works and doesnt work.  Under Output in sound pref it says Dummy Output and and nothing under Input even though 9.04 had the correct thing in both tabs from the getgo.  This 9.10 install is a clean install fresh from a MD5 checksum verified ISO of 32bit 9.10 that was downloaded roughly 5 days after launch.


I'm getting the same problems and it was fine last week. Must be the new upgrades that I installed this week. Haven't been able to figure what broke what yet though.

---

### Post by Tito Thomson on 2009-12-10
Same here. I installed the beta of Google Chrome for Linux and since then, no sound. Sound was fine before. 

And strangely, now Skype isn't working either. I click on it, type my password and it just disappears.

Help please.

---

### Post by buffalojr on 2009-12-10
Same here. I'm getting the dummy output for my sound. Ubuntu sees my sound card but for some reason there is now connection.

---

### Post by GuiGuy on 2009-12-13
Same here.

Ready to give up...

---

### Post by xx58 on 2009-12-14
:rolleyes:   	 	 	 	 	 	  Just go to your Hardware Drivers menu (System>Administration>Hardware Drivers)...

Select the 'Software Modem'-driver... and press Remove!

Close all your applications, and reboot your system...

---

### Post by milandinic on 2009-12-14
> **xx58 said:**
> :rolleyes:                                  Just go to your Hardware Drivers menu (System>Administration>Hardware Drivers)...

Select the 'Software Modem'-driver... and press Remove!

Close all your applications, and reboot your system...

this worked for me, thx!

---

### Post by Tricity on 2009-12-14
@sevenfactorial:

I suspect that the driver did not load, and I agree with you that a version mismatch may be the cause. The last few days, there was some confusion between the -15 and -16 versions of the kernel.

Your sound system is loaded, but do you have a file /dev/dsp  ?

I fixed a number of (different) problems by removing *all* kernel-related packages with 2.6.28-15 and reinstalling all packages that ended with 2.6.28-16-generic. I think this may work for you as well.

---

### Post by rosswmcgee on 2009-12-17
No proprietary drivers in system. 

I am trying to get a friends computer who switched to Ubuntu 9.10 on my say so to have sound, As the initial post says I have tried everything. I just need a driver for the card. Poor folks who can not afford a new computer are switching to Ubuntu but then they get this kind of problem/ not a good thing to happen.

---

### Post by Apallo on 2010-01-27
If the above solutions don't work, try downloading gamix (a GTK alsa graphical mixer) and make sure the "Mono" output is selected and has the volume up. This is what fixed it for me.

---

