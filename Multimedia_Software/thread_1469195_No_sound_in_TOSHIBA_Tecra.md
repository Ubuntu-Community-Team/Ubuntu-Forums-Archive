---
title: "No sound in TOSHIBA Tecra"
date: 2010-05-02
forum: Multimedia Software
---

### Post by Quencey on 2010-05-02
Hi guys...

I am using TOSHIBA Tecra A8 notebook and i have install Ubuntu 10.04. However sound is not working. Is there any sound drivers for TOSHIBA Tecra A8 and it's version is : PTA83E-01D023AR. Please send your ideas....

Thank you very much...
Quencey.

---

### Post by lidex on 2010-05-02
First. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

Next. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by Quencey on 2010-05-05
> **lidex said:**
> First. Check your levels in alsamixer.
```
 alsamixer 
```Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

Next. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

**Here these are the out puts i got.**

Quencey@Quencey-lap:~$ uname -a
Linux Quencey-lap 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
Quencey@Quencey-lap:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Quencey@Quencey-lap:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
Quencey@Quencey-lap:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC262

==> /proc/asound/card0/codec#1 <==
Codec: LSI Si3054
Quencey@Quencey-lap:~$ 

**Thank you for helping me..**

---

### Post by Yellow Pasque on 2010-05-05
In terminal:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
This should bring up a text file. At the end of the file, copy/paste this line:
```
options snd-hda-intel enable=1 index=0 model=basic
```
Save, quit, and reboot. See if sound works.

---

### Post by Quencey on 2010-05-11
Still the problem is remaining. No sound  ](*,)..!!!!

---

### Post by lidex on 2010-05-11
Remove the previous line from alsa-base.conf and replace it with this:
```
options snd-hda-intel model=toshiba
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by Quencey on 2010-06-15
Hi guys,

I have done what you ask me to do, but still the problem is exist. No Sound in TOSHIBA Tecra in Ubuntu 10.04. :-k

---

### Post by 2edgesword on 2010-06-25
I have the same system, the same problem and nothing I've tried so far has restored sound.
 
Does anyone with this system and have sound running Ubuntu 10.04?

---

### Post by lidex on 2010-06-25
Some other model options to try:
```
options snd-hda-intel model=toshiba-s06
options snd-hda-intel model=toshiba-rx1
options snd-hda-intel model=auto
```
Remember to only use one line at a time and reboot for changes to take effect.

---

### Post by Bill Sempf on 2010-08-03
I hate to be a thread necro but I have the same problem, on a slightly older machine.  Toshiba Tecra M7, and no sound.  Tried the whole thread, still no sound.  Learned a lot though.

Does anyone have a Tecra M series with working sound out there?  would you mind posting your configuration?

S

---

### Post by lidex on 2010-08-05
> **Bill Sempf said:**
> I hate to be a thread necro but I have the same problem, on a slightly older machine.  Toshiba Tecra M7, and no sound.  Tried the whole thread, still no sound.  Learned a lot though.

Does anyone have a Tecra M series with working sound out there?  would you mind posting your configuration?

S

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by bad.skipper on 2010-09-23
Hi, I have the same problem with Toshiba Tecra A8:

```

