---
title: "Suffering in silence"
date: 2011-01-03
forum: Multimedia Software
---

### Post by Sunships on 2011-01-03
Hi all,

I installed 10.10 on my machine a few months ago and everything was great. However, as of one month ago, every so often when I boot up my computer I get no sound in Ubuntu. This is not an easily reproducible error, as far as I can tell, but is a pain to fix. The previous times this happened I messed around, tried some commands shown in other help threads, and then eventually re-adjusted the "Profile" setting for the output devices in the "Sound Preferences" utility, which brought back the sound. I have never conclusively been able to determine the source of the problem, or how to resolve it. Now it is happening again and I have been unable to restore the sound with my primitive methods.

I just came back to the tiny village where I live to be near my workplace, and am missing my family - I just want to eat my dinner and watch some Buzzcocks with sound* - can anyone help please? Ideally I'd like to identify the source of the problem, fix it, and make sure it does not happen again.

During my travels of the forums I came across a troubleshooting script thing which I ran. The output, if it is of any use, is located here: [http://www.alsa-project.org/db/?f=e2f65cda34b24234d3172b0d7e04879306032f42](http://www.alsa-project.org/db/?f=e2f65cda34b24234d3172b0d7e04879306032f42) 

Thank you for reading!



*Alright, this is a bit melodramatic, but the alternative is booting up in Windows, and no-one wants to see that happen, right? Right?? :p

---

### Post by Sunships on 2011-01-03
I do hear the characteristic crackle and pop of the speakers doing something, every now and again, or if I change the sound device profile settings...but no hint of any proper sound.

---

### Post by Sunships on 2011-01-03
Alright, I bumbled around the Comprehensive Sound Guide and came across this fix:

"Adding the current user to the audio group


A very common cause for a user to not have sound is not having his/her username in the /etc/group."

Instead of: 
```
audio:x:29:[username]
```
I had

```
audio:x:29:pulse
```

I amended this as per the instructions, rebooted, and sound is working once more. I am still uncertain if I have managed to fix the sound or if it has randomly fixed itself as it has done in the past, only to fail again at a later date. If it does so, I will resurrect this thread.

---

### Post by Sunships on 2011-01-19
So...the problem has occurred once more.

Although /etc/group contains the line:

```
audio:x:29:[username]
```

my sound has failed once more. I tried deleting the username from this line in /etc/group so it read:

```
audio:x:29:
```

and this had no effect. I rebooted, and there still wasn't any sound, and when I checked out /etc/group the line had been altered to:

```
audio:x:29:w
```

I edited the line back to:

```
audio:x:29:[username]
```

and rebooted once more, but still no sound. Can anyone please help? I depend on sound for watching TV, listening to music, and generally not going mad.

Thanks!!

---

### Post by Sunships on 2011-01-19
I installed some updates this morning...maybe a file that gets infrequently updated is the source of my problems?

---

### Post by Sunships on 2011-01-19
And randomly enough, after a few hours logged into Windows, after a hopeful reboot the sound in Ubuntu is now working again. 

I ran the alsa-info script to get an idea of what a working system looks like. Next time this happens I'll do it again and compare the too.

```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```

Apologies for my unstoppable (post) length.

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Wed Jan 19 23:13:02 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name
Product Version:   System Version


!!Kernel Information
!!------------------

Kernel release:    2.6.35-24-generic
Operating System:  GNU/Linux
Architecture:      x86_64
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

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfbff8000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe87c000 irq 19


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:00.1 Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383 (rev 40)
	Subsystem: 1043:841b
--
01:00.1 0403: 10de:0beb (rev a1)
	Subsystem: 1462:2322


!!Modprobe options (Sound related)
!!--------------------------------

snd-snd_hda_intel: index=0
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
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
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

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
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

Codec: Realtek ALC892
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0892
Subsystem Id: 0x1043841b
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC892 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Surround Playback Volume", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=5, channel=2
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x30]
  Converter: stream=5, channel=4
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x90 0x90]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC892 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0xae 0xae]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100711: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Rear Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Rear Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Surround Playback Switch", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=In, idx=0, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC892 Digital", type="SPDIF", device=1
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x99430140: [Fixed] SPDIF Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x4, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003e: IN OUT HP EAPD Detect Trigger
  EAPD 0x2: EAPD
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Rear Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19850: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19c60: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x6, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181305f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x5, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001373e: IN OUT HP EAPD Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  EAPD 0x2: EAPD
  Pin Default 0x02214c20: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f 0x26*
