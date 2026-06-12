---
title: "Ubuntu 10.10 installed on Vaio, no sound - end of my troubleshooting ability!"
date: 2011-05-30
forum: Multimedia Software
---

### Post by camtom12 on 2011-05-30
Hey!  I got a new computer and finally got around to a full dual-boot install, Windows 7 and Ubuntu 10.10.  I can't get my audio to work though.

I tried following this guide: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
and got all the way to step 11 with no dice.  I didn't try the terminal entries after that because I didn't really understand them.

Here's my terminal outputs for step 3 and 4 of the above troubleshooting procedure: [https://answers.launchpad.net/ubuntu/+question/159547](https://answers.launchpad.net/ubuntu/+question/159547)


Next I searched and found this which seemed close to my problem: [http://ubuntuforums.org/showthread.php?t=1732225](http://ubuntuforums.org/showthread.php?t=1732225)

I followed those steps and no dice there, either.

I'm at a loss, does anyone have any ideas?

---

### Post by BicyclerBoy on 2011-05-31
I'd do the real simple step of running from terminal:

pavucontrol

check the output device is appropriate to your connection i.e. analogue stereo 2ch output 

check for mutes & very low (0) volume settings..

Check the microphone by using the VU meters in gnome sound preferences...

---

### Post by Yellow Pasque on 2011-05-31
Run the alsa-info script: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

---

### Post by camtom12 on 2011-05-31
> **BicyclerBoy said:**
> I'd do the real simple step of running from terminal:

pavucontrol

check the output device is appropriate to your connection i.e. analogue stereo 2ch output 

check for mutes & very low (0) volume settings..

Check the microphone by using the VU meters in gnome sound preferences...


Checked - they all appear to be normal!  but all my little speaker buttons (mute on/off) have the lines next to them like they're always muted.  Clicking them shadows the controls, clicking again brings everything back on-line but no change to the icon.  Not sure if this is normal or not.

---

### Post by camtom12 on 2011-05-31
> **Temüjin said:**
> Run the alsa-info script: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)


To run this do I need to just paste all of it into a terminal?

---

### Post by Yellow Pasque on 2011-05-31
You download the file, untar it and run the script. Then the script gives you a link to a text webpage with your info (and you post the link).

---

### Post by camtom12 on 2011-06-01
> **Temüjin said:**
> You download the file, untar it and run the script. Then the script gives you a link to a text webpage with your info (and you post the link).


Tried to untar - it said it's not a compressed file.  So then I just double-clicked it and it gave me this:

Do you want to run "alsa-info.sh", or display its contents?
"alsa-info.sh" is an executable text file.

First I tried to "Run" and nothing happened, then I tried to "Run in Terminal" and saw some progress stuff going on but then the terminal shut itself down and I don't have a clue where that information got uploaded to.

---

### Post by camtom12 on 2011-06-01
> **Temüjin said:**
> You download the file, untar it and run the script. Then the script gives you a link to a text webpage with your info (and you post the link).


Better yet, here's the link from my original post that has the alsa-info script output when I ran it from a terminal a couple of days ago:  [https://answers.launchpad.net/ubuntu/+question/159547](https://answers.launchpad.net/ubuntu/+question/159547)

---

### Post by camtom12 on 2011-06-02
Does anyone have any ideas?  I'm pretty much past any troubleshooting I can do at my current ubuntu ability.

Thanks!

---