!################################ !!ALSA Information Script v 0.4.59 !!################################  !!Script ran on: Thu Sep 30 20:12:45 UTC 2010   !!Linux Distribution !!------------------  Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"   !!DMI Information !!---------------  Manufacturer:      TOSHIBA Product Name:      TECRA A8   !!Kernel Information !!------------------  Kernel release:    2.6.32-25-generic Operating System:  GNU/Linux Architecture:      i686 Processor:         unknown SMP Enabled:       Yes   !!ALSA Version !!------------  Driver version:     1.0.23 Library version:    1.0.23 Utilities version:  1.0.22   !!Loaded ALSA modules !!-------------------  snd_hda_intel   !!Sound Servers on this system !!----------------------------  Pulseaudio:       Installed - Yes (/usr/bin/pulseaudio)       Running - Yes  ESound Daemon:       Installed - Yes (/usr/bin/esd)       Running - No   !!Soundcards recognised by ALSA !!-----------------------------   0 [Intel          ]: HDA-Intel - HDA Intel                       HDA Intel at 0x6a080000 irq 28   !!PCI Soundcards installed in the system !!--------------------------------------  00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)   !!Advanced information - PCI Vendor/Device/Susbsystem ID's !!--------------------------------------------------------  00:1b.0 0403: 8086:27d8 (rev 02)     Subsystem: 1179:0001   !!Modprobe options (Sound related) !!--------------------------------  snd-atiixp-modem: index=-2 snd-intel8x0m: index=-2 snd-via82xx-modem: index=-2 snd-usb-audio: index=-2 snd-usb-us122l: index=-2 snd-usb-usx2y: index=-2 snd-usb-caiaq: index=-2 snd-cmipci: mpu_port=0x330 fm_port=0x388 snd-pcsp: index=-1 snd-hda-intel: model=sony-assamd   !!Loaded sound module options !!--------------------------  !!Module: snd_hda_intel     bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1     beep_mode : 1,1,1,1,1,1,1,1     enable : Y,Y,Y,Y,Y,Y,Y,Y     enable_msi : -1     id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>     index : -1,-1,-1,-1,-1,-1,-1,-1     model : sony-assamd,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>     patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>     position_fix : 0,0,0,0,0,0,0,0     power_save : 0     power_save_controller : Y     probe_mask : -1,-1,-1,-1,-1,-1,-1,-1     probe_only : 0,0,0,0,0,0,0,0     single_cmd : N   !!HDA-Intel Codec information !!--------------------------- --startcollapse--  Codec: Realtek ALC262 Address: 0 Function Id: 0x1 Vendor Id: 0x10ec0262 Subsystem Id: 0x11790580 Revision Id: 0x100100 No Modem Function Group found Default PCM:     rates [0x560]: 44100 48000 96000 192000     bits [0xe]: 16 20 24     formats [0x1]: PCM Default Amp-In caps: N/A Default Amp-Out caps: N/A GPIO: io=4, o=0, i=0, unsolicited=1, wake=0   IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0   IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0   IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0   IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0 Node 0x02 [Audio Output] wcaps 0x11: Stereo   Device: name="ALC262 Analog", type="Audio", device=0   Converter: stream=5, channel=0   PCM:     rates [0x560]: 44100 48000 96000 192000     bits [0xe]: 16 20 24     formats [0x1]: PCM Node 0x03 [Audio Output] wcaps 0x11: Stereo   Converter: stream=0, channel=0   PCM:     rates [0x560]: 44100 48000 96000 192000     bits [0xe]: 16 20 24     formats [0x1]: PCM Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital   Converter: stream=0, channel=0   Digital:   Digital category: 0x0   PCM:     rates [0x560]: 44100 48000 96000 192000     bits [0x1e]: 16 20 24 32     formats [0x1]: PCM Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In   Control: name="Capture Switch", index=0, device=0   Control: name="Capture Volume", index=0, device=0   Device: name="ALC262 Analog", type="Audio", device=0   Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1   Amp-In vals:  [0x91 0x91]   Converter: stream=0, channel=0   SDI-Select: 0   PCM:     rates [0x160]: 44100 48000 96000     bits [0x6]: 16 20     formats [0x1]: PCM   Connection: 1      0x24 Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In   Control: name="Capture Switch", index=1, device=0   Control: name="Capture Volume", index=1, device=0   Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1   Amp-In vals:  [0x94 0x94]   Converter: stream=0, channel=0   SDI-Select: 0   PCM:     rates [0x160]: 44100 48000 96000     bits [0x6]: 16 20     formats [0x1]: PCM   Connection: 1      0x23 Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In   Control: name="Capture Switch", index=2, device=0   Control: name="Capture Volume", index=2, device=0   Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1   Amp-In vals:  [0x94 0x94]   Converter: stream=0, channel=0   SDI-Select: 0   PCM:     rates [0x160]: 44100 48000 96000     bits [0x6]: 16 20     formats [0x1]: PCM   Connection: 1      0x22 Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital   Converter: stream=0, channel=0   SDI-Select: 0   Digital:   Digital category: 0x0   PCM:     rates [0x560]: 44100 48000 96000 192000     bits [0x1e]: 16 20 24 32     formats [0x1]: PCM   Unsolicited: tag=00, enabled=0   Connection: 1      0x1f Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In   Control: name="Mic Playback Volume", index=0, device=0     ControlAmp: chs=3, dir=In, idx=0, ofs=0   Control: name="Mic Playback Switch", index=0, device=0     ControlAmp: chs=3, dir=In, idx=0, ofs=0   Control: name="ATAPI Mic Playback Volume", index=0, device=0     ControlAmp: chs=3, dir=In, idx=1, ofs=0   Control: name="ATAPI Mic Playback Switch", index=0, device=0     ControlAmp: chs=3, dir=In, idx=1, ofs=0   Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1   Amp-In vals:  [0x11 0x11] [0x12 0x12] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x97 0x97] [0x97 0x97]   Connection: 8      0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out   Control: name="Master Playback Volume", index=0, device=0     ControlAmp: chs=3, dir=Out, idx=0, ofs=0   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-In vals:  [0x00 0x00] [0x00 0x00]   Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0   Amp-Out vals:  [0x17 0x17]   Connection: 2      0x02 0x0b Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-In vals:  [0x00 0x00] [0x00 0x00]   Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0   Amp-Out vals:  [0x00 0x00]   Connection: 2      0x03 0x0b Node 0x0e [Audio Mixer] wcaps 0x20010e: Mono Amp-In Amp-Out   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-In vals:  [0x00] [0x00]   Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0   Amp-Out vals:  [0x00]   Connection: 2      0x02 0x0b Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out   Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0   Amp-In vals:  [0x00 0x00]   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-Out vals:  [0x00 0x00]   Pincap 0x0000003e: IN OUT HP Detect Trigger   Pin Default 0x90170110: [Fixed] Speaker at Int N/A     Conn = Analog, Color = Unknown     DefAssociation = 0x1, Sequence = 0x0     Misc = NO_PRESENCE   Pin-ctls: 0xc0: OUT HP   Unsolicited: tag=00, enabled=0   Connection: 2      0x0c* 0x0d Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out   Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0   Amp-In vals:  [0x00 0x00]   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-Out vals:  [0x00 0x00]   Pincap 0x0000003e: IN OUT HP Detect Trigger   Pin Default 0x0221101f: [Jack] HP Out at Ext Front     Conn = 1/8, Color = Black     DefAssociation = 0x1, Sequence = 0xf   Pin-ctls: 0xc0: OUT HP   Unsolicited: tag=04, enabled=1   Connection: 2      0x0c* 0x0d Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-Out vals:  [0x80]   Pincap 0x00000010: OUT   Pin Default 0x40f000f6: [N/A] Other at Ext N/A     Conn = Unknown, Color = Unknown     DefAssociation = 0xf, Sequence = 0x6   Pin-ctls: 0x40: OUT   Connection: 1      0x0e Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out   Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0   Amp-In vals:  [0x00 0x00]   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-Out vals:  [0x80 0x80]   Pincap 0x0000173e: IN OUT HP Detect Trigger     Vref caps: HIZ 50 GRD 80   Pin Default 0x02a110f0: [Jack] Mic at Ext Front     Conn = 1/8, Color = Black     DefAssociation = 0xf, Sequence = 0x0   Pin-ctls: 0x24: IN VREF_80   Unsolicited: tag=00, enabled=0   Connection: 2      0x0c* 0x0d Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out   Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0   Amp-In vals:  [0x00 0x00]   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-Out vals:  [0x80 0x80]   Pincap 0x0000173e: IN OUT HP Detect Trigger     Vref caps: HIZ 50 GRD 80   Pin Default 0x40f000f8: [N/A] Other at Ext N/A     Conn = Unknown, Color = Unknown     DefAssociation = 0xf, Sequence = 0x8   Pin-ctls: 0x24: IN VREF_80   Unsolicited: tag=00, enabled=0   Connection: 2      0x0c* 0x0d Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out   Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0   Amp-In vals:  [0x00 0x00]   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-Out vals:  [0x80 0x80]   Pincap 0x0000173e: IN OUT HP Detect Trigger     Vref caps: HIZ 50 GRD 80   Pin Default 0x218411f0: [Jack] Line In at Sep Rear     Conn = RCA, Color = Black     DefAssociation = 0xf, Sequence = 0x0     Misc = NO_PRESENCE   Pin-ctls: 0x20: IN VREF_HIZ   Unsolicited: tag=00, enabled=0   Connection: 2      0x0c* 0x0d Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out   Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0   Amp-In vals:  [0x00 0x00]   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-Out vals:  [0x80 0x80]   Pincap 0x0000173e: IN OUT HP Detect Trigger     Vref caps: HIZ 50 GRD 80   Pin Default 0x210411f0: [Jack] Line Out at Sep Rear     Conn = RCA, Color = Black     DefAssociation = 0xf, Sequence = 0x0     Misc = NO_PRESENCE   Pin-ctls: 0x20: IN VREF_HIZ   Unsolicited: tag=00, enabled=0   Connection: 2      0x0c* 0x0d Node 0x1c [Pin Complex] wcaps 0x400001: Stereo   Pincap 0x00000020: IN   Pin Default 0x40f000fb: [N/A] Other at Ext N/A     Conn = Unknown, Color = Unknown     DefAssociation = 0xf, Sequence = 0xb   Pin-ctls: 0x00: Node 0x1d [Pin Complex] wcaps 0x400000: Mono   Pincap 0x00000020: IN   Pin Default 0x598301f0: [N/A] Line In at Int ATAPI     Conn = ATAPI, Color = Unknown     DefAssociation = 0xf, Sequence = 0x0     Misc = NO_PRESENCE   Pin-ctls: 0x00: Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital   Pincap 0x00000010: OUT   Pin Default 0x40f000fd: [N/A] Other at Ext N/A     Conn = Unknown, Color = Unknown     DefAssociation = 0xf, Sequence = 0xd   Pin-ctls: 0x00:   Unsolicited: tag=00, enabled=0   Connection: 1      0x06 Node 0x1f [Pin Complex] wcaps 0x400280: Mono Digital   Pincap 0x00000020: IN   Pin Default 0x40f000fe: [N/A] Other at Ext N/A     Conn = Unknown, Color = Unknown     DefAssociation = 0xf, Sequence = 0xe   Pin-ctls: 0x00:   Unsolicited: tag=00, enabled=0 Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono   Processing caps: benign=0, ncoeff=17 Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono   Volume-Knob: delta=0, steps=32, direct=0, val=64   Unsolicited: tag=00, enabled=0   Connection: 0 Node 0x22 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out   Control: name="Input Source", index=2, device=0   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]   Amp-Out caps: N/A   Amp-Out vals:  [0x00 0x00]   Connection: 9      0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b Node 0x23 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out   Control: name="Input Source", index=1, device=0   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]   Amp-Out caps: N/A   Amp-Out vals:  [0x00 0x00]   Connection: 9      0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b Node 0x24 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out   Control: name="Input Source", index=0, device=0   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1   Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]   Amp-Out caps: N/A   Amp-Out vals:  [0x00 0x00]   Connection: 9      0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b Codec: LSI Si3054 Address: 1 Function Id: 0x2 Vendor Id: 0x11c13026 Subsystem Id: 0x11790001 Revision Id: 0x100700 Modem Function Group: 0x1 --endcollapse--   !!ALSA Device nodes !!-----------------  crw-rw----  1 root audio 116,  0 Sep 30 22:08 /dev/snd/controlC0 crw-rw----  1 root audio 116,  4 Sep 30 22:08 /dev/snd/hwC0D0 crw-rw----  1 root audio 116,  5 Sep 30 22:08 /dev/snd/hwC0D1 crw-rw----  1 root audio 116, 24 Sep 30 22:09 /dev/snd/pcmC0D0c crw-rw----  1 root audio 116, 16 Sep 30 22:11 /dev/snd/pcmC0D0p crw-rw----  1 root audio 116, 30 Sep 30 22:08 /dev/snd/pcmC0D6c crw-rw----  1 root audio 116, 22 Sep 30 22:08 /dev/snd/pcmC0D6p crw-rw----  1 root audio 116,  1 Sep 30 22:08 /dev/snd/seq crw-rw----  1 root audio 116, 33 Sep 30 22:08 /dev/snd/timer  /dev/snd/by-path: total 0 drwxr-xr-x 2 root root  60 Sep 30 22:08 . drwxr-xr-x 3 root root 240 Sep 30 22:08 .. lrwxrwxrwx 1 root root  12 Sep 30 22:08 pci-0000:00:1b.0 -> ../controlC0   !!Aplay/Arecord output !!------------  APLAY  **** List of PLAYBACK Hardware Devices **** card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]   Subdevices: 0/1   Subdevice #0: subdevice #0 card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]   Subdevices: 1/1   Subdevice #0: subdevice #0  ARECORD  **** List of CAPTURE Hardware Devices **** card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]   Subdevices: 1/1   Subdevice #0: subdevice #0 card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]   Subdevices: 1/1   Subdevice #0: subdevice #0  !!Amixer output !!-------------  !!-------Mixer controls for card 0 [Intel]  Card hw:0 'Intel'/'HDA Intel at 0x6a080000 irq 28'   Mixer name    : 'Realtek ALC262'   Components    : 'HDA:10ec0262,11790580,00100100 HDA:11c13026,11790001,00100700'   Controls      : 18   Simple ctrls  : 12 Simple mixer control 'Master',0   Capabilities: pvolume pswitch pswitch-joined penum   Playback channels: Front Left - Front Right   Limits: Playback 0 - 31   Mono:   Front Left: Playback 23 [74%] [-12.00dB] [on]   Front Right: Playback 23 [74%] [-12.00dB] [on] Simple mixer control 'PCM',0   Capabilities: pvolume penum   Playback channels: Front Left - Front Right   Limits: Playback 0 - 255   Mono:   Front Left: Playback 250 [98%] [-1.00dB]   Front Right: Playback 250 [98%] [-1.00dB] Simple mixer control 'Mic',0   Capabilities: pvolume pswitch penum   Playback channels: Front Left - Front Right   Limits: Playback 0 - 31   Mono:   Front Left: Playback 17 [55%] [-9.00dB] [on]   Front Right: Playback 17 [55%] [-9.00dB] [on] Simple mixer control 'Capture',0   Capabilities: cvolume cswitch penum   Capture channels: Front Left - Front Right   Limits: Capture 0 - 31   Front Left: Capture 17 [55%] [13.50dB] [off]   Front Right: Capture 17 [55%] [13.50dB] [off] Simple mixer control 'Capture',1   Capabilities: cvolume cswitch penum   Capture channels: Front Left - Front Right   Limits: Capture 0 - 31   Front Left: Capture 20 [65%] [18.00dB] [off]   Front Right: Capture 20 [65%] [18.00dB] [off] Simple mixer control 'Capture',2   Capabilities: cvolume cswitch penum   Capture channels: Front Left - Front Right   Limits: Capture 0 - 31   Front Left: Capture 20 [65%] [18.00dB] [off]   Front Right: Capture 20 [65%] [18.00dB] [off] Simple mixer control 'ATAPI Mic',0   Capabilities: pvolume pswitch penum   Playback channels: Front Left - Front Right   Limits: Playback 0 - 31   Mono:   Front Left: Playback 18 [58%] [-7.50dB] [on]   Front Right: Playback 18 [58%] [-7.50dB] [on] Simple mixer control 'Caller ID',0   Capabilities: pswitch pswitch-joined penum   Playback channels: Mono   Mono: Playback [off] Simple mixer control 'Input Source',0   Capabilities: cenum   Items: 'Mic' 'Front Mic' 'Line' 'CD'   Item0: 'Mic' Simple mixer control 'Input Source',1   Capabilities: cenum   Items: 'Mic' 'Front Mic' 'Line' 'CD'   Item0: 'Mic' Simple mixer control 'Input Source',2   Capabilities: cenum   Items: 'Mic' 'Front Mic' 'Line' 'CD'   Item0: 'Mic' Simple mixer control 'Off-hook',0   Capabilities: pswitch pswitch-joined penum   Playback channels: Mono   Mono: Playback [off]   !!Alsactl output !!-------------  --startcollapse-- state.Intel {     control.1 {         comment.access 'read write'         comment.type INTEGER         comment.count 2         comment.range '0 - 31'         comment.dbmin -4650         comment.dbmax 0         iface MIXER         name 'Master Playback Volume'         value.0 23         value.1 23     }     control.2 {         comment.access 'read write'         comment.type BOOLEAN         comment.count 1         iface MIXER         name 'Master Playback Switch'         value true     }     control.3 {         comment.access 'read write'         comment.type INTEGER         comment.count 2         comment.range '0 - 31'         comment.dbmin -3450         comment.dbmax 1200         iface MIXER         name 'Mic Playback Volume'         value.0 17         value.1 17     }     control.4 {         comment.access 'read write'         comment.type BOOLEAN         comment.count 2         iface MIXER         name 'Mic Playback Switch'         value.0 true         value.1 true     }     control.5 {         comment.access 'read write'         comment.type INTEGER         comment.count 2         comment.range '0 - 31'         comment.dbmin -3450         comment.dbmax 1200         iface MIXER         name 'ATAPI Mic Playback Volume'         value.0 18         value.1 18     }     control.6 {         comment.access 'read write'         comment.type BOOLEAN         comment.count 2         iface MIXER         name 'ATAPI Mic Playback Switch'         value.0 true         value.1 true     }     control.7 {         comment.access 'read write'         comment.type BOOLEAN         comment.count 2         iface MIXER         name 'Capture Switch'         value.0 false         value.1 false     }     control.8 {         comment.access 'read write'         comment.type BOOLEAN         comment.count 2         iface MIXER         name 'Capture Switch'         index 1         value.0 false         value.1 false     }     control.9 {         comment.access 'read write'         comment.type BOOLEAN         comment.count 2         iface MIXER         name 'Capture Switch'         index 2         value.0 false         value.1 false     }     control.10 {         comment.access 'read write'         comment.type INTEGER         comment.count 2         comment.range '0 - 31'         comment.dbmin -1200         comment.dbmax 3450         iface MIXER         name 'Capture Volume'         value.0 17         value.1 17     }     control.11 {         comment.access 'read write'         comment.type INTEGER         comment.count 2         comment.range '0 - 31'         comment.dbmin -1200         comment.dbmax 3450         iface MIXER         name 'Capture Volume'         index 1         value.0 20         value.1 20     }     control.12 {         comment.access 'read write'         comment.type INTEGER         comment.count 2         comment.range '0 - 31'         comment.dbmin -1200         comment.dbmax 3450         iface MIXER         name 'Capture Volume'         index 2         value.0 20         value.1 20     }     control.13 {         comment.access 'read write'         comment.type ENUMERATED         comment.count 1         comment.item.0 Mic         comment.item.1 'Front Mic'         comment.item.2 Line         comment.item.3 CD         iface MIXER         name 'Input Source'         value Mic     }     control.14 {         comment.access 'read write'         comment.type ENUMERATED         comment.count 1         comment.item.0 Mic         comment.item.1 'Front Mic'         comment.item.2 Line         comment.item.3 CD         iface MIXER         name 'Input Source'         index 1         value Mic     }     control.15 {         comment.access 'read write'         comment.type ENUMERATED         comment.count 1         comment.item.0 Mic         comment.item.1 'Front Mic'         comment.item.2 Line         comment.item.3 CD         iface MIXER         name 'Input Source'         index 2         value Mic     }     control.16 {         comment.access 'read write'         comment.type BOOLEAN         comment.count 1         iface MIXER         name 'Off-hook Switch'         value false     }     control.17 {         comment.access 'read write'         comment.type BOOLEAN         comment.count 1         iface MIXER         name 'Caller ID Switch'         value false     }     control.18 {         comment.access 'read write user'         comment.type INTEGER         comment.count 2         comment.range '0 - 255'         comment.tlv '0000000100000008ffffec1400000014'         comment.dbmin -5100         comment.dbmax 0         iface MIXER         name 'PCM Playback Volume'         value.0 250         value.1 250     } } --endcollapse--   !!All Loaded Modules !!------------------  Module xt_limit xt_tcpudp ipt_LOG ipt_MASQUERADE xt_DSCP ipt_REJECT nf_conntrack_irc nf_conntrack_ftp xt_state aes_i586 aes_generic rfcomm binfmt_misc lp sco bridge stp bnep l2cap vboxnetadp vboxnetflt vboxdrv btusb bluetooth joydev snd_hda_codec_si3054 snd_hda_codec_realtek fbcon tileblit font bitblit softcursor vga16fb vgastate iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 iptable_mangle iptable_filter ip_tables x_tables pcmcia arc4 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event iwl3945 snd_seq iwlcore ppdev i915 drm_kms_helper snd_timer snd_seq_device mac80211 parport_pc sdhci_pci yenta_socket rsrc_nonstatic intel_agp drm i2c_algo_bit parport psmouse serio_raw toshiba_acpi sdhci led_class cfg80211 pcmcia_core agpgart video output snd soundcore snd_page_alloc ohci1394 ieee1394 e1000e   !!Sysfs Files !!-----------  /sys/class/sound/hwC0D0/init_pin_configs: 0x14 0x90170110 0x15 0x0221101f 0x16 0x40f000f6 0x18 0x02a110f0 0x19 0x40f000f8 0x1a 0x218411f0 0x1b 0x210411f0 0x1c 0x40f000fb 0x1d 0x598301f0 0x1e 0x40f000fd 0x1f 0x40f000fe  /sys/class/sound/hwC0D0/driver_pin_configs:  /sys/class/sound/hwC0D0/user_pin_configs:  /sys/class/sound/hwC0D0/init_verbs:  /sys/class/sound/hwC0D1/init_pin_configs:  /sys/class/sound/hwC0D1/driver_pin_configs:  /sys/class/sound/hwC0D1/user_pin_configs:  /sys/class/sound/hwC0D1/init_verbs:   !!ALSA/HDA dmesg !!------------------  [   15.135548] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0 [   15.135653] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0 [   15.135690] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0 [   15.135696] HDA Intel 0000:00:1b.0: enabling device (0000 -> 0002) [   15.135704]   alloc irq_desc for 22 on node -1 [   15.135706]   alloc kstat_irqs on node -1 [   15.135714] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 [   15.135753]   alloc irq_desc for 28 on node -1 [   15.135755]   alloc kstat_irqs on node -1 [   15.135765] HDA Intel 0000:00:1b.0: irq 28 for MSI/MSI-X [   15.135797] HDA Intel 0000:00:1b.0: setting latency timer to 64 [   15.141972] vga16fb: initializing -- [   15.141982] vga16fb: not registering due to another framebuffer present [   15.180836] hda_codec: ALC262: SKU not ready 0x598301f0 [   15.180979] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6 [   15.269180] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7

```

---

### Post by lkjoel on 2010-09-24
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by lidex on 2010-09-24
*Bad Skipper:*
Please edit that previous post - I can't make anything of it. Run the script again and enter Y when prompted to upload. Then post the **link **given in place of the whole content of that text.

---