Node 0x1c [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4005e601: [N/A] Line Out at Ext N/A
    Conn = Optical, Color = White
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x01456130: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Orange
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400681: Stereo Digital
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=24
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 12
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x26 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x25 0x0b
Codec: Nvidia GPU 12 HDMI/DP
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de0012
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=6, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GPU 12 HDMI/DP
Address: 1
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de0012
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Device: name="HDMI 0", type="HDMI", device=7
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GPU 12 HDMI/DP
Address: 2
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de0012
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=2, device=0
  Control: name="IEC958 Playback Pro Mask", index=2, device=0
  Control: name="IEC958 Playback Default", index=2, device=0
  Control: name="IEC958 Playback Switch", index=2, device=0
  Device: name="HDMI 0", type="HDMI", device=8
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GPU 12 HDMI/DP
Address: 3
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de0012
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=3, device=0
  Control: name="IEC958 Playback Pro Mask", index=3, device=0
  Control: name="IEC958 Playback Default", index=3, device=0
  Control: name="IEC958 Playback Switch", index=3, device=0
  Device: name="HDMI 0", type="HDMI", device=9
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  6 Jan 19 23:04 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 15 Jan 19 23:04 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  5 Jan 19 23:04 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 14 Jan 19 23:04 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116, 13 Jan 19 23:04 /dev/snd/hwC1D1
crw-rw----+ 1 root audio 116, 12 Jan 19 23:04 /dev/snd/hwC1D2
crw-rw----+ 1 root audio 116, 11 Jan 19 23:04 /dev/snd/hwC1D3
crw-rw----+ 1 root audio 116,  4 Jan 19 23:04 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  3 Jan 19 23:05 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  2 Jan 19 23:04 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 10 Jan 19 23:04 /dev/snd/pcmC1D3p
crw-rw----+ 1 root audio 116,  9 Jan 19 23:04 /dev/snd/pcmC1D7p
crw-rw----+ 1 root audio 116,  8 Jan 19 23:04 /dev/snd/pcmC1D8p
crw-rw----+ 1 root audio 116,  7 Jan 19 23:04 /dev/snd/pcmC1D9p
crw-rw----+ 1 root audio 116,  1 Jan 19 23:04 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jan 19 23:04 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Jan 19 23:04 .
drwxr-xr-x 3 root root 380 Jan 19 23:04 ..
lrwxrwxrwx 1 root root  12 Jan 19 23:04 pci-0000:00:14.2 -> ../controlC0
lrwxrwxrwx 1 root root  12 Jan 19 23:04 pci-0000:01:00.1 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0xfbff8000 irq 16'
  Mixer name	: 'Realtek ALC892'
  Components	: 'HDA:10ec0892,1043841b,00100302'
  Controls      : 32
  Simple ctrls  : 18
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Surround',1
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 48 [75%] [-16.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 46 [100%] [30.00dB] [off]
  Front Right: Capture 46 [100%] [30.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 16 [35%] [0.00dB] [off]
  Front Right: Capture 16 [35%] [0.00dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Rear Mic' 'Front Mic' 'Line'
  Item0: 'Line'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Rear Mic' 'Front Mic' 'Line'
  Item0: 'Line'
Simple mixer control 'Rear Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Rear Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]

!!-------Mixer controls for card 1 [NVidia]

Card hw:1 'NVidia'/'HDA NVidia at 0xfe87c000 irq 19'
  Mixer name	: 'Nvidia GPU 12 HDMI/DP'
  Components	: 'HDA:10de0012,10de0101,00100100'
  Controls      : 16
  Simple ctrls  : 4
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',3
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.SB {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 64
		value.1 64
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
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		index 1
		value.0 64
		value.1 64
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		index 1
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Center Playback Volume'
		value 64
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'LFE Playback Volume'
		value 48
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value true
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value true
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 64
		value.1 64
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.11 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Rear Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Rear Mic Playback Switch'
		value.0 true
		value.1 true
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Front Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 true
		value.1 true
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Rear Mic Boost Volume'
		value.0 0
		value.1 0
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Front Mic Boost Volume'
		value.0 0
		value.1 0
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 46'
		comment.dbmin -1600
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		value.0 46
		value.1 46
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 46'
		comment.dbmin -1600
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 16
		value.1 16
	}
	control.23 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Rear Mic'
		comment.item.1 'Front Mic'
		comment.item.2 Line
		iface MIXER
		name 'Input Source'
		value Line
	}
	control.24 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Rear Mic'
		comment.item.1 'Front Mic'
		comment.item.2 Line
		iface MIXER
		name 'Input Source'
		index 1
		value Line
	}
	control.25 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.26 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.27 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.29 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.30 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 64
	}
	control.31 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.32 {
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
state.NVidia {
	control.1 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.2 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.3 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.5 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 1
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.6 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 1
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.7 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		index 1
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		index 1
		value true
	}
	control.9 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 2
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.10 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 2
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.11 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		index 2
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		index 2
		value true
	}
	control.13 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 3
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.14 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 3
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.15 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		index 3
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		index 3
		value true
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
dm_crypt
snd_hda_codec_hdmi
binfmt_misc
vboxnetadp
vboxnetflt
vboxdrv
snd_hda_codec_realtek
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
nvidia
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
ppdev
snd_seq_device
edac_core
joydev
parport_pc
psmouse
i2c_piix4
hid_drff
ff_memless
asus_atk0110
serio_raw
snd
edac_mce_amd
xhci_hcd
k10temp
soundcore
snd_page_alloc
lp
parport
dm_raid45
xor
usbhid
hid
firewire_ohci
firewire_core
crc_itu_t
ahci
libahci
pata_via
r8169
mii
pata_atiixp
ramzswap
lzo_compress


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x99430140
0x12 0x411111f0
0x14 0x01014010
0x15 0x01011012
0x16 0x01016011
0x17 0x01012014
0x18 0x01a19850
0x19 0x02a19c60
0x1a 0x0181305f
0x1b 0x02214c20
0x1c 0x411111f0
0x1d 0x4005e601
0x1e 0x01456130
0x1f 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:

/sys/class/sound/hwC1D1/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D1/driver_pin_configs:

/sys/class/sound/hwC1D1/user_pin_configs:

/sys/class/sound/hwC1D1/init_verbs:

/sys/class/sound/hwC1D2/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D2/driver_pin_configs:

/sys/class/sound/hwC1D2/user_pin_configs:

/sys/class/sound/hwC1D2/init_verbs:

/sys/class/sound/hwC1D3/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D3/driver_pin_configs:

/sys/class/sound/hwC1D3/user_pin_configs:

/sys/class/sound/hwC1D3/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   14.483259]   alloc kstat_irqs on node 0
[   14.483265] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.483348] ALSA hda_intel.c:2561: chipset global capabilities = 0x4401
[   14.500118] lp0: using parport0 (interrupt-driven).
[   14.550012] ALSA hda_intel.c:914: codec_mask = 0x1
[   14.550101] ALSA hda_intel.c:1354: codec #0 probed OK
[   14.586212] ALSA patch_realtek.c:1530: SKU: Nid=0x1d sku_cfg=0x4005e601
[   14.586215] ALSA patch_realtek.c:1532: SKU: port_connectivity=0x1
[   14.586217] ALSA patch_realtek.c:1533: SKU: enable_pcbeep=0x0
[   14.586218] ALSA patch_realtek.c:1534: SKU: check_sum=0x00000005
[   14.586220] ALSA patch_realtek.c:1535: SKU: customization=0x000000e6
[   14.586222] ALSA patch_realtek.c:1536: SKU: external_amp=0x0
[   14.586223] ALSA patch_realtek.c:1537: SKU: platform_type=0x0
[   14.586225] ALSA patch_realtek.c:1538: SKU: swap=0x0
[   14.586226] ALSA patch_realtek.c:1539: SKU: override=0x1
[   14.586386] hda_codec: ALC892: BIOS auto-probing.
[   14.586390] ALSA hda_codec.c:4633: autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0)
[   14.586392] ALSA hda_codec.c:4637:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   14.586394] ALSA hda_codec.c:4641:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   14.586396] ALSA hda_codec.c:4642:    mono: mono_out=0x0
[   14.586397] ALSA hda_codec.c:4645:    dig-out=0x11/0x1e
[   14.586399] ALSA hda_codec.c:4646:    inputs:
[   14.586401] ALSA hda_codec.c:4650:  Rear Mic=0x18
[   14.586402] ALSA hda_codec.c:4650:  Front Mic=0x19
[   14.586404] ALSA hda_codec.c:4650:  Line=0x1a
[   14.586405] ALSA hda_codec.c:4652: 
[   14.588533] ALSA patch_realtek.c:1587: realtek: No valid SSID, checking pincfg 0x4005e601 for NID 0x1d
[   14.588535] ALSA patch_realtek.c:1603: realtek: Enabling init ASM_ID=0xe601 CODEC_ID=10ec0892
[   14.591532] ALSA hda_codec.c:2164: Cannot find slave Surround Playback Volume, skipped
[   14.591535] ALSA hda_codec.c:2164: Cannot find slave Side Playback Volume, skipped
[   14.591538] ALSA hda_codec.c:2164: Cannot find slave Speaker Playback Volume, skipped
[   14.591540] ALSA hda_codec.c:2164: Cannot find slave Mono Playback Volume, skipped
[   14.591542] ALSA hda_codec.c:2164: Cannot find slave Line-Out Playback Volume, skipped
[   14.591543] ALSA hda_codec.c:2164: Cannot find slave PCM Playback Volume, skipped
[   14.591547] ALSA hda_codec.c:2164: Cannot find slave Surround Playback Switch, skipped
[   14.591551] ALSA hda_codec.c:2164: Cannot find slave Side Playback Switch, skipped
[   14.591553] ALSA hda_codec.c:2164: Cannot find slave Speaker Playback Switch, skipped
[   14.591555] ALSA hda_codec.c:2164: Cannot find slave Mono Playback Switch, skipped
[   14.591559] ALSA hda_codec.c:2164: Cannot find slave Line-Out Playback Switch, skipped
[   14.591561] ALSA hda_codec.c:2164: Cannot find slave PCM Playback Switch, skipped
[   14.591777] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   14.591919] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   14.591922] hda_intel: Disable MSI for Nvidia chipset
[   14.591947] HDA Intel 0000:01:00.1: setting latency timer to 64
[   14.591950] ALSA hda_intel.c:2561: chipset global capabilities = 0x2403
[   14.650019] ALSA hda_intel.c:914: codec_mask = 0xf
[   14.670017] ALSA hda_intel.c:1354: codec #0 probed OK
[   14.690017] ALSA hda_intel.c:1354: codec #1 probed OK
[   14.710017] ALSA hda_intel.c:1354: codec #2 probed OK
[   14.730110] ALSA hda_intel.c:1354: codec #3 probed OK
[   14.922888] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
--
[   16.830492] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.06  Mon Sep 13 04:29:19 PDT 2010
[   18.939494] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   18.971688] ALSA patch_hdmi.c:793: hdmi_setup_stream: NID=0x5, pinctl=0x40
[   18.971694] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
[   19.031723] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.071686] ALSA patch_hdmi.c:793: hdmi_setup_stream: NID=0x5, pinctl=0x40
[   19.071690] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
[   19.072374] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.072403] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.073914] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   19.111685] ALSA patch_hdmi.c:793: hdmi_setup_stream: NID=0x5, pinctl=0x40
[   19.111689] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
[   19.111750] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   19.151688] ALSA patch_hdmi.c:793: hdmi_setup_stream: NID=0x5, pinctl=0x40
[   19.151691] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x6, channel=0, format=0x4011
[   19.158683] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.158687] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.158689] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.158691] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.158781] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.158783] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.158785] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.158786] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.158921] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.158923] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.158924] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.158926] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.159106] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.159108] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.159110] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.159111] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.159194] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.159196] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.159197] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.159199] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.159278] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.159280] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.159281] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.159283] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.159399] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.159401] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.159402] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.159404] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.159576] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.159578] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.159579] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.159581] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.159662] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.159664] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.159666] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.159667] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.159747] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.159749] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.159751] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.159752] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.159867] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.159869] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.159870] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.159872] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.160043] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.160045] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.160047] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.160048] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.160130] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.160131] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.160133] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.160134] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.160213] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.160215] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.160217] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.160218] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.160333] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.160334] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.160336] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.160338] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.160509] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.160511] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.160512] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.160514] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.160594] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.160596] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.160597] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.160599] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.160680] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.160682] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.160684] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.160685] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.160801] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.160803] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.160804] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.160806] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.160978] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.160980] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.160982] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.160983] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.161292] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.161312] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   19.181696] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   19.201694] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   19.221689] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x25, stream=0x5, channel=0, format=0x4011
[   19.241688] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   19.261691] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x4011
[   19.281729] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.281745] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   19.281747] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   19.281752] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   19.281754] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x25, stream=0x5, channel=0, format=0x4011
[   19.281756] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[   19.281758] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x4011
[   19.281967] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.282057] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.282184] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.282363] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.282660] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.282668] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.301730] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.301738] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.301753] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.301761] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.302147] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.302149] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.302150] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.302152] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.302154] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.302155] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.302169] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.302171] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.302173] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.302174] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.302474] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x6e80, format=0x4013
[   19.302483] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.302485] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.302486] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4013
[   19.321693] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x25, stream=0x5, channel=0, format=0x4013
[   19.341694] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4013
[   19.343039] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   19.361686] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x4013
[   19.381733] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x6e80, format=0x4013
[   19.381742] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.381744] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.381746] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4013
[   19.381749] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x25, stream=0x5, channel=0, format=0x4013
[   19.381751] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4013
[   19.381753] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x4013
[   19.381947] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.382038] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.382167] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.382347] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.382647] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.382655] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.382688] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.382695] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.382702] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.382708] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.383049] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.383051] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.383053] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.383054] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.383079] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.383081] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.383082] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.383084] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.383478] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xa500, format=0x4015
[   19.383487] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.383489] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.383491] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4015
[   19.401685] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x25, stream=0x5, channel=0, format=0x4015
[   19.421686] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4015
[   19.441686] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=4, format=0x4015
[   19.461721] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xa500, format=0x4015
[   19.461730] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.461732] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.461733] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4015
[   19.461735] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x25, stream=0x5, channel=0, format=0x4015
[   19.461738] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4015
[   19.461740] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=4, format=0x4015
[   19.461876] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.461962] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.462082] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.462257] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.462527] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.462535] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.462569] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.462576] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.462584] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.462590] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.462923] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.462925] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.462927] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.462929] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.462948] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.462950] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.462952] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.462953] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.463338] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xa500, format=0x4015
[   19.463347] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.463349] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.463350] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4015
[   19.463353] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x25, stream=0x5, channel=0, format=0x4015
[   19.463355] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4015
[   19.463357] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=4, format=0x4015
[   19.463380] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xa500, format=0x4015
[   19.463387] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.463389] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.463390] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4015
[   19.463393] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x25, stream=0x5, channel=0, format=0x4015
[   19.463395] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4015
[   19.463397] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=4, format=0x4015
[   19.463485] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.463568] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.463685] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.463860] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.464129] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.464137] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.464170] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.464177] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.464183] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.464188] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.464513] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.464515] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.464517] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.464518] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.464542] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.464544] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.464546] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.464547] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.464836] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xa500, format=0x4015
[   19.464845] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.464846] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.464848] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4015
[   19.464851] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x25, stream=0x5, channel=0, format=0x4015
[   19.464853] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4015
[   19.464855] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=4, format=0x4015
[   19.464877] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xa500, format=0x4015
[   19.464885] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.464887] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.464888] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4015
[   19.464891] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x25, stream=0x5, channel=0, format=0x4015
[   19.464893] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4015
[   19.464895] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=4, format=0x4015
[   19.464981] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.465062] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.465179] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.465355] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.465627] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.465634] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.465667] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.465674] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.465681] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.465686] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.466009] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.466011] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.466012] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.466014] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.466038] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.466039] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.466041] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.466043] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.466229] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.466231] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.466233] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.466234] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.466408] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.466410] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.466412] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.466413] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.466652] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.466654] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.466655] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.466657] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.466961] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.466962] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.466964] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.466966] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.467140] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.467142] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.467144] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.467145] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.467317] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.467319] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.467320] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.467322] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.467559] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.467561] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.467562] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.467564] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.467864] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.467866] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.467868] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.467869] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.468045] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.468046] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.468048] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.468050] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.468222] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.468224] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.468225] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.468227] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.468463] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.468464] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.468466] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.468468] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.468768] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.468770] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.468772] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.468773] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.468947] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.468949] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.468951] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.468952] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.469124] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.469125] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.469127] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.469129] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.469364] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.469366] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.469368] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.469369] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.469670] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.469672] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.469673] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.469675] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.469849] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.469851] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.469853] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.469854] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.470029] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.470031] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.470033] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.470034] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.470269] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.470271] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.470272] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.470274] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.470573] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   19.470575] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   19.470577] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   19.470578] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   19.470888] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.470899] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x8, channel=0, format=0x4011
[   19.491686] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[   19.511722] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.511733] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x8, channel=0, format=0x4011
[   19.511735] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[   19.511877] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.511963] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.512084] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.512260] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.512531] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.512539] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.512573] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.512580] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.512586] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.512592] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.512915] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.512917] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.512953] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.512955] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.513182] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.513183] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.513399] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.513401] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.513668] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.513669] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.513992] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.513994] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.514213] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.514215] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.514428] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.514429] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.514687] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.514689] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.515009] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.515011] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.515230] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.515232] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.515446] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.515448] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.515707] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.515709] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.516028] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.516030] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.516250] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.516252] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.516466] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.516468] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.516726] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.516728] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.517048] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.517050] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.517268] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.517269] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.517483] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.517485] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.517743] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.517745] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.518066] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.518068] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.519040] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.519121] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.519238] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.519414] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.519706] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.519714] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.519748] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.519754] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.519762] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.519769] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   19.521013] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xff00, format=0x4015
[   19.521023] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.521025] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.521027] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4015
[   19.521030] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x25, stream=0x5, channel=0, format=0x4015
[   19.521032] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4015
[   19.521034] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=4, format=0x4015
[   19.521075] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xff00, format=0x4015
[   19.521083] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.521084] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   19.521086] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4015
[   19.521088] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x25, stream=0x5, channel=0, format=0x4015
[   19.521090] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4015
[   19.521092] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=4, format=0x4015
[   19.527472] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   19.527480] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.527512] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   19.527519] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   19.588536] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   21.584494] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   24.914603] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   24.914617] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   25.170021] eth0: no IPv6 routers present
[   29.915277] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   29.915309] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   29.915674] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   29.915677] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   29.915679] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   29.915681] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   29.915695] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   29.915696] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[   29.915698] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x4
[   29.915699] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x25
[   89.749857] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xff00, format=0x4015
[   89.749868] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   89.749871] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   89.749873] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4015
[   89.749876] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x25, stream=0x5, channel=0, format=0x4015
[   89.749878] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4015
[   89.749880] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=4, format=0x4015
[   89.749915] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xff00, format=0x4015
[   89.749923] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   89.749925] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   89.749926] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4015
[   89.749928] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x25, stream=0x5, channel=0, format=0x4015
[   89.749930] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=2, format=0x4015
[   89.749932] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=4, format=0x4015
```

---

### Post by Sunships on 2011-07-30
Hello! After several peaceful (or should that be noisy?) months, the sound on my computer has stopped working once more following the installation of various system updates. As promised, here is the output of the script used in the above post. If someone knowledgeable in these matters could take a look at the two and let me know if they can identify the source of the problem, and how I can fix it, please post here and I will be beholden unto you.

In the above post is what the script output is when sound is working. Below is the script output today while it has stopped working:

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Jul 30 13:58:55 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name
Product Version:   System Version


!!Kernel Information
!!------------------

Kernel release:    2.6.35-28-generic
Operating System:  GNU/Linux
Architecture:      x86_64
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

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfbff8000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe87c000 irq 19


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:00.1 Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383 (rev 40)
	Subsystem: 1043:841b
--
01:00.1 0403: 10de:0beb (rev a1)
	Subsystem: 1462:2322


!!Modprobe options (Sound related)
!!--------------------------------

snd-snd_hda_intel: index=0
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
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
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

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
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

Codec: Realtek ALC892
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0892
Subsystem Id: 0x1043841b
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC892 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x23 0x23]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x23 0x23]
  Converter: stream=5, channel=2
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x23 0x23]
  Converter: stream=5, channel=4
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC892 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x90 0x90]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC892 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x2e 0x2e]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100711: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=In, idx=0, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x99430140: [Fixed] SPDIF Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x4, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003e: IN OUT HP EAPD Detect Trigger
  EAPD 0x2: EAPD
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19850: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19c60: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x6, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181305f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x5, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001373e: IN OUT HP EAPD Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  EAPD 0x2: EAPD
  Pin Default 0x02214c20: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4005e601: [N/A] Line Out at Ext N/A
    Conn = Optical, Color = White
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x01456130: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Orange
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400681: Stereo Digital
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=24
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 12
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x23 0x23]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x26 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x25 0x0b
Codec: Nvidia GPU 12 HDMI/DP
Address: 0
Function Id: 0x1
Vendor Id: 0x10de0012
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=3
  Converter: stream=6, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GPU 12 HDMI/DP
Address: 1
Function Id: 0x1
Vendor Id: 0x10de0012
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=7
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GPU 12 HDMI/DP
Address: 2
Function Id: 0x1
Vendor Id: 0x10de0012
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=2, device=0
  Control: name="IEC958 Playback Pro Mask", index=2, device=0
  Control: name="IEC958 Playback Default", index=2, device=0
  Control: name="IEC958 Playback Switch", index=2, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=8
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GPU 12 HDMI/DP
Address: 3
Function Id: 0x1
Vendor Id: 0x10de0012
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=3, device=0
  Control: name="IEC958 Playback Pro Mask", index=3, device=0
  Control: name="IEC958 Playback Default", index=3, device=0
  Control: name="IEC958 Playback Switch", index=3, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=9
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  8 Jul 30 14:30 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 17 Jul 30 14:30 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  7 Jul 30 14:30 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 16 Jul 30 14:30 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116, 15 Jul 30 14:30 /dev/snd/hwC1D1
crw-rw----+ 1 root audio 116, 14 Jul 30 14:30 /dev/snd/hwC1D2
crw-rw----+ 1 root audio 116, 13 Jul 30 14:30 /dev/snd/hwC1D3
crw-rw----+ 1 root audio 116,  6 Jul 30 14:32 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  5 Jul 30 14:32 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  4 Jul 30 14:30 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 12 Jul 30 14:57 /dev/snd/pcmC1D3p
crw-rw----+ 1 root audio 116, 11 Jul 30 14:30 /dev/snd/pcmC1D7p
crw-rw----+ 1 root audio 116, 10 Jul 30 14:30 /dev/snd/pcmC1D8p
crw-rw----+ 1 root audio 116,  9 Jul 30 14:30 /dev/snd/pcmC1D9p
crw-rw----+ 1 root audio 116,  3 Jul 30 14:29 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Jul 30 14:29 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Jul 30 14:30 .
drwxr-xr-x 3 root root 380 Jul 30 14:30 ..
lrwxrwxrwx 1 root root  12 Jul 30 14:30 pci-0000:00:14.2 -> ../controlC0
lrwxrwxrwx 1 root root  12 Jul 30 14:30 pci-0000:01:00.1 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0xfbff8000 irq 16'
  Mixer name	: 'Realtek ALC892'
  Components	: 'HDA:10ec0892,1043841b,00100302'
  Controls      : 33
  Simple ctrls  : 19
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 35 [55%] [-29.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
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
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 46 [100%] [30.00dB] [on]
  Front Right: Capture 46 [100%] [30.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 16 [35%] [0.00dB] [off]
  Front Right: Capture 16 [35%] [0.00dB] [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Line'

!!-------Mixer controls for card 1 [NVidia]

Card hw:1 'NVidia'/'HDA NVidia at 0xfe87c000 irq 19'
  Mixer name	: 'Nvidia GPU 12 HDMI/DP'
  Components	: 'HDA:10de0012,10de0101,00100100'
  Controls      : 16
  Simple ctrls  : 4
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',3
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.SB {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 64
		value.1 64
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
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 64
		value.1 64
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Center Playback Volume'
		value 64
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'LFE Playback Volume'
		value 64
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value true
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value true
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 64
		value.1 64
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.11 {
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
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Front Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 true
		value.1 true
	}
	control.17 {
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
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Front Mic Boost'
		value.0 0
		value.1 0
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 46'
		comment.dbmin -1600
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		value.0 46
		value.1 46
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 46'
		comment.dbmin -1600
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 16
		value.1 16
	}
	control.23 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		iface MIXER
		name 'Input Source'
		value 'Front Mic'
	}
	control.24 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		iface MIXER
		name 'Input Source'
		index 1
		value Line
	}
	control.25 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.26 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.27 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.29 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.30 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 35
	}
	control.31 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.32 {
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
	control.33 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 120'
		comment.tlv '0000000100000008fffff44800000032'
		comment.dbmin -3000
		comment.dbmax 3000
		iface MIXER
		name 'Digital Capture Volume'
		value.0 60
		value.1 60
	}
}
state.NVidia {
	control.1 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.2 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.3 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.5 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 1
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.6 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 1
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.7 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		index 1
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		index 1
		value true
	}
	control.9 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 2
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.10 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 2
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.11 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		index 2
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		index 2
		value true
	}
	control.13 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 3
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.14 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 3
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.15 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		index 3
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		index 3
		value true
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_seq_dummy
binfmt_misc
vboxnetadp
vboxnetflt
vboxdrv
dm_crypt
snd_hda_codec_nvhdmi
snd_hda_codec_realtek
snd_hda_intel
snd_hda_codec
nvidia
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
ppdev
snd
lp
parport_pc
psmouse
soundcore
parport
joydev
serio_raw
snd_page_alloc
edac_core
edac_mce_amd
hid_drff
asus_atk0110
k10temp
ff_memless
i2c_piix4
dm_raid45
xor
usbhid
firewire_ohci
hid
firewire_core
crc_itu_t
ahci
pata_via
pata_atiixp
r8169
mii
xhci_hcd
libahci
ramzswap
lzo_compress


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x99430140
0x12 0x411111f0
0x14 0x01014010
0x15 0x01011012
0x16 0x01016011
0x17 0x01012014
0x18 0x01a19850
0x19 0x02a19c60
0x1a 0x0181305f
0x1b 0x02214c20
0x1c 0x411111f0
0x1d 0x4005e601
0x1e 0x01456130
0x1f 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:

/sys/class/sound/hwC1D1/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D1/driver_pin_configs:

/sys/class/sound/hwC1D1/user_pin_configs:

/sys/class/sound/hwC1D1/init_verbs:

/sys/class/sound/hwC1D2/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D2/driver_pin_configs:

/sys/class/sound/hwC1D2/user_pin_configs:

/sys/class/sound/hwC1D2/init_verbs:

/sys/class/sound/hwC1D3/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D3/driver_pin_configs:

/sys/class/sound/hwC1D3/user_pin_configs:

/sys/class/sound/hwC1D3/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   12.468812]   alloc kstat_irqs on node 0
[   12.468819] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.571759] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
--
[   12.571885] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.06  Mon Sep 13 04:29:19 PDT 2010
[   12.689217] hda_codec: ALC892: BIOS auto-probing.
[   12.696353] Too many connections
[   12.697677] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   12.697680] hda_intel: Disable MSI for Nvidia chipset
[   12.697713] HDA Intel 0000:01:00.1: setting latency timer to 64
[   14.546053] type=1400 audit(1312032601.754:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1079 comm="apparmor_parser"
--
[   26.525994] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   30.474238] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   32.251868] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.


```