### Post by lidex on 2011-06-03
Have you tried a LiveCD session of 11.04? See if you can get sound that way. [http://cdimage.ubuntu.com/releases/11.04/release/](http://cdimage.ubuntu.com/releases/11.04/release/)

---

### Post by camtom12 on 2011-06-04
> **lidex said:**
> Have you tried a LiveCD session of 11.04? See if you can get sound that way. [http://cdimage.ubuntu.com/releases/11.04/release/](http://cdimage.ubuntu.com/releases/11.04/release/)


I haven't.  My current internet speed just about precludes me from downloading the .iso for 11.04.  I had to get my wife send me a disc with 10.10 on it.

Over the course of the last 2 days I was able to update through the software center to 11.04 though.  It's a neat update, but still no sound in my case.  I'm going to re-run through the troubleshooting guide up to where I'm at now and see if that helps.

---

### Post by camtom12 on 2011-06-04
Ok, here's my ALSA Info Script

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Jun  4 17:17:34 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"


!!DMI Information
!!---------------

Manufacturer:      Sony Corporation
Product Name:      VPCEE42FX
Product Version:   C105867M


!!Kernel Information
!!------------------

Kernel release:    2.6.38-8-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         athlon
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.24.1
Utilities version:  1.0.24.2


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
                      HDA ATI SB at 0xf4300000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xf4210000 irq 19


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383 (rev 40)
    Subsystem: 104d:9077
--
01:05.1 0403: 1002:970f
    Subsystem: 104d:9077


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
snd-hda-intel: model=lenovo-101e


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : lenovo-101e,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
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
    model : lenovo-101e,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
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

Codec: Realtek ALC269VB
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0269
Subsystem Id: 0x104d4c00
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC269VB Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x57 0x57]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x57 0x57]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x8b 0x8b]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC269VB Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 5
     0x18 0x19 0x1a 0x1b 0x1d
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0f [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x00]
  Connection: 2
     0x02 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x40000b: Stereo Amp-In
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x03 0x03]
  Pincap 0x00000020: IN
  Pin Default 0x99a30920: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00010014: OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x16 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x17 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x02 0x02]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00001734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a15830: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Red
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=08, enabled=1
  Connection: 1
     0x0d
Node 0x19 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x22: IN VREF_GRD
  Unsolicited: tag=00, enabled=0
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003c: IN OUT HP Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4007992d: [N/A] Line Out at Ext N/A
    Conn = Analog, Color = Pink
    DefAssociation = 0x2, Sequence = 0xd
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=25
Node 0x21 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0221101f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 2
     0x0c 0x0d*
Node 0x22 [Audio Selector] wcaps 0x30010b: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Connection: 7
     0x18 0x19 0x1a 0x1b 0x1d 0x0b 0x12*
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x0b
Codec: ATI RS690/780 HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002791a
Subsystem Id: 0x104d4c00
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x60]: 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=1, channel=0
  Digital: Enabled
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  5 Jun  4 19:40 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  8 Jun  4 19:40 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  4 Jun  4 19:40 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  7 Jun  4 19:40 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116,  3 Jun  4 20:06 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  2 Jun  4 20:17 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  6 Jun  4 19:41 /dev/snd/pcmC1D3p
crw-rw----+ 1 root audio 116,  1 Jun  4 19:40 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jun  4 19:40 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Jun  4 19:40 .
drwxr-xr-x 3 root root 240 Jun  4 19:40 ..
lrwxrwxrwx 1 root root  12 Jun  4 19:40 pci-0000:00:14.2 -> ../controlC0
lrwxrwxrwx 1 root root  12 Jun  4 19:40 pci-0000:01:05.1 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0xf4300000 irq 16'
  Mixer name    : 'Realtek ALC269VB'
  Components    : 'HDA:10ec0269,104d4c00,00100100'
  Controls      : 11
  Simple ctrls  : 7
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 2 [67%] [24.00dB]
  Front Right: 2 [67%] [24.00dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [18.00dB] [off]
  Front Right: Capture 23 [74%] [18.00dB] [off]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [36.00dB]
  Front Right: 3 [100%] [36.00dB]

!!-------Mixer controls for card 1 [HDMI]

Card hw:1 'HDMI'/'HDA ATI HDMI at 0xf4210000 irq 19'
  Mixer name    : 'ATI RS690/780 HDMI'
  Components    : 'HDA:1002791a,104d4c00,00100000'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.SB {
    control.1 {
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 87
        value.1 87
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 87'
            dbmin -6525
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.2 {
        iface MIXER
        name 'Speaker Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.3 {
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 87
        value.1 87
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 87'
            dbmin -6525
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.4 {
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.5 {
        iface MIXER
        name 'Internal Mic Boost Volume'
        value.0 3
        value.1 3
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3600
            dbvalue.0 3600
            dbvalue.1 3600
        }
    }
    control.6 {
        iface MIXER
        name 'Mic Boost Volume'
        value.0 2
        value.1 2
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3600
            dbvalue.0 2400
            dbvalue.1 2400
        }
    }
    control.7 {
        iface MIXER
        name 'Capture Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.8 {
        iface MIXER
        name 'Capture Volume'
        value.0 23
        value.1 23
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -1650
            dbmax 3000
            dbvalue.0 1800
            dbvalue.1 1800
        }
    }
    control.9 {
        iface MIXER
        name 'Master Playback Volume'
        value 87
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 87'
            dbmin -6525
            dbmax 0
            dbvalue.0 0
        }
    }
    control.10 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.11 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 255
        value.1 255
        comment {
            access 'read write user'
            type INTEGER
            count 2
            range '0 - 255'
            tlv '0000000100000008ffffec1400000014'
            dbmin -5100
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
}
state.HDMI {
    control.1 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.2 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.3 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
parport_pc
ppdev
vesafb
snd_hda_codec_hdmi
snd_hda_codec_realtek
arc4
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
ath9k
mac80211
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
ath9k_common
snd_seq
ath9k_hw
snd_timer
snd_seq_device
fglrx
joydev
snd
uvcvideo
videodev
ath
soundcore
cfg80211
psmouse
sp5100_tco
i2c_piix4
snd_page_alloc
shpchp
sony_laptop
k10temp
serio_raw
video
lp
parport
usbhid
hid
usb_storage
uas
ahci
r8169
libahci
pata_atiixp


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x12 0x99a30920
0x14 0x90170110
0x17 0x411111f0
0x18 0x02a15830
0x19 0x411111f0
0x1a 0x411111f0
0x1b 0x411111f0
0x1d 0x4007992d
0x1e 0x411111f0
0x21 0x0221101f

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[    9.816014] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   10.510383] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.510485] HDA Intel 0000:00:14.2: setting latency timer to 64
[   11.073430] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
--
[   11.074100] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8780000, irq=19
[   11.105356] hda_codec: ALC269VB: BIOS auto-probing.
[   11.110882] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[   11.110997] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[   11.111158] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   11.111193] HDA Intel 0000:01:05.1: setting latency timer to 64
[   11.916476] vesafb: framebuffer at 0xe0000000, mapped to 0xf9900000, using 3072k, total 3072k
--
[   21.728852] [fglrx:MCIL_GetVirtualAddressInDescriptor] *ERROR* Can not get the virtual address
[   30.546076] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   32.533921] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0

```

I clearly have no idea what half this means or what it's supposed to look like!

Thanks for any help!

---

### Post by camtom12 on 2011-06-04
And here's the output from step 4:

```
Advanced Linux Sound Architecture Driver Version 1.0.23.
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf4300000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xf4210000 irq 19
  1:        : sequencer
  2: [ 0- 0]: digital audio playback
  3: [ 0- 0]: digital audio capture
  4: [ 0- 0]: hardware dependent
  5: [ 0]   : control
  6: [ 1- 3]: digital audio playback
  7: [ 1- 0]: hardware dependent
  8: [ 1]   : control
 33:        : timer