---

### Post by shantiq on 2011-07-30
i am going to offer something simple here which is often overlooked


sometimes when one reboots sound goes to mute in the sound preferences    just check that next time it goes quiet

system/preferences/sound  and see if the box is checked



if i am stating the obvious just ignore this:KS

---

### Post by Sunships on 2011-08-01
> **shantiq said:**
> i am going to offer something simple here which is often overlooked


sometimes when one reboots sound goes to mute in the sound preferences    just check that next time it goes quiet

system/preferences/sound  and see if the box is checked



if i am stating the obvious just ignore this:KS

Thanks for stopping by Shantiq - that is definitely not the problem :)

---

### Post by Sunships on 2011-08-01
OK, so a few days later and the sound is back on. Here is another script output to compare with the previous.

I repeat, when the following output of this script was generated, the sound was WORKING:

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Mon Aug  1 18:18:36 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name
Product Version:   System Version


!!Kernel Information
!!------------------

Kernel release:    2.6.35-28-generic
Operating System:  GNU/Linux
Architecture:      x86_64
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

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfbff8000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe87c000 irq 19


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:00.1 Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383 (rev 40)
	Subsystem: 1043:841b
--
01:00.1 0403: 10de:0beb (rev a1)
	Subsystem: 1462:2322


!!Modprobe options (Sound related)
!!--------------------------------