00-00: HDA Codec 0
01-00: HDA Codec 0
00-00: ALC269VB Analog : ALC269VB Analog : playback 1 : capture 1
01-03: HDMI 0 : HDMI 0 : playback 1
Client info
  cur  clients : 1
  peak clients : 1
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
[sudo] password for cameron: 
rm: cannot remove `/etc/asound.conf': No such file or directory
rm: cannot remove `/home/cameron/.asound*': No such file or directory
Ign http://extras.ubuntu.com natty InRelease                        
Ign http://security.ubuntu.com natty-security InRelease             
Ign http://iq.archive.ubuntu.com natty InRelease
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]                      
Hit http://extras.ubuntu.com natty Release                                   
Hit http://security.ubuntu.com natty-security Release.gpg
Hit http://security.ubuntu.com natty-security Release
Hit http://security.ubuntu.com natty-security/main Sources
Hit http://extras.ubuntu.com natty/main Sources
Hit http://security.ubuntu.com natty-security/restricted Sources
Hit http://extras.ubuntu.com natty/main i386 Packages
Hit http://security.ubuntu.com natty-security/universe Sources
Ign http://extras.ubuntu.com natty/main TranslationIndex
Hit http://security.ubuntu.com natty-security/multiverse Sources
Hit http://security.ubuntu.com natty-security/main i386 Packages
Hit http://security.ubuntu.com natty-security/restricted i386 Packages
Hit http://security.ubuntu.com natty-security/universe i386 Packages
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages    
Ign http://security.ubuntu.com natty-security/main TranslationIndex       
Ign http://iq.archive.ubuntu.com natty-updates InRelease
Ign http://extras.ubuntu.com natty/main Translation-en_US                                                                                                              
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex                                                                                              
Ign http://extras.ubuntu.com natty/main Translation-en                                                                                                                 
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex                                                                                              
Ign http://security.ubuntu.com natty-security/universe TranslationIndex                                                                                                
Hit http://iq.archive.ubuntu.com natty Release.gpg                                                                                                                     
Hit http://iq.archive.ubuntu.com natty-updates Release.gpg                                                                                                             
Ign http://security.ubuntu.com natty-security/main Translation-en_US                                                                                                   
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Hit http://iq.archive.ubuntu.com natty Release 
Hit http://iq.archive.ubuntu.com natty-updates Release                
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Hit http://iq.archive.ubuntu.com natty/main Sources
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Hit http://iq.archive.ubuntu.com natty/restricted Sources
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Hit http://iq.archive.ubuntu.com natty/universe Sources
Hit http://iq.archive.ubuntu.com natty/multiverse Sources                    
Ign http://security.ubuntu.com natty-security/universe Translation-en        
Hit http://iq.archive.ubuntu.com natty/main i386 Packages
Hit http://iq.archive.ubuntu.com natty/restricted i386 Packages
Hit http://iq.archive.ubuntu.com natty/universe i386 Packages
Hit http://iq.archive.ubuntu.com natty/multiverse i386 Packages
Ign http://iq.archive.ubuntu.com natty/main TranslationIndex
Ign http://iq.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://iq.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://iq.archive.ubuntu.com natty/universe TranslationIndex
Hit http://iq.archive.ubuntu.com natty-updates/main Sources
Hit http://iq.archive.ubuntu.com natty-updates/restricted Sources
Hit http://iq.archive.ubuntu.com natty-updates/universe Sources
Hit http://iq.archive.ubuntu.com natty-updates/multiverse Sources
Hit http://iq.archive.ubuntu.com natty-updates/main i386 Packages
Hit http://iq.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://iq.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://iq.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://iq.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://iq.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://iq.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://iq.archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://iq.archive.ubuntu.com natty/main Translation-en_US
Ign http://iq.archive.ubuntu.com natty/main Translation-en
Ign http://iq.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://iq.archive.ubuntu.com natty/multiverse Translation-en
Ign http://iq.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://iq.archive.ubuntu.com natty/restricted Translation-en
Ign http://iq.archive.ubuntu.com natty/universe Translation-en_US
Ign http://iq.archive.ubuntu.com natty/universe Translation-en
Ign http://iq.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://iq.archive.ubuntu.com natty-updates/main Translation-en
Ign http://iq.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://iq.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://iq.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://iq.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://iq.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://iq.archive.ubuntu.com natty-updates/universe Translation-en
Fetched 72 B in 42s (2 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
H/W path         Device      Class       Description
====================================================
                             system      VPCEE42FX (N/A)
/0                           bus         VAIO
/0/0                         memory      1MiB BIOS
/0/6                         processor   AMD Athlon(tm) II P360 Dual-Core Processor
/0/6/7                       memory      128KiB L1 cache
/0/6/8                       memory      512KiB L2 cache
/0/9                         memory      4GiB System Memory
/0/9/0                       memory      2GiB SODIMM DDR3
/0/9/1                       memory      2GiB SODIMM DDR3
/0/100                       bridge      RS880 Host Bridge
/0/100/1                     bridge      Sony Corporation
/0/100/1/5                   display     M880G [Mobility Radeon HD 4200]
/0/100/1/5.1                 multimedia  RS880 Audio Device [Radeon HD 4200]
/0/100/4                     bridge      RS780 PCI to PCI bridge (PCIE port 0)
/0/100/4/0       eth0        network     RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/7                     bridge      RS780 PCI to PCI bridge (PCIE port 3)
/0/100/7/0       wlan0       network     AR9285 Wireless Network Adapter (PCI-Express)
/0/100/11        scsi2       storage     SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
/0/100/11/0      /dev/sda    disk        500GB WDC WD5000BEVT-5
/0/100/11/0/1    /dev/sda1   volume      9791MiB Windows NTFS volume
/0/100/11/0/2    /dev/sda2   volume      100MiB Windows NTFS volume
/0/100/11/0/3    /dev/sda3   volume      236GiB Windows NTFS volume
/0/100/11/0/4    /dev/sda4   volume      219GiB Extended partition
/0/100/11/0/4/5  /dev/sda5   volume      488MiB Linux filesystem partition
/0/100/11/0/4/6  /dev/sda6   volume      19GiB Linux filesystem partition
/0/100/11/0/4/7  /dev/sda7   volume      6640MiB Linux swap / Solaris partition
/0/100/11/0/4/8  /dev/sda8   volume      193GiB Linux filesystem partition
/0/100/11/1      /dev/cdrom  disk        DVD RW AD-7710H
/0/100/12                    bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/12.2                  bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/13                    bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/13.2                  bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/14                    bus         SBx00 SMBus Controller
/0/100/14.1                  storage     SB7x0/SB8x0/SB9x0 IDE Controller
/0/100/14.2                  multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3                  bridge      SB7x0/SB8x0/SB9x0 LPC host controller
/0/100/14.4                  bridge      SBx00 PCI to PCI Bridge
/0/100/14.5                  bus         SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
/0/100/15                    bridge      ATI Technologies Inc
/0/100/16                    bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/16.2                  bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/101                       bridge      Family 10h Processor HyperTransport Configuration
/0/102                       bridge      Family 10h Processor Address Map
/0/103                       bridge      Family 10h Processor DRAM Controller
/0/104                       bridge      Family 10h Processor Miscellaneous Control
/0/105                       bridge      Family 10h Processor Link Control
/0/1             scsi4       storage     
/0/1/0.0.0       /dev/sdb    disk        500GB SCSI Disk
/0/1/0.0.0/1     /dev/sdb1   volume      465GiB Windows NTFS volume
/0/2             scsi5       storage     
/0/2/0.0.0       /dev/sdc    disk        SCSI Disk
/0/2/0.0.1       /dev/sdd    disk        SCSI Disk
total 0
crw-rw----+  1 root audio 116, 33 2011-06-04 19:40 timer
crw-rw----+  1 root audio 116,  1 2011-06-04 19:40 seq
crw-rw----+  1 root audio 116,  4 2011-06-04 19:40 hwC0D0
crw-rw----+  1 root audio 116,  5 2011-06-04 19:40 controlC0
drwxr-xr-x   3 root root      240 2011-06-04 19:40 .
crw-rw----+  1 root audio 116,  7 2011-06-04 19:40 hwC1D0
crw-rw----+  1 root audio 116,  8 2011-06-04 19:40 controlC1
drwxr-xr-x   2 root root       80 2011-06-04 19:40 by-path
crw-rw----+  1 root audio 116,  6 2011-06-04 19:41 pcmC1D3p
crw-rw----+  1 root audio 116,  3 2011-06-04 20:06 pcmC0D0c
crw-rw----+  1 root audio 116,  2 2011-06-04 20:17 pcmC0D0p
drwxr-xr-x  19 root root     4520 2011-06-04 20:23 ..
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601]
00:01.0 PCI bridge [0604]: Sony Corporation Device [104d:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) [1022:9607]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:15.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a0]
00:16.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:16.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
01:05.1 Audio device [0403]: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] [1002:970f]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
09:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
/sbin/alsactl
Specified filename /dev/dsp does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  cameron    1631 F.... pulseaudio
dpkg-query: no path found matching pattern *bin/slmodemd*.
[    0.156409] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.161777] ACPI: No dock devices found.
[    0.161779] HEST: Table not found.
[    0.207724] pnp: PnP ACPI: found 10 devices
[    0.356485] audit: initializing netlink socket (disabled)
[    0.356495] type=2000 audit(1307216437.356:1): initialized
[    0.375149] ERST: Table is not found!
[    0.754574] isapnp: No Plug & Play device found
[    0.990757] Fixed MDIO Bus: probed
[    0.991074] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.000268] hub 1-0:1.0: USB hub found
[    1.000489] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.012270] hub 2-0:1.0: USB hub found
[    1.012494] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.024266] hub 3-0:1.0: USB hub found
[    1.084250] hub 4-0:1.0: USB hub found
[    1.148239] hub 5-0:1.0: USB hub found
[    1.208199] hub 6-0:1.0: USB hub found
[    1.268225] hub 7-0:1.0: USB hub found
[    1.270764] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.271954] powernow-k8: Found 1 AMD Athlon(tm) II P360 Dual-Core Processor (2 cpu cores) (version 2.20.00)
[    1.272626] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    7.732535] lp: driver loaded but no devices found
[    8.789040] type=1400 audit(1307205646.014:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=557 comm="apparmor_parser"
[    8.789061] type=1400 audit(1307205646.014:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=586 comm="apparmor_parser"
[    8.789383] type=1400 audit(1307205646.014:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=557 comm="apparmor_parser"
[    8.789412] type=1400 audit(1307205646.014:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=586 comm="apparmor_parser"
[    8.789604] type=1400 audit(1307205646.014:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=557 comm="apparmor_parser"
[    8.789639] type=1400 audit(1307205646.014:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=586 comm="apparmor_parser"
[    8.864409] uvcvideo: Found UVC 1.00 device Sony Visual Communication Camera (064e:03f5)
[   11.110882] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[   11.110997] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[   14.770974] type=1400 audit(1307205651.994:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=925 comm="apparmor_parser"
[   14.771339] type=1400 audit(1307205651.994:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=925 comm="apparmor_parser"
[   14.771565] type=1400 audit(1307205651.994:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=925 comm="apparmor_parser"
[   14.876310] type=1400 audit(1307205652.102:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=926 comm="apparmor_parser"
[   14.880982] type=1400 audit(1307205652.106:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=926 comm="apparmor_parser"
[   14.883728] type=1400 audit(1307205652.106:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=926 comm="apparmor_parser"
[   14.923806] type=1400 audit(1307205652.146:14): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=924 comm="apparmor_parser"
[   15.035461] type=1400 audit(1307205652.258:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=928 comm="apparmor_parser"
[   15.035883] type=1400 audit(1307205652.258:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=928 comm="apparmor_parser"
[   15.067519] type=1400 audit(1307205652.290:17): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=929 comm="apparmor_parser"
[   30.546076] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
sudo: /etc/init.d/sl-modem-daemon: command not found
/etc/modprobe.d/alsa-base.conf:options snd-hda-intel model=lenovo-101e
    Manufacturer: Sony Corporation
    Product Name: VPCEE42FX
    Manufacturer: Sony Corporation
    Product Name: VAIO
    Manufacturer: Sony Corporation
    Manufacturer: AuthenticAMD
snd_seq_dummy          12686  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  1 
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
  *-multimedia            
       description: Audio device
       product: RS880 Audio Device [Radeon HD 4200]
       vendor: ATI Technologies Inc
       physical id: 5.1
       bus info: pci@0000:01:05.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:19 memory:f4210000-f4213fff
  *-multimedia
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 40
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:16 memory:f4300000-f4303fff

```

---

### Post by camtom12 on 2011-06-04
And one last thing if it helps...

In Windows my sound driver is:
Provider: Realtek Semiconductor Corp.
Date: 3/17/2010
Version: 6.0.1.6069

Not sure if that'll help or not but I'm at a loss!

Thanks again for any help!

---

### Post by camtom12 on 2011-06-04
Aaaaaaand I may have taken a step backwards.  I downloaded alsa-driver_1.0.24+dfsg-0ubuntu1.dsc and can't figure out how to load it!  I did manage to uninstall my mis-matched 1.0.23 driver though.  now my output looks like this:
```
bash alsa-info.sh --stdout
cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
grep: /proc/asound/cards: No such file or directory
/usr/sbin/alsactl: save_state:1519: No soundcards found...
cat: /tmp/alsa-info.JbOZx23hoM/alsactl.tmp: No such file or directory
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Jun  4 18:24:19 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"


!!DMI Information
!!---------------

Manufacturer:      Sony Corporation
Product Name:      VPCEE42FX
Product Version:   C105867M


!!Kernel Information
!!------------------

Kernel release:    2.6.38-8-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         athlon
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------



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



!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383 (rev 40)
    Subsystem: 104d:9077
--
01:05.1 0403: 1002:970f
    Subsystem: 104d:9077


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
snd-hda-intel: model=lenovo-101e


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw------- 1 root root 116,  1 Jun  4 21:20 /dev/snd/seq
crw------- 1 root root 116, 33 Jun  4 21:20 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:240: no soundcards found...

ARECORD

arecord: device_list:240: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
parport_pc
ppdev
vesafb
arc4
ath9k
joydev
mac80211
ath9k_common
ath9k_hw
ath
fglrx
cfg80211
uvcvideo
videodev
soundcore
snd_page_alloc
psmouse
serio_raw
k10temp
sony_laptop
shpchp
sp5100_tco
i2c_piix4
video
lp
parport
usbhid
hid
usb_storage
uas
pata_atiixp
ahci
r8169
libahci


!!ALSA/HDA dmesg
!!------------------

[   14.061410] cfg80211: Calling CRDA to update world regulatory domain
[   14.110770] snd: Unknown symbol unregister_sound_special (err 0)
[   14.111109] snd: Unknown symbol register_sound_special_device (err 0)
[   14.111739] snd: Unknown symbol unregister_sound_special (err 0)
[   14.121505] snd_timer: Unknown symbol snd_info_register (err 0)
--
[   14.122617] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)
[   14.134548] snd: Unknown symbol register_sound_special_device (err 0)
[   14.136243] snd_timer: Unknown symbol snd_info_register (err 0)
--
[   14.137359] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)
[   14.177215] snd: Unknown symbol unregister_sound_special (err 0)
[   14.177541] snd: Unknown symbol register_sound_special_device (err 0)
[   14.182297] snd_timer: Unknown symbol snd_info_register (err 0)
--
[   14.183471] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)
[   14.201259] snd: Unknown symbol unregister_sound_special (err 0)
[   14.201584] snd: Unknown symbol register_sound_special_device (err 0)
[   14.203111] snd_timer: Unknown symbol snd_info_register (err 0)

```

---

### Post by camtom12 on 2011-06-04
Solved!!!  I'm not entirely sure how I did it all, but I ran the alsa update again after somehow deleting the driver and now I've got audio!

---