snd-snd_hda_intel: index=0
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
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
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

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
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

Codec: Realtek ALC892
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0892
Subsystem Id: 0x1043841b
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC892 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x19 0x19]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x19 0x19]
  Converter: stream=5, channel=2
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x19 0x19]
  Converter: stream=5, channel=4
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC892 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x90 0x90]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC892 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x2e 0x2e]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100711: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=In, idx=0, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x99430140: [Fixed] SPDIF Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x4, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003e: IN OUT HP EAPD Detect Trigger
  EAPD 0x2: EAPD
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19850: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19c60: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x6, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181305f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x5, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001373e: IN OUT HP EAPD Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  EAPD 0x2: EAPD
  Pin Default 0x02214c20: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4005e601: [N/A] Line Out at Ext N/A
    Conn = Optical, Color = White
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x01456130: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Orange
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400681: Stereo Digital
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=24
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 12
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x19 0x19]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x26 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x25 0x0b
Codec: Nvidia GPU 12 HDMI/DP
Address: 0
Function Id: 0x1
Vendor Id: 0x10de0012
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=3
  Converter: stream=6, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GPU 12 HDMI/DP
Address: 1
Function Id: 0x1
Vendor Id: 0x10de0012
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=7
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GPU 12 HDMI/DP
Address: 2
Function Id: 0x1
Vendor Id: 0x10de0012
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=2, device=0
  Control: name="IEC958 Playback Pro Mask", index=2, device=0
  Control: name="IEC958 Playback Default", index=2, device=0
  Control: name="IEC958 Playback Switch", index=2, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=8
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GPU 12 HDMI/DP
Address: 3
Function Id: 0x1
Vendor Id: 0x10de0012
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
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=3, device=0
  Control: name="IEC958 Playback Pro Mask", index=3, device=0
  Control: name="IEC958 Playback Default", index=3, device=0
  Control: name="IEC958 Playback Switch", index=3, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=9
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  8 Aug  1 11:41 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 17 Aug  1 11:41 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  7 Aug  1 11:41 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 16 Aug  1 11:41 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116, 15 Aug  1 11:41 /dev/snd/hwC1D1
crw-rw----+ 1 root audio 116, 14 Aug  1 11:41 /dev/snd/hwC1D2
crw-rw----+ 1 root audio 116, 13 Aug  1 11:41 /dev/snd/hwC1D3
crw-rw----+ 1 root audio 116,  6 Aug  1 18:39 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  5 Aug  1 15:17 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  4 Aug  1 11:41 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 12 Aug  1 11:41 /dev/snd/pcmC1D3p
crw-rw----+ 1 root audio 116, 11 Aug  1 11:41 /dev/snd/pcmC1D7p
crw-rw----+ 1 root audio 116, 10 Aug  1 11:41 /dev/snd/pcmC1D8p
crw-rw----+ 1 root audio 116,  9 Aug  1 11:41 /dev/snd/pcmC1D9p
crw-rw----+ 1 root audio 116,  3 Aug  1 11:41 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Aug  1 11:41 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Aug  1 11:41 .
drwxr-xr-x 3 root root 380 Aug  1 11:41 ..
lrwxrwxrwx 1 root root  12 Aug  1 11:41 pci-0000:00:14.2 -> ../controlC0
lrwxrwxrwx 1 root root  12 Aug  1 11:41 pci-0000:01:00.1 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0xfbff8000 irq 16'
  Mixer name	: 'Realtek ALC892'
  Components	: 'HDA:10ec0892,1043841b,00100302'
  Controls      : 33
  Simple ctrls  : 19
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 25 [39%] [-39.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 253 [99%] [0.40dB]
  Front Right: Playback 253 [99%] [0.40dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
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
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 46 [100%] [30.00dB] [on]
  Front Right: Capture 46 [100%] [30.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 16 [35%] [0.00dB] [off]
  Front Right: Capture 16 [35%] [0.00dB] [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Line'

!!-------Mixer controls for card 1 [NVidia]

Card hw:1 'NVidia'/'HDA NVidia at 0xfe87c000 irq 19'
  Mixer name	: 'Nvidia GPU 12 HDMI/DP'
  Components	: 'HDA:10de0012,10de0101,00100100'
  Controls      : 16
  Simple ctrls  : 4
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',3
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.SB {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 64
		value.1 64
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
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 64
		value.1 64
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Center Playback Volume'
		value 64
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'LFE Playback Volume'
		value 64
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value true
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value true
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 64
		value.1 64
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.11 {
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
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Front Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 true
		value.1 true
	}
	control.17 {
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
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Front Mic Boost'
		value.0 0
		value.1 0
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 46'
		comment.dbmin -1600
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		value.0 46
		value.1 46
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 46'
		comment.dbmin -1600
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 16
		value.1 16
	}
	control.23 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		iface MIXER
		name 'Input Source'
		value 'Front Mic'
	}
	control.24 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		iface MIXER
		name 'Input Source'
		index 1
		value Line
	}
	control.25 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.26 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.27 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.29 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.30 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 25
	}
	control.31 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.32 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 253
		value.1 253
	}
	control.33 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 120'
		comment.tlv '0000000100000008fffff44800000032'
		comment.dbmin -3000
		comment.dbmax 3000
		iface MIXER
		name 'Digital Capture Volume'
		value.0 60
		value.1 60
	}
}
state.NVidia {
	control.1 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.2 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.3 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.5 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 1
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.6 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 1
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.7 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		index 1
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		index 1
		value true
	}
	control.9 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 2
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.10 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 2
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.11 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		index 2
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		index 2
		value true
	}
	control.13 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 3
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.14 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 3
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.15 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		index 3
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		index 3
		value true
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
dm_crypt
binfmt_misc
vboxnetadp
vboxnetflt
vboxdrv
snd_hda_codec_nvhdmi
snd_hda_codec_realtek
nvidia
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_seq_midi
snd_pcm
snd_rawmidi
snd_seq_midi_event
snd_seq
joydev
ppdev
hid_drff
ff_memless
parport_pc
snd_timer
snd_seq_device
asus_atk0110
k10temp
psmouse
serio_raw
edac_core
edac_mce_amd
snd
i2c_piix4
soundcore
snd_page_alloc
lp
parport
dm_raid45
xor
usbhid
hid
pata_atiixp
ahci
libahci
firewire_ohci
pata_via
firewire_core
xhci_hcd
r8169
mii
crc_itu_t
ramzswap
lzo_compress


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x99430140
0x12 0x411111f0
0x14 0x01014010
0x15 0x01011012
0x16 0x01016011
0x17 0x01012014
0x18 0x01a19850
0x19 0x02a19c60
0x1a 0x0181305f
0x1b 0x02214c20
0x1c 0x411111f0
0x1d 0x4005e601
0x1e 0x01456130
0x1f 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:

/sys/class/sound/hwC1D1/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D1/driver_pin_configs:

/sys/class/sound/hwC1D1/user_pin_configs:

/sys/class/sound/hwC1D1/init_verbs:

/sys/class/sound/hwC1D2/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D2/driver_pin_configs:

/sys/class/sound/hwC1D2/user_pin_configs:

/sys/class/sound/hwC1D2/init_verbs:

/sys/class/sound/hwC1D3/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D3/driver_pin_configs:

/sys/class/sound/hwC1D3/user_pin_configs:

/sys/class/sound/hwC1D3/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   15.259565]   alloc kstat_irqs on node 0
[   15.259571] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.281375] type=1400 audit(1312195287.493:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=865 comm="apparmor_parser"
--
[   15.300119] lp0: using parport0 (interrupt-driven).
[   15.365711] hda_codec: ALC892: BIOS auto-probing.
[   15.372772] Too many connections
[   15.374105] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   15.374108] hda_intel: Disable MSI for Nvidia chipset
[   15.374166] HDA Intel 0000:01:00.1: setting latency timer to 64
[   15.924320] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr
--
[   18.779382] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   21.665881] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   23.039052] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   27.288396] eth0: no IPv6 routers present


```

---

### Post by Sunships on 2013-03-17
This problem still occurs occasionally in 12.04 (same hardware as above). I believe it is linked to a software update, as it tends to happen after running system update. 

It also once happened when I ran this command: sudo update-initramfs -u
Running the above command and rebooting also sometimes fixes the problem.

---

### Post by wildmanne39 on 2013-03-17
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

