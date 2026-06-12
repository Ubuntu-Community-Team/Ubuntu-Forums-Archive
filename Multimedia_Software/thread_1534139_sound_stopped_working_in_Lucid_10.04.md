---
title: "sound stopped working in Lucid 10.04"
date: 2010-07-19
forum: Multimedia Software
---

### Post by stuque on 2010-07-19
My sound in Lucid was working fine (for months), and then, for no obvious reason, it stopped working today. I get no sound from any application. I have no idea what could have changed on my system to cause this.

When I re-boot Lucid, the login sound plays, and sound works briefly, but it always stops eventually after I login.

I am overwhelmed by the large number of different Ubuntu sound problem fixes, and none seem to help.

Any advice about what to do?

---

### Post by rewritems on 2010-07-20
I had the exact same problem... except nobody ever helped me, and I had to fix it myself. Difference here is I'm gonna help you. I need you to run this command:

```
cat /proc/asound/card0/codec#* | grep Codec
```

EDIT: I forgot to say, haha, give me the output of it. Also, what's the computer manufacturer? (hp, dell, etc)

---

### Post by bjarkih on 2010-07-21
I  have the same problem on a HP CQ61-414  Sound works fine for some hours after bootup but the dies :-(  I ran 
cat /proc/asound/card0/codec#* | grep Codec and got:
Codec: IDT 92HD75B2X5
Codec: Intel G45 DEVCTG

---

### Post by rewritems on 2010-07-21
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Open up a terminal and type:

```

sudo gedit /etc/modprobe.d/alsa-base.conf

```
(you could always use vi but I bet it'd be too confusing)

So after that, enter your password. Then, at the very bottom of that file, type this in:

```

options snd-hda-intel model=(model)

```
(model) is the model of your laptop. I'm positive it would "hp-cq61", so go ahead and replace "(model)" with that

---

### Post by bjarkih on 2010-07-21
Thank you, it seems to work after 4 hours so I'm hopefull :-)

---

### Post by rewritems on 2010-07-22
I'm happy to help. Update me on whether it worked or not the rest of the day.

---

### Post by bjarkih on 2010-07-22
It's still working the morning after, I left the computer running over night.

---

### Post by rewritems on 2010-07-24
> **bjarkih said:**
> It's still working the morning after, I left the computer running over night.

So would you say I helped you? :D If so, you're the first person I helped here on ubuntu forums :D

---

### Post by bjarkih on 2010-07-25
The sound has dissapeared again in a misterous way :-(

---

### Post by lidex on 2010-07-26
This is like a bad movie. Remove any custom entries from alsa-base.conf and update your system:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
**Reboot**
Now this. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by bjarkih on 2010-07-26
> **lidex said:**
> This is like a bad movie. Remove any custom entries from alsa-base.conf and update your system:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```**Reboot**
Now this. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```Enter your user password when prompted. Provide a link for the output or post it here using code tags.

Thank you for the help.  Here's a copy/paste of the Output since I'm new to Linux and have no idea what's usefull and what isin't :oops:
[qoute]upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Mon Jul 26 15:15:58 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      Compaq Presario CQ61 Notebook PC


!!Kernel Information
!!------------------

Kernel release:    2.6.32-24-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
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
                      HDA Intel at 0xd4500000 irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
    Subsystem: 103c:3069


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
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : 0
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: IDT 92HD75B2X5
Address: 0
Function Id: 0x1
Vendor Id: 0x111d7608
Subsystem Id: 0x103c3069
Revision Id: 0x100202
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=8, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[4]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[5]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[6]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[7]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Power-Map: 0x00
Analog Loopback: 0x00
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0121101f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Connection: 3
     0x10 0x11* 0x17
Node 0x0b [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01a11020: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
Node 0x0c [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x92a71130: [Fixed] Mic at Int Front
    Conn = Analog, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x90110110: [Fixed] Speaker at Int N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 3
     0x10* 0x11 0x17
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x40f000f9: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x9
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
Node 0x0f [Vendor Defined Widget] wcaps 0xf00181: Stereo
  Unsolicited: tag=00, enabled=0
  Connection: 3
     0x10 0x11 0x17*
Node 0x10 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x11 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x12 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D3, actual=D3
  Delay: 13 samples
  Connection: 1
     0x1c
  Processing caps: benign=0, ncoeff=0
Node 0x13 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x1d
  Processing caps: benign=0, ncoeff=0
Node 0x14 [Pin Complex] wcaps 0x400100: Mono
  Pincap 0x00000030: IN OUT
  Pin Default 0x40f000f1: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x1
  Pin-ctls: 0x00:
  Connection: 1
     0x16
Node 0x15 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x10 0x11 0x17*
Node 0x16 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x15
Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 5
     0x10 0x11 0x14 0x1a 0x1b
Node 0x18 [Pin Complex] wcaps 0x40000b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40f000f2: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x2
  Pin-ctls: 0x00:
Node 0x19 [Vendor Defined Widget] wcaps 0xf0000b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals: 
Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 3
     0x0b 0x0c* 0x0e
Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 3
     0x0b* 0x0c 0x0e
Node 0x1c [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x8f 0x8f]
  Connection: 4
     0x1a* 0x17 0x18 0x19
Node 0x1d [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 4
     0x1b* 0x17 0x18 0x19
Node 0x1e [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f4: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x4
  Pin-ctls: 0x00:
  Connection: 1
     0x24
Node 0x1f [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00010010: OUT EAPD
  EAPD 0x0:
  Pin Default 0x40f000f5: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x5
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
  Connection: 2
     0x24* 0x25
Node 0x20 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f6: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x6
  Pin-ctls: 0x00:
  Connection: 1
     0x25
Node 0x21 [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x22 [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x23 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x21* 0x1c 0x1d
Node 0x25 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x22* 0x1c 0x1d
Node 0x26 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
Node 0x27 [Volume Knob Widget] wcaps 0x600000: Mono
  Volume-Knob: delta=1, steps=127, direct=0, val=127
  Connection: 2
     0x10 0x11
Codec: Intel G45 DEVCTG
Address: 3
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
  Converter: stream=0, channel=0
  Digital:
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
  Unsolicited: tag=08, enabled=1
  Connection: 1
     0x02
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 9 Jul 26 15:11 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 8 Jul 26 15:11 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 7 Jul 26 15:11 /dev/snd/hwC0D3
crw-rw----+ 1 root audio 116, 6 Jul 26 15:11 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 5 Jul 26 15:11 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 4 Jul 26 15:11 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116, 3 Jul 26 15:10 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Jul 26 15:10 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jul 26 15:11 .
drwxr-xr-x 3 root root 220 Jul 26 15:11 ..
lrwxrwxrwx 1 root root  12 Jul 26 15:11 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xd4500000 irq 22'
  Mixer name    : 'Intel G45 DEVCTG'
  Components    : 'HDA:111d7608,103c3069,00100202 HDA:80862802,80860101,00100000'
  Controls      : 18
  Simple ctrls  : 10
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
Simple mixer control 'Speaker',0
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
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Mic In'
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [off]
  Front Right: Capture 15 [100%] [22.50dB] [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Mux',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'PC Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 64'
        comment.dbmin -4800
        comment.dbmax 0
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 64
        value.1 64
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Speaker Playback Switch'
        value.0 true
        value.1 true
    }
    control.3 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'Mic In'
        comment.item.1 'Line In'
        iface MIXER
        name 'Mic Jack Mode'
        value 'Mic In'
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PC Beep Playback Switch'
        value false
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 3'
        comment.dbmin -1800
        comment.dbmax 0
        iface MIXER
        name 'PC Beep Playback Volume'
        value 0
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 64'
        comment.dbmin -4800
        comment.dbmax 0
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 64
        value.1 64
    }
    control.7 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 15'
        comment.dbmin 0
        comment.dbmax 2250
        iface MIXER
        name 'Capture Volume'
        value.0 15
        value.1 15
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 false
        value.1 false
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3000
        iface MIXER
        name 'Mux Capture Volume'
        value.0 0
        value.1 0
    }
    control.11 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 64'
        comment.dbmin -4800
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value 64
    }
    control.12 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.13 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.14 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.15 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value false
    }
    control.17 {
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
    control.18 {
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
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
ppdev
snd_hda_codec_intelhdmi
snd_hda_codec_idt
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
fbcon
tileblit
snd_pcm
font
arc4
bitblit
softcursor
snd_seq_dummy
joydev
snd_seq_oss
ath9k
vga16fb
snd_seq_midi
vgastate
snd_rawmidi
mac80211
snd_seq_midi_event
snd_seq
ath
i915
snd_timer
drm_kms_helper
uvcvideo
snd_seq_device
videodev
intel_agp
drm
v4l1_compat
cfg80211
snd
led_class
i2c_algo_bit
psmouse
agpgart
serio_raw
video
lp
output
soundcore
snd_page_alloc
parport
usbhid
hid
ahci
r8169
mii


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x0a 0x0121101f
0x0b 0x01a11020
0x0c 0x92a71130
0x0d 0x90110110
0x0e 0x40f000f9
0x14 0x40f000f1
0x18 0x40f000f2
0x1e 0x40f000f4
0x1f 0x40f000f5
0x20 0x40f000f6

/sys/class/sound/hwC0D0/driver_pin_configs:
0x0f 0x40f000f0
0x19 0x40f000f3

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D3/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D3/driver_pin_configs:

/sys/class/sound/hwC0D3/user_pin_configs:

/sys/class/sound/hwC0D3/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   16.538307]   alloc kstat_irqs on node -1
[   16.538313] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.538353] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.640668] ADDRCONF(NETDEV_UP): wlan0: link is not ready
--
[   16.644608] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.677171] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   16.720635] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   16.720716] input: HDA Intel HP Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   17.229371] ppdev: user-space parallel port driver

[/qoute]

---

### Post by lidex on 2010-07-26
OK. Follow the alsa-upgrade link in my sig to get v 1.0.23 and report your results please. One aside here: when posting blocks of text it's helpful to highlight the text and click the # in the editor toolbar to wrap in code tags ;)

---

### Post by bjarkih on 2010-07-28
Everything went well and the sound is working fine :-)  Thank's for the help.  Now I only hope that I won't need to post here again ;-)

---

### Post by defaria on 2010-08-07
My sound broke with the kernel upgrade to 2.6.32-24. Lidex you helped me out immensely last time. Note I had ALSA 1.0.23 before and had compiled it (driver, lib and utils). So I figured "Uh oh, the kernel updated - time to recompile ALSA 1.0.23 again". In the past this worked fine so I compiled and rebooted as always and the sound was lethargic at first and broken soon after. Even had poltikd hogging my memory. Interestingly cat /proc/asound/version is saying I have 1.0.22.1! 

So I decided to do try the AlsaUpgrade script But I could not compile the alsa driver. Complained about no Makefile or something like that. I've seen this error before being as I have an AMD 64 bit machine. The fixes I've seen are to either make ARCH=x86 or symlink /usr/src/linux-headers-2.6.32-24-generic/arch/linux -> x86. But alas that doesn't work in this case. I get:

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/hrtimer.o
Arch linux is not supported with CONFIG_FTRACE_MCOUNT_RECORD at /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl line 249.
make[3]: *** [/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/hrtimer.o] Error 255
```

I changed the make's in AlsaUpgrade-1.0.23-2.sh to have ARCH=x86 and that seemed to do the trick. Maybe you should add some code checking uname -m to see if it says x86_64 and if so add ARCH=x86 to the make's? (Why don't they (kernel build team) fix this?)

OK, the install finished and by accident I started a video in Chrome without thinking and wham it started playing with sound! This is promising!!! However time to reboot to make this complete.

I also want to do this on my HP dv7 also running Ubuntu 10.04 and recently updated that to 2.6.32-24 and also suffers from broken sound...

---

### Post by defaria on 2010-08-07
Once again Lidex - you da man! All back up or as back up as I used to be (Note: Have not checked the HDMI yet - I'll report back if it fails).

---

### Post by defaria on 2010-08-07
Well I spoke too soon. It just up and broke! I rebooted but it didn't fix it. Instead audio would play for a little bit of time but then stop. I've also seen many pulseaudio processes running in the background (many started from sounds from various apps such as pidgin, etc.). Now it thinks I have no sound card.

EDIT: I did AlsaUpgrade-1.0.23-2.sh -i step again and rebooted and I'm back. I wonder if it will break again...

Doing service alsasound stop yields:

```
Shutting down sound driver: ERROR: Module snd_usb_audio is in use
ERROR: Module snd_usbmidi_lib is in use by snd_usb_audio
ERROR: Module snd_hda_codec_realtek is in use
ERROR: Module snd_hda_codec is in use by snd_hda_codec_realtek
ERROR: Module snd_hwdep is in use by snd_usb_audio,snd_hda_codec
ERROR: Module snd_pcm is in use by snd_usb_audio,snd_hda_codec
ERROR: Module snd_rawmidi is in use by snd_usbmidi_lib
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_seq_device is in use by snd_rawmidi
ERROR: Module snd is in use by snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_timer,snd_seq_device
done
```

Here's the output from alsa-info.sh:

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sun Aug  8 01:42:07 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      HP-Pavilion
Product Name:      FQ563AA-ABA a6750f


!!Kernel Information
!!------------------

Kernel release:    2.6.32-24-generic
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
snd_usb_audio


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 1 [CinemaTM       ]: USB-Audio - Microsoft<C2><AE> LifeCam Cinema(TM)

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 1 [CinemaTM       ]: USB-Audio - Microsoft<C2><AE> LifeCam Cinema(TM)
                      Microsoft Microsoft<C2><AE> LifeCam Cinema(TM) at usb-0000:00:12.2-2, high speed


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383
        Subsystem: 103c:2a7f


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
snd-hda-intel: model=dv5
snd-hda-intel: enable_msi=0 probe_mask=0xffff,0xfff2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
        bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1
        beep_mode : 1,1,1,1,1,1,1,1
        enable : Y,Y,Y,Y,Y,Y,Y,Y
        enable_msi : 0
        id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
        index : -1,-1,-1,-1,-1,-1,-1,-1
        model : dv5,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
        patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
        position_fix : 0,0,0,0,0,0,0,0
        power_save : 0
        power_save_controller : Y
        probe_mask : 65535,65522,-1,-1,-1,-1,-1,-1
        probe_only : 0,0,0,0,0,0,0,0
        single_cmd : N

!!Module: snd_usb_audio
        async_unlink : Y
        device_setup : 0,0,0,0,0,0,0,0
        enable : Y,Y,Y,Y,Y,Y,Y,Y
        id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
        ignore_ctl_error : N
        index : -2,-1,-1,-1,-1,-1,-1,-1
        nrpacks : 8
        pid : -1,-1,-1,-1,-1,-1,-1,-1
        vid : -1,-1,-1,-1,-1,-1,-1,-1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC1200
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0888
Subsystem Id: 0x103c2a7f
Revision Id: 0x100101
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
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC1200 Analog", type="Audio", device=0
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
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC1200 Digital", type="SPDIF", device=1
  Converter: stream=5, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC1200 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1f 0x1f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Device: name="ALC1200 Analog", type="Audio", device=2
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
    rates [0x160]: 44100 48000 96000
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
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
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
  Amp-Out vals:  [0x14 0x14]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x14 0x14]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=In, idx=2, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x15 0x15]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Side Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Side Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x15 0x15]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x11 [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x10
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
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
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
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
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
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
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
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
  Pin Default 0x01a19840: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a1984f: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0xf
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
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02214020: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x01813050: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01446130: [Jack] SPDIF Out at Ext Rear
    Conn = RCA, Color = Orange
    DefAssociation = 0x3, Sequence = 0x0
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
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=0, device=0
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
--endcollapse--


!!USB Mixer information
!!---------------------------
--startcollapse--

USB Mixer: usb_id=0x045e075d, ctrlif=2, ctlerr=0
Card: Microsoft Microsoft<C2><AE> LifeCam Cinema(TM) at usb-0000:00:12.2-2, high speed
  Unit: 5
    Control: name="Mic Capture Volume", index=0
    Info: id=5, control=2, cmask=0x1, channels=1, type="S16"
    Volume: min=-5120, max=9216, dBmin=-2000, dBmax=3600
  Unit: 5
    Control: name="Mic Capture Switch", index=0
    Info: id=5, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  0 Aug  7 18:27 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 32 Aug  7 18:27 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  4 Aug  7 18:27 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 24 Aug  7 18:32 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 16 Aug  7 18:36 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 17 Aug  7 18:32 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 26 Aug  7 18:27 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116, 56 Aug  7 18:32 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  1 Aug  7 18:27 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Aug  7 18:27 /dev/snd/timer

/dev/snd/by-id:
total 0
drwxr-xr-x 2 root root  60 Aug  7 18:27 .
drwxr-xr-x 4 root root 280 Aug  7 18:27 ..
lrwxrwxrwx 1 root root  12 Aug  7 18:27 usb-Microsoft_Microsoft<C2><AE>_LifeCam_Cinema_TM_-02 -> ../controlC1

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Aug  7 18:27 .
drwxr-xr-x 4 root root 280 Aug  7 18:27 ..
lrwxrwxrwx 1 root root  12 Aug  7 18:27 pci-0000:00:12.2-usb-0:2:1.2 -> ../controlC1
lrwxrwxrwx 1 root root  12 Aug  7 18:27 pci-0000:00:14.2 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CinemaTM [Microsoft<C2><AE> LifeCam Cinema(TM)], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0xfe024000 irq 16'
  Mixer name    : 'Realtek ALC1200'
  Components    : 'HDA:10ec0888,103c2a7f,00100101'
  Controls      : 33
  Simple ctrls  : 19
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 21 [68%] [-15.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
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
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 30 [97%] [-1.50dB] [on]
  Front Right: Playback 30 [97%] [-1.50dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
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
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 30 [97%] [-1.50dB] [on]
  Front Right: Playback 30 [97%] [-1.50dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
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
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'

!!-------Mixer controls for card 1 [CinemaTM]

Card hw:1 'CinemaTM'/'Microsoft Microsoft<C2><AE> LifeCam Cinema(TM) at usb-0000:00:12.2-2, high speed'
  Mixer name    : 'USB Mixer'
  Components    : 'USB045e:075d'
  Controls      : 2
  Simple ctrls  : 1
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 56
  Mono: Capture 54 [96%] [34.00dB] [on]


!!Alsactl output
!!-------------

--startcollapse--
state.SB {
        control.1 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                comment.dbmin -4650
                comment.dbmax 0
                iface MIXER
                name 'Front Playback Volume'
                value.0 30
                value.1 30
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
                comment.dbmin -4650
                comment.dbmax 0
                iface MIXER
                name 'Surround Playback Volume'
                value.0 30
                value.1 30
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
                comment.range '0 - 31'
                comment.dbmin -4650
                comment.dbmax 0
                iface MIXER
                name 'Center Playback Volume'
                value 31
        }
        control.6 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 1
                comment.range '0 - 31'
                comment.dbmin -4650
                comment.dbmax 0
                iface MIXER
                name 'LFE Playback Volume'
                value 31
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
                comment.range '0 - 31'
                comment.dbmin -4650
                comment.dbmax 0
                iface MIXER
                name 'Side Playback Volume'
                value.0 31
                value.1 31
        }
        control.10 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Side Playback Switch'
                value.0 true
                value.1 true
        }
        control.11 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Headphone Playback Switch'
                value.0 true
                value.1 true
        }
        control.12 {
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
        control.13 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Mic Playback Switch'
                value.0 false
                value.1 false
        }
        control.14 {
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
        control.15 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Front Mic Playback Switch'
                value.0 false
                value.1 false
        }
        control.16 {
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
        control.17 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Line Playback Switch'
                value.0 false
                value.1 false
        }
        control.18 {
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
        control.19 {
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
        control.20 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Capture Switch'
                value.0 true
                value.1 true
        }
        control.21 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Capture Switch'
                index 1
                value.0 true
                value.1 true
        }
        control.22 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                comment.dbmin -1650
                comment.dbmax 3000
                iface MIXER
                name 'Capture Volume'
                value.0 31
                value.1 31
        }
        control.23 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                comment.dbmin -1650
                comment.dbmax 3000
                iface MIXER
                name 'Capture Volume'
                index 1
                value.0 0
                value.1 0
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
                value Mic
        }
        control.25 {
                comment.access 'read write'
                comment.type ENUMERATED
                comment.count 1
                comment.item.0 Mic
                comment.item.1 'Front Mic'
                comment.item.2 Line
                iface MIXER
                name 'Input Source'
                index 1
                value Mic
        }
        control.26 {
                comment.access read
                comment.type IEC958
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Con Mask'
                value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        }
        control.27 {
                comment.access read
                comment.type IEC958
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Pro Mask'
                value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        }
        control.28 {
                comment.access 'read write'
                comment.type IEC958
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Default'
                value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        }
        control.29 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Switch'
                value false
        }
        control.30 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'IEC958 Default PCM Playback Switch'
                value true
        }
        control.31 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 1
                comment.range '0 - 31'
                comment.dbmin -4650
                comment.dbmax 0
                iface MIXER
                name 'Master Playback Volume'
                value 21
        }
        control.32 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'Master Playback Switch'
                value true
        }
        control.33 {
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
}
state.CinemaTM {
        control.1 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'Mic Capture Switch'
                value true
        }
        control.2 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 1
                comment.range '0 - 56'
                comment.dbmin -2000
                comment.dbmax 3600
                iface MIXER
                name 'Mic Capture Volume'
                value 54
        }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
snd_usb_audio
snd_usbmidi_lib
snd_hda_codec_realtek
vmnet
ppdev
parport_pc
vmblock
vsock
vmci
vmmon
arc4
snd_hda_intel
snd_seq_dummy
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_seq_oss
snd_pcm
snd_seq_midi
snd_rawmidi
nfsd
exportfs
snd_seq_midi_event
snd_seq
nfs
lockd
nfs_acl
snd_timer
snd_seq_device
auth_rpcgss
rt73usb
crc_itu_t
rt2x00usb
rt2x00lib
led_class
mac80211
sunrpc
uvcvideo
fbcon
tileblit
videodev
font
v4l1_compat
bitblit
softcursor
v4l2_compat_ioctl32
snd
psmouse
cfg80211
serio_raw
nvidia
vga16fb
vgastate
i2c_piix4
edac_core
edac_mce_amd
soundcore
snd_page_alloc
lp
parport
usbhid
hid
usb_storage
ohci1394
ieee1394
pata_atiixp
r8169
mii
ahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x411111f0
0x14 0x01014010
0x15 0x01011012
0x16 0x01016011
0x17 0x01012014
0x18 0x01a19840
0x19 0x02a1984f
0x1a 0x411111f0
0x1b 0x02214020
0x1c 0x01813050
0x1d 0x411111f0
0x1e 0x01446130
0x1f 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   42.015706] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   42.080491] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   42.080495] hda_intel: codec_mask forced to 0xff
[   42.085360] Console: switching to colour frame buffer device 80x30
--
[   44.961154] bridge-eth0: attached
[   45.163763] ALSA hda_intel.c:712: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   46.010014] /dev/vmnet: open called by PID 1496 (vmnet-dhcpd)
--
[   46.163330] NFSD: starting 90-second grace period
[   46.170012] ALSA hda_intel.c:1420: Codec #1 probe error; disabling it...
[   47.260008] ALSA hda_intel.c:1420: Codec #2 probe error; disabling it...
[   48.350823] ALSA hda_intel.c:1420: Codec #3 probe error; disabling it...
[   48.523274] hda_codec: ALC1200: SKU not ready 0x411111f0
[   48.523358] hda_codec: ALC1200: BIOS auto-probing.
[   48.524785] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input6
[   50.072636] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   50.108747] usbcore: registered new interface driver snd-usb-audio
[   50.266733] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   51.393806] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   52.471255] eth0: no IPv6 routers present
[   52.512632] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   54.810148] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   55.930096] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   56.102419] vmnet8: no IPv6 routers present
[   56.620835] vmnet1: no IPv6 routers present
[   60.010084] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   61.130161] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   65.220152] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   66.340097] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   70.360094] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   71.480042] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   75.671390] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   76.800089] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   80.811335] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   81.940159] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   85.890039] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   87.010112] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   90.980123] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   92.100071] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   96.130066] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   97.250142] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  101.260138] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  102.380093] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  106.561314] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  107.690137] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  111.720137] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  112.840085] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  116.920071] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  118.040148] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  118.386179] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[  122.080148] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  123.210096] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  127.341323] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  128.470151] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  132.551388] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  133.680084] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  137.763825] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  138.900146] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  143.040125] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  144.170072] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  147.082520] rpcbind: server mars not responding, timed out
[  148.390165] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  149.520111] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  153.671340] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  154.800163] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  158.890150] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  160.020105] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  164.120082] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  165.250154] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  169.323893] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  170.460092] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  174.521333] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  175.650152] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  179.831378] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  180.960074] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  185.041313] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  186.170135] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  190.271972] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  191.400191] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  192.711363] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  193.840067] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  197.990167] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  199.120118] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  203.180110] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  204.311302] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  208.391416] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  209.520118] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  213.691339] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  214.820164] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  218.901403] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  220.030101] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  224.070095] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  225.200167] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  229.360141] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  230.490087] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  234.640196] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  235.770137] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  239.930118] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  241.060067] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  245.270153] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  246.400106] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  250.590076] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  251.720152] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  255.820135] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  256.950081] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  260.990078] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  262.122023] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  266.281997] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  267.410077] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  271.630164] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  272.750119] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  276.872596] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  278.010172] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  282.230137] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  283.360083] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  287.551181] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  288.682631] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  292.750118] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  293.881312] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  297.931433] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  299.060133] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  303.120172] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  304.250090] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  308.282630] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  309.410048] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  313.840142] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  314.972565] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  319.130078] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  320.260128] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  324.380148] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  325.501326] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  908.422583] ALSA hda_intel.c:751: hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x001f000a
```

---

### Post by lidex on 2010-08-08
> **defaria said:**
> Well I spoke too soon. It just up and broke! I rebooted but it didn't fix it. Instead audio would play for a little bit of time but then stop. I've also seen many pulseaudio processes running in the background (many started from sounds from various apps such as pidgin, etc.). Now it thinks I have no sound card.

EDIT: I did AlsaUpgrade-1.0.23-2.sh -i step again and rebooted and I'm back. I wonder if it will break again...

Doing service alsasound stop yields:

```
Shutting down sound driver: ERROR: Module snd_usb_audio is in use
ERROR: Module snd_usbmidi_lib is in use by snd_usb_audio
ERROR: Module snd_hda_codec_realtek is in use
ERROR: Module snd_hda_codec is in use by snd_hda_codec_realtek
ERROR: Module snd_hwdep is in use by snd_usb_audio,snd_hda_codec
ERROR: Module snd_pcm is in use by snd_usb_audio,snd_hda_codec
ERROR: Module snd_rawmidi is in use by snd_usbmidi_lib
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_seq_device is in use by snd_rawmidi
ERROR: Module snd is in use by snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_timer,snd_seq_device
done
```

Here's the output from alsa-info.sh:

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sun Aug  8 01:42:07 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      HP-Pavilion
Product Name:      FQ563AA-ABA a6750f


!!Kernel Information
!!------------------

Kernel release:    2.6.32-24-generic
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
snd_usb_audio


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 1 [CinemaTM       ]: USB-Audio - Microsoft<C2><AE> LifeCam Cinema(TM)

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 1 [CinemaTM       ]: USB-Audio - Microsoft<C2><AE> LifeCam Cinema(TM)
                      Microsoft Microsoft<C2><AE> LifeCam Cinema(TM) at usb-0000:00:12.2-2, high speed


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383
        Subsystem: 103c:2a7f


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
snd-hda-intel: model=dv5
snd-hda-intel: enable_msi=0 probe_mask=0xffff,0xfff2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
        bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1
        beep_mode : 1,1,1,1,1,1,1,1
        enable : Y,Y,Y,Y,Y,Y,Y,Y
        enable_msi : 0
        id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
        index : -1,-1,-1,-1,-1,-1,-1,-1
        model : dv5,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
        patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
        position_fix : 0,0,0,0,0,0,0,0
        power_save : 0
        power_save_controller : Y
        probe_mask : 65535,65522,-1,-1,-1,-1,-1,-1
        probe_only : 0,0,0,0,0,0,0,0
        single_cmd : N

!!Module: snd_usb_audio
        async_unlink : Y
        device_setup : 0,0,0,0,0,0,0,0
        enable : Y,Y,Y,Y,Y,Y,Y,Y
        id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
        ignore_ctl_error : N
        index : -2,-1,-1,-1,-1,-1,-1,-1
        nrpacks : 8
        pid : -1,-1,-1,-1,-1,-1,-1,-1
        vid : -1,-1,-1,-1,-1,-1,-1,-1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC1200
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0888
Subsystem Id: 0x103c2a7f
Revision Id: 0x100101
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
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC1200 Analog", type="Audio", device=0
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
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC1200 Digital", type="SPDIF", device=1
  Converter: stream=5, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC1200 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1f 0x1f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Device: name="ALC1200 Analog", type="Audio", device=2
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
    rates [0x160]: 44100 48000 96000
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
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
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
  Amp-Out vals:  [0x14 0x14]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x14 0x14]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=In, idx=2, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x15 0x15]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Side Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Side Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x15 0x15]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x11 [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x10
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
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
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
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
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
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
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
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
  Pin Default 0x01a19840: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a1984f: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0xf
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
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02214020: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x01813050: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01446130: [Jack] SPDIF Out at Ext Rear
    Conn = RCA, Color = Orange
    DefAssociation = 0x3, Sequence = 0x0
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
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=0, device=0
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
--endcollapse--


!!USB Mixer information
!!---------------------------
--startcollapse--

USB Mixer: usb_id=0x045e075d, ctrlif=2, ctlerr=0
Card: Microsoft Microsoft<C2><AE> LifeCam Cinema(TM) at usb-0000:00:12.2-2, high speed
  Unit: 5
    Control: name="Mic Capture Volume", index=0
    Info: id=5, control=2, cmask=0x1, channels=1, type="S16"
    Volume: min=-5120, max=9216, dBmin=-2000, dBmax=3600
  Unit: 5
    Control: name="Mic Capture Switch", index=0
    Info: id=5, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  0 Aug  7 18:27 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 32 Aug  7 18:27 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  4 Aug  7 18:27 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 24 Aug  7 18:32 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 16 Aug  7 18:36 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 17 Aug  7 18:32 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 26 Aug  7 18:27 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116, 56 Aug  7 18:32 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  1 Aug  7 18:27 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Aug  7 18:27 /dev/snd/timer

/dev/snd/by-id:
total 0
drwxr-xr-x 2 root root  60 Aug  7 18:27 .
drwxr-xr-x 4 root root 280 Aug  7 18:27 ..
lrwxrwxrwx 1 root root  12 Aug  7 18:27 usb-Microsoft_Microsoft<C2><AE>_LifeCam_Cinema_TM_-02 -> ../controlC1

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Aug  7 18:27 .
drwxr-xr-x 4 root root 280 Aug  7 18:27 ..
lrwxrwxrwx 1 root root  12 Aug  7 18:27 pci-0000:00:12.2-usb-0:2:1.2 -> ../controlC1
lrwxrwxrwx 1 root root  12 Aug  7 18:27 pci-0000:00:14.2 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CinemaTM [Microsoft<C2><AE> LifeCam Cinema(TM)], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0xfe024000 irq 16'
  Mixer name    : 'Realtek ALC1200'
  Components    : 'HDA:10ec0888,103c2a7f,00100101'
  Controls      : 33
  Simple ctrls  : 19
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 21 [68%] [-15.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
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
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 30 [97%] [-1.50dB] [on]
  Front Right: Playback 30 [97%] [-1.50dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
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
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 30 [97%] [-1.50dB] [on]
  Front Right: Playback 30 [97%] [-1.50dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
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
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'

!!-------Mixer controls for card 1 [CinemaTM]

Card hw:1 'CinemaTM'/'Microsoft Microsoft<C2><AE> LifeCam Cinema(TM) at usb-0000:00:12.2-2, high speed'
  Mixer name    : 'USB Mixer'
  Components    : 'USB045e:075d'
  Controls      : 2
  Simple ctrls  : 1
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 56
  Mono: Capture 54 [96%] [34.00dB] [on]


!!Alsactl output
!!-------------

--startcollapse--
state.SB {
        control.1 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                comment.dbmin -4650
                comment.dbmax 0
                iface MIXER
                name 'Front Playback Volume'
                value.0 30
                value.1 30
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
                comment.dbmin -4650
                comment.dbmax 0
                iface MIXER
                name 'Surround Playback Volume'
                value.0 30
                value.1 30
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
                comment.range '0 - 31'
                comment.dbmin -4650
                comment.dbmax 0
                iface MIXER
                name 'Center Playback Volume'
                value 31
        }
        control.6 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 1
                comment.range '0 - 31'
                comment.dbmin -4650
                comment.dbmax 0
                iface MIXER
                name 'LFE Playback Volume'
                value 31
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
                comment.range '0 - 31'
                comment.dbmin -4650
                comment.dbmax 0
                iface MIXER
                name 'Side Playback Volume'
                value.0 31
                value.1 31
        }
        control.10 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Side Playback Switch'
                value.0 true
                value.1 true
        }
        control.11 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Headphone Playback Switch'
                value.0 true
                value.1 true
        }
        control.12 {
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
        control.13 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Mic Playback Switch'
                value.0 false
                value.1 false
        }
        control.14 {
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
        control.15 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Front Mic Playback Switch'
                value.0 false
                value.1 false
        }
        control.16 {
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
        control.17 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Line Playback Switch'
                value.0 false
                value.1 false
        }
        control.18 {
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
        control.19 {
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
        control.20 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Capture Switch'
                value.0 true
                value.1 true
        }
        control.21 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Capture Switch'
                index 1
                value.0 true
                value.1 true
        }
        control.22 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                comment.dbmin -1650
                comment.dbmax 3000
                iface MIXER
                name 'Capture Volume'
                value.0 31
                value.1 31
        }
        control.23 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                comment.dbmin -1650
                comment.dbmax 3000
                iface MIXER
                name 'Capture Volume'
                index 1
                value.0 0
                value.1 0
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
                value Mic
        }
        control.25 {
                comment.access 'read write'
                comment.type ENUMERATED
                comment.count 1
                comment.item.0 Mic
                comment.item.1 'Front Mic'
                comment.item.2 Line
                iface MIXER
                name 'Input Source'
                index 1
                value Mic
        }
        control.26 {
                comment.access read
                comment.type IEC958
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Con Mask'
                value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        }
        control.27 {
                comment.access read
                comment.type IEC958
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Pro Mask'
                value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        }
        control.28 {
                comment.access 'read write'
                comment.type IEC958
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Default'
                value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        }
        control.29 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Switch'
                value false
        }
        control.30 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'IEC958 Default PCM Playback Switch'
                value true
        }
        control.31 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 1
                comment.range '0 - 31'
                comment.dbmin -4650
                comment.dbmax 0
                iface MIXER
                name 'Master Playback Volume'
                value 21
        }
        control.32 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'Master Playback Switch'
                value true
        }
        control.33 {
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
}
state.CinemaTM {
        control.1 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'Mic Capture Switch'
                value true
        }
        control.2 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 1
                comment.range '0 - 56'
                comment.dbmin -2000
                comment.dbmax 3600
                iface MIXER
                name 'Mic Capture Volume'
                value 54
        }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
snd_usb_audio
snd_usbmidi_lib
snd_hda_codec_realtek
vmnet
ppdev
parport_pc
vmblock
vsock
vmci
vmmon
arc4
snd_hda_intel
snd_seq_dummy
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_seq_oss
snd_pcm
snd_seq_midi
snd_rawmidi
nfsd
exportfs
snd_seq_midi_event
snd_seq
nfs
lockd
nfs_acl
snd_timer
snd_seq_device
auth_rpcgss
rt73usb
crc_itu_t
rt2x00usb
rt2x00lib
led_class
mac80211
sunrpc
uvcvideo
fbcon
tileblit
videodev
font
v4l1_compat
bitblit
softcursor
v4l2_compat_ioctl32
snd
psmouse
cfg80211
serio_raw
nvidia
vga16fb
vgastate
i2c_piix4
edac_core
edac_mce_amd
soundcore
snd_page_alloc
lp
parport
usbhid
hid
usb_storage
ohci1394
ieee1394
pata_atiixp
r8169
mii
ahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x411111f0
0x14 0x01014010
0x15 0x01011012
0x16 0x01016011
0x17 0x01012014
0x18 0x01a19840
0x19 0x02a1984f
0x1a 0x411111f0
0x1b 0x02214020
0x1c 0x01813050
0x1d 0x411111f0
0x1e 0x01446130
0x1f 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   42.015706] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   42.080491] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   42.080495] hda_intel: codec_mask forced to 0xff
[   42.085360] Console: switching to colour frame buffer device 80x30
--
[   44.961154] bridge-eth0: attached
[   45.163763] ALSA hda_intel.c:712: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   46.010014] /dev/vmnet: open called by PID 1496 (vmnet-dhcpd)
--
[   46.163330] NFSD: starting 90-second grace period
[   46.170012] ALSA hda_intel.c:1420: Codec #1 probe error; disabling it...
[   47.260008] ALSA hda_intel.c:1420: Codec #2 probe error; disabling it...
[   48.350823] ALSA hda_intel.c:1420: Codec #3 probe error; disabling it...
[   48.523274] hda_codec: ALC1200: SKU not ready 0x411111f0
[   48.523358] hda_codec: ALC1200: BIOS auto-probing.
[   48.524785] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input6
[   50.072636] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   50.108747] usbcore: registered new interface driver snd-usb-audio
[   50.266733] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   51.393806] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   52.471255] eth0: no IPv6 routers present
[   52.512632] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   54.810148] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   55.930096] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   56.102419] vmnet8: no IPv6 routers present
[   56.620835] vmnet1: no IPv6 routers present
[   60.010084] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   61.130161] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   65.220152] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   66.340097] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   70.360094] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   71.480042] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   75.671390] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   76.800089] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   80.811335] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   81.940159] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   85.890039] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   87.010112] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   90.980123] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   92.100071] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   96.130066] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   97.250142] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  101.260138] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  102.380093] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  106.561314] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  107.690137] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  111.720137] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  112.840085] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  116.920071] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  118.040148] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  118.386179] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[  122.080148] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  123.210096] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  127.341323] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  128.470151] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  132.551388] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  133.680084] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  137.763825] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  138.900146] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  143.040125] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  144.170072] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  147.082520] rpcbind: server mars not responding, timed out
[  148.390165] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  149.520111] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  153.671340] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  154.800163] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  158.890150] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  160.020105] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  164.120082] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  165.250154] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  169.323893] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  170.460092] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  174.521333] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  175.650152] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  179.831378] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  180.960074] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  185.041313] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  186.170135] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  190.271972] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  191.400191] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  192.711363] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  193.840067] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  197.990167] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  199.120118] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  203.180110] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  204.311302] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  208.391416] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  209.520118] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  213.691339] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  214.820164] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  218.901403] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  220.030101] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  224.070095] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  225.200167] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  229.360141] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  230.490087] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  234.640196] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  235.770137] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  239.930118] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  241.060067] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  245.270153] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  246.400106] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  250.590076] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  251.720152] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  255.820135] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  256.950081] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  260.990078] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  262.122023] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  266.281997] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  267.410077] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  271.630164] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  272.750119] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  276.872596] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  278.010172] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  282.230137] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  283.360083] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  287.551181] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  288.682631] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  292.750118] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  293.881312] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  297.931433] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  299.060133] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  303.120172] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  304.250090] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  308.282630] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  309.410048] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  313.840142] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  314.972565] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  319.130078] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  320.260128] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  324.380148] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  325.501326] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[  908.422583] ALSA hda_intel.c:751: hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x001f000a
```

You have a lot of problems in dmesg. Those entries in alsa-base.conf could be the culprit. Remove them and reboot. Some recent issues with sound "breaking" may be related to your pulse-cookie. No harm in removing that.
```
rm ~/.pulse-cookie
```

---

### Post by defaria on 2010-08-09
I don't have any ~/pulse-cookie to remove.

You say "Those entries in alsa-base.conf could be the culprit". I'm not sure how to associate "messages in dmesg" to "those entries" so that I can remove them.

Here's my alsa-base.conf. The only thing I modified was the last two lines. Which entries should I try removing?

EDIT: Well I commented out everything **except** for the last line and rebooted. Sounds working again. dmesg seems cleaner (I don't claim to be an expert dmesg reader. I can post it if you like). Keeping fingers crossed...

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

# Adding snd-hda-intel: How did this go missing?
options snd-hda-intel model=dv5

```

---

### Post by lidex on 2010-08-09
> **defaria said:**
> I don't have any ~/pulse-cookie to remove.
That's actually ~/.pulse-cookie

> You say "Those entries in alsa-base.conf could be the culprit". I'm not sure how to associate "messages in dmesg" to "those entries" so that I can remove them.
Referring to your alsa-info script output. This is shown in your alsa-base.conf:
```
snd-hda-intel: model=dv5
snd-hda-intel: enable_msi=0 probe_mask=0xffff,0xfff2

```
> Here's my alsa-base.conf. The only thing I modified was the last two lines. Which entries should I try removing? See above.

> EDIT: Well I commented out everything **except** for the last line and rebooted. Sounds working again. dmesg seems cleaner (I don't claim to be an expert dmesg reader. I can post it if you like). Keeping fingers crossed...
You lost me.

---

### Post by defaria on 2010-08-10
> **lidex said:**
> That's actually ~/.pulse-cookie

Argh. My mistake. Note: I did not remove my ~/.pulse-cookie (at least not yet).

> 
Referring to your alsa-info script output. This is shown in your alsa-base.conf:
```
snd-hda-intel: model=dv5
snd-hda-intel: enable_msi=0 probe_mask=0xffff,0xfff2

```
 See above.


Interesting but there is no "snd-hda-intel: enable_msi=0 probe_mask=0xffff,0xfff2" in alsa-base.conf. 

> You lost me.

Sorry. What I did was copy /etc/modprobe/alsa-base.conf to my home directory as alsa-base.conf.save. Then I edited /etc/modprobe/alsa-base.conf such that all lines were commented out - except the last one which was the "sna-hda-intel: model=dv5". I seem to recall that unless I had that in there my sound card would not be recognized at all. I then rebooted. I didn't see anything bad in dmesg and the sound card's been behaving all day so far. I'll keep an eye on it.

If there's anything you can think of for me to do or check then let me know.

---

### Post by defaria on 2010-08-10
OK, eventually it crapped out again, but I get a good 10-20 hours before it breaks. I tried commenting out the final line thus having a fully commented out /etc/modprobe.d/alsa-base.conf file and rebooted. Things were bad. dmesg had errors. Sound basically didn't work.

So then I tried restoring the original alsa-base.conf and commenting out only the last line that I added. Rebooted. Still bad. Comes up in pavcontrol with an Output Device of only Dummy Output.

So it's back to having an alsa-conf with only the last line uncommented as at least that works for about 10-20 hours.

EDIT: Now it's crapping out left and right. HELP! This is a real pain.

EDIT2: I'm just noticing that pulseaudio keeps respawning. Looking in /var/log/syslog I'm seeing:

```
Aug 10 08:40:32 earth pulseaudio[6698]: pid.c: Stale PID file, overwriting.
Aug 10 08:40:33 earth kernel: [  631.480085] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
Aug 10 08:40:34 earth kernel: [  632.620158] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c: snd_pcm_delay() returned a value that is exceptionally large: 86769664 bytes (491891 ms).
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c: snd_pcm_dump():
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c: Soft volume PCM
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c: Control: PCM Playback Volume
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c: min_dB: -51
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c: max_dB: 0
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c: resolution: 256
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c: Its setup is:
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   stream       : CAPTURE
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   access       : MMAP_INTERLEAVED
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   format       : S16_LE
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   subformat    : STD
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   channels     : 2
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   rate         : 44100
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   exact rate   : 44100 (44100/1)
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   msbits       : 16
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   buffer_size  : 16384
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   period_size  : 8192
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   period_time  : 185759
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   tstamp_mode  : ENABLE
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   period_step  : 1
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   avail_min    : 15502
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   period_event : 0
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   start_threshold  : -1
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   stop_threshold   : 4611686018427387904
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   silence_threshold: 0
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   silence_size : 0
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   boundary     : 4611686018427387904
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c: Slave: Hardware PCM card 1 'HDA ATI SB' device 0 subdevice 0
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c: Its setup is:
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   stream       : CAPTURE
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   access       : MMAP_INTERLEAVED
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   format       : S16_LE
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   subformat    : STD
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   channels     : 2
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   rate         : 44100
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   exact rate   : 44100 (44100/1)
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   msbits       : 16
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   buffer_size  : 16384
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   period_size  : 8192
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   period_time  : 185759
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   tstamp_mode  : ENABLE
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   period_step  : 1
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   avail_min    : 15502
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   period_event : 0
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   start_threshold  : -1
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   stop_threshold   : 4611686018427387904
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   silence_threshold: 0
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   silence_size : 0
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   boundary     : 4611686018427387904
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   appl_ptr     : 180224
Aug 10 08:40:36 earth pulseaudio[6698]: alsa-util.c:   hw_ptr       : 22528000
Aug 10 08:40:37 earth rtkit-daemon[1786]: Sucessfully made thread 6717 of process 6717 (n/a) owned by '1000' high priority at nice level -11.
Aug 10 08:40:37 earth rtkit-daemon[1786]: Supervising 1 threads of 1 processes of 1 users.

```

aplay -l does list my sound card:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Took another snapshot of my alsa stuff @ [http://www.alsa-project.org/db/?f=40a05e629ce4aa3b4576d889fe781a68c341ac80](http://www.alsa-project.org/db/?f=40a05e629ce4aa3b4576d889fe781a68c341ac80)

---

### Post by lidex on 2010-08-11
Looks like it may be defaulting to your usb device. But there are plenty of errors to go around. Restore your alsa-base.conf to default, then add this line and reboot:
```
options snd-hda-intel probe_mask=1
```
And you certainly don't want the dv5 model!!

---

### Post by defaria on 2010-08-11
I changed that and once again I'm back up. Will see how this works and if it stops working again.

Re: model=dv5: <Slaps forehead> I was having problems with both my desktop and my laptop (Both 10.04, both updated kernel recently and I try to keep them pretty much in sync) and I guess I was just thinking "laptop" while configuring my desktop. My laptop is a dv7 but as you probably know there is no model=dv7, just a dv5.

I will report back if this breaks at all but assuming it doesn't, once again Lidex you da man! How do these coffee beans work anyway?

EDIT: UGH! It broke again! Sound stops and then I notice in pavcontrol that there are a bunch of backed up sounds form Pidgin (that little ding that happens when people sign in) and the like. Still shows my output device properly. Switching over to PulseAudio Manager I see I'm connected. There's a bunch of queue up sounds in Devices and Clients and the like. I think one time I was able to ungum things by killing them here. Why is this happening? What sort of data can I provide for you to help solve this problem?!?

---

### Post by lidex on 2010-08-11
> **defaria said:**
> I changed that and once again I'm back up. Will see how this works and if it stops working again.

Re: model=dv5: <Slaps forehead> I was having problems with both my desktop and my laptop (Both 10.04, both updated kernel recently and I try to keep them pretty much in sync) and I guess I was just thinking "laptop" while configuring my desktop. My laptop is a dv7 but as you probably know there is no model=dv7, just a dv5.

I will report back if this breaks at all but assuming it doesn't, once again Lidex you da man! How do these coffee beans work anyway?

EDIT: UGH! It broke again! Sound stops and then I notice in pavcontrol that there are a bunch of backed up sounds form Pidgin (that little ding that happens when people sign in) and the like. Still shows my output device properly. Switching over to PulseAudio Manager I see I'm connected. There's a bunch of queue up sounds in Devices and Clients and the like. I think one time I was able to ungum things by killing them here. Why is this happening? What sort of data can I provide for you to help solve this problem?!?

Not sure, but it may be you're trying to use multiple devices at the same time and there is an issue with one grabbing control of alsa.

---

### Post by defaria on 2010-08-11
Well the hardware hasn't changed for a while (cept a new keyboard). I have the soundcard (which is a 5.1 job BTW) and this Microsoft Webcam thing. I don't really use the cam but I use it's mic for Skype? Why would ALSA get confused and try to send sound down to a Webcam???

I have seen odd things like for example right now. I'm running Chrome and I can go to hulu.com and watch videos. I get sound. I also have a VM of XP running and I can hear sound from there. I have sounds associated with opening of menus and they don't play. If I look at pavucontrol I see Dummy Output on the Output Devices but the Hulu videos are still playing OK.

Skype won't work - no sound. PulseAudio Manager says it's connected but the Default Sink is auto_null and the Default Source is alsa_input.usb-Microsoft__LifeCam_Cinema_TM_-02-CinemaTM.analog-mono (how's that for a name?). I can run Banshee but there's no sound. Odd...


Nothing else to try/report?

---

### Post by lidex on 2010-08-11
Post this output please:
```
cat /etc/modprobe.d/alsa-base.conf
```
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

---

### Post by defaria on 2010-08-12
I assume you mean to do this gathering when I'm in the "weird state". I'm in the "weird state", well the sorta weird state. Right now I can play videos through Chrome and hear sound but alerts from Pidgin and Skype and playing movies with VLC have no sound. pavucontrol: Output Devices still says my sound card though.

Here's the results (Note: "Earth:" is my prompt):

```
Earth:cat /etc/modprobe.d/alsa-base.conf 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

# Adding snd-hda-intel: How did this go missing?
options snd-hda-intel probe_mask=1
Earth:sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq* 
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  andrew     2127 F.... pulseaudio
                     andrew    19365 F.... chrome
                     andrew    19572 f.... npviewer.bin
/dev/snd/controlC1:  andrew     2127 F.... pulseaudio
/dev/snd/pcmC0D0p:   andrew    19365 F...m chrome
                     andrew    19572 F...m npviewer.bin
/dev/snd/timer:      andrew    19365 f.... chrome
                     andrew    19572 F.... npviewer.bin
Earth:dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
[   41.946174] USB Video Class driver (v0.1.0)
[   42.037872] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   42.037876] hda_intel: codec_mask forced to 0xff
[   42.042519] Console: switching to colour frame buffer device 80x30
--
[   42.166760] usbcore: registered new interface driver rt73usb
[   45.120009] ALSA hda_intel.c:712: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   46.130011] ALSA hda_intel.c:1420: Codec #1 probe error; disabling it...
[   47.220242] ALSA hda_intel.c:1420: Codec #2 probe error; disabling it...
[   48.310011] ALSA hda_intel.c:1420: Codec #3 probe error; disabling it...
[   48.496954] hda_codec: ALC1200: SKU not ready 0x411111f0
[   48.497038] hda_codec: ALC1200: BIOS auto-probing.
[   48.499599] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input7
[   49.830112] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[   49.861548] usbcore: registered new interface driver snd-usb-audio
--
[ 1080.635153] NFSD: starting 90-second grace period
[ 1088.580148] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[ 1089.600005] vmnet1: no IPv6 routers present
[ 1089.700040] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[ 1090.040007] vmnet8: no IPv6 routers present
[ 1091.903656] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 1109.960082] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[ 1111.081335] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[ 1137.785552] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
--
[ 1409.076134] sd 9:0:0:0: [sdf] Attached SCSI removable disk
[ 1428.383907] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[ 1534.473885] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[ 1574.762604] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[ 1579.169274] /dev/vmmon[3625]: PTSC: initialized at 2293510000 Hz using TSC
--
[ 7226.277138] sd 11:0:0:0: [sdf] Attached SCSI removable disk
[40702.773814] ALSA pcm.c:194: 2:3:1: cannot get freq at ep 0x82
[41092.498803] usb 1-4: USB disconnect, address 6
Earth:
```

---

### Post by defaria on 2010-08-17
Bump. Lidex, perhaps you're busy but I'd really like to get this sound thing resolved. It's such a pain. I've tried removing Pulseaudio and things generally work better but one thing that definitely breaks is my mic doesn't work. I like using Skype for a morning conference call I must attend each working day as well as when I call family and I've been without it for quite some time. What am I doing wrong? Why is this breaking after working for a little bit. As you may know I did nothing that I know of to cause this. A kernel update come along and after updating to that I've been broken ever since. Surely others are having similar problems. 

If there's a better thread I should be reading or join in on let me know. If there's anything I can be doing to help also let me know. I'd like to solve this problem for myself but for anybody else in a similar situation.

And thanks for all the hard work you've been doing so far. You often come up with the right solution which is why I'm here and have such hope that you will once again solve my problem.

---

### Post by astriemer on 2010-08-17
[I'll move this to a thread of my own to keep this thread cleaner for defaria and lidex...didn't mean to hijack...sorry]

I also have had some sound problems since upgrading to 10.04 this weekend, 
sound was working fine in 9.10, and if anyone can shed some light on what is going on I'd appreciate it. I'm fairly computer literate, but am new to linux.

After the upgrade I initially had no sound and so using some of the troubleshooting guides I was able to determine that I had some muted channels and after unmuting everything I now have some sound. However, I'm not sure that really was the best solution as the channel that seems to have sound on it was my microphone channel. Furthermore the sound actually sounds a bit like it is coming from a microphone (it is coming through the speakers) but it is tinny and a little staticy.

What is really strange however is that other than the startup sound I don't have any sound unless I have the Sound Preferences dialog box open. Sound seems to work for any of the programs that I've tried as long as the Sound Preferences is open or minimized, but otherwise no sound.

Here is some other information that may be helpful.

aplay:

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI_1 [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. Device 8288
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fe4f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
    Subsystem: VISIONTEK Device aa08
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fe5ec000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
    Subsystem: VISIONTEK Device aa08
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fe6ec000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel


cat /etc/modprobe.d/alsa-base.conf
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2


Thanks in advance for any help!

---

### Post by lidex on 2010-08-17
*defaria*
OK. Let's try this. If you have probe mask in alsa-base.conf add these two lines before it so it looks like this:
```

[COLOR="Red"]options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel[/COLOR]
options snd-hda-intel probe_mask=1
```

---

### Post by defaria on 2010-08-17
Also rebooted (is there a way to apply these things without having to reboot each time?).

Not must better. Observations: 

. Pulse Audio Manager says the default sink is auto_null
. pavucontrol has only dummy output under output devices
. Video in Chrome (youtube/hulu/etc) play and have sound
. Sounds associated with events (for example I have little menu popup sound) and Pidgin alerts make sound
. Hulu Desktop works
. Skype starts up but no startup sound. Using Skype options Sound Devices the Make a test sound does not sound. The mic doesn't work either. Of course Skype is set to go through Pulse Audio which seems to be grounded to Dummy Output. No other selections but Pulse Audio are available in Skype.
. No speaker icon appears in top bar.
. Interesting, in Sound Preferences I had things set to use ALSA as part of the many things I've been trying. Change it to Auto Detect causes things like Banshee to stop emitting sound. I think Auto Detect is choosing Auto Null as the output.
. Trying Sound Records. Works! 

So far all things work 'cept it says Dummy output in pavucontrol and Skype doesn't work.

EDIT: Another question. According to aplay -l my sound cards is an ALC1200. Yet on pages like [http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt) there is no entry for ALC1200. Why not?

EDIT2: Kernel update. Sound works seemingly better with Dummy Output not appearing for a while. Ah but now it's back. The real change however is that my webcam, thus my mic, is now no longer present thus Skype is unusable still

---

### Post by defaria on 2010-08-25
Bump!

OK How do I get this webcam mic working again? UGH! This is so annoying that my sound doesn't work (or half works)!!!

---

### Post by lidex on 2010-08-25
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by defaria on 2010-08-25
Hmmm... When I do I get a dialog box that asks:

```
What particular problem do you observe?

o Playback does not work, or is crckling
o Surround playback problem (but stereo playback works)
o Recording does not work properly
o Sound problem with one or a few applications only
```

The last one seems the closest description of my problem so I select that. When I do I get two lines output on the terminal I ran this one:

```
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
```

I select OK and I get:

```
Please use the "report bug" feature, available in the menu of the application.
or use "ubuntu-bug <packagename>" to report a bug 
against the particular package.
```

Well on application that doesn't work well is Banshee but it doesn't have any "report bug" feature. Another application that doesn't work well is Pulse Audio Manager but it doesn't even have a menu!

I don't think I managed to actually report any bug.

Note I did try the AlsaUpgrade again just to see if that would fix it - it didn't but it did get my USB webcam working again. Finally Skype seems to be working right now but this setup is very frail and it breaks at the drop of a hat.

---

### Post by lidex on 2010-08-26
I think part of the problem is we don't know what your problem is - at least I don't. Can you explain concisely in one sentence what it is exactly? ;)

---

### Post by lost_seoul on 2010-08-26
luser@luser-desktop:~$ asoundconf list
asoundconf: command not found
luser@luser-desktop:~$ asoundconf set-default-card <parameter>
bash: syntax error near unexpected token `newline'
luser@luser-desktop:~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2010-08-26 01:56:10--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 212.20.107.51
Connecting to [www.alsa-project.org|212.20.107.51|:80](www.alsa-project.org|212.20.107.51|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2010-08-26 01:56:10--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,026       101K/s   in 0.3s    

2010-08-26 01:56:12 (101 KB/s) - `alsa-info.sh' saved [27026]

ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=7974e8777dc9eb3552b78e2b82c655baed2ba094](http://www.alsa-project.org/db/?f=7974e8777dc9eb3552b78e2b82c655baed2ba094)

Please inform the person helping you.





what do i do with this? it is my first time using ubuntu. i recently found out about it through a friend that i am not in contact with anymore. completely lost so any reference on what the terminal is and how to use it would be appreciated beyond words. i am not a program writer or nothing like that so should i just leave ubuntu alone?????????????????????????????????????????????????????????????????????????????????????????????????? very frustrated

---

### Post by lost_seoul on 2010-08-26
RS480m
realtek alc655 ac'97
i also have a soundblaster audigy se soundcard not insalled because that wasnt working either. i've deleted and installed ubuntu like 5 times. niether works so i'm stuck and begging for help. THANKS

---

### Post by lidex on 2010-08-26
> **lost_seoul said:**
> RS480m
realtek alc655 ac'97
i also have a soundblaster audigy se soundcard not insalled because that wasnt working either. i've deleted and installed ubuntu like 5 times. niether works so i'm stuck and begging for help. THANKS
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-atiixp ac97_codec=0 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by defaria on 2010-08-26
> **lidex said:**
> I think part of the problem is we don't know what your problem is - at least I don't. Can you explain concisely in one sentence what it is exactly? ;)

At various times, different parts of the sound system stop working.

That's about as concise as I can get. There's not particular pattern though some things seems to fail more often than others. For example, playing movies with vlc or using skype tend to fail quicker. Interestingly audio playing through a browser (i.e. Chrome) seems to consistently work as will perhaps Hulu Desktop or Boxee but not Banshee.

For example, just this morning I tried Skype, which surprisingly was working last night after re-running the AlsaUpgrade script and rebooting. I was hopeful I'd be able to use it for a conference call I have this morning. Not working anymore! Cannot produce a sound so I cannot hear any call I might make.

So I ran pavucontrol which came up with the output tab selected. My sound card was listed there with all 6 volume sliders (my card does 5.1). Great. So click on Playback just to see if Skype is listed as connected and instead I get a dialog box that says "Disconnected" or some such error with only an OK button which when selected stops the running of pavucontrol. I try again, same behavior and the same error. I try once more but this time I first click on Input Devices tab and it lists my webcam and doesn't blow up. Look at the Configuration tab and it only lists my webcam. Strange. Click on Playback and I see only System Sounds. Back to Output Devices and now it says "Dummy Output" with only 2 volume controls. Now my sound card seems to have disappeared and it will not return until I at least reboot.

Skype still doesn't work, Banshee now hangs when started (goes dim) but sound under say a Hulu video either through the browser or Hulu desktop still works.

I don't make this stuff up and I wish it was simply an always repeatable thing. I can only describe to you what I see because it makes no sense to me still. It seems pretty consistent however that eventually my sound card in the Output Devices tab of pavucontrol goes away and often pulseaudio get's disconnected. Sound seems to work on say the menus of the window manager and the browers, Hulu desktop, Boxee, etc. but Banshee, vlc, Skype work only sometimes for a brief few hours at best then break never to be fixed until a reboot (and sometimes they don't work just after a reboot).

How about we focus on this: What causes the Output Devices tab to no longer list your sound card and switch to "Dummy Output". And how, when it's switched to "Dummy Output" can I get it back to recognizing my sound card short of rebooting?

---

### Post by lidex on 2010-08-27
*defaria*,
Seems like an issue with pulse audio. Follow the pulse link in my sig to make sure it's correctly configured.

---

### Post by lost_seoul on 2010-08-27
lidex

ok so i'm not sure what happened exactly but the soundblaster card was not installed in my pc. so i followed the instructions you gave me and nothing happened.:evil:  so i installed the soundblaster card then booted and clicked on the volume icon and selected the hardware tab and selected the soundblaster card which i never noticed before and magically there is sound. Thanks. still kinda lost though

---

### Post by defaria on 2010-08-27
Well that page doesn't specifically say anything about Lucid but I tried to follow it anyway.

When trying to do #4, one problem that constantly raises it's head, and that I wish would have a solution that works is after selecting System: Preferences: Sound I get a dialog that says:

```
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some
preferences may not take effect. This could indicate a 
problem with Bonobo, or non-GNOME (e.g. KDE) settings
manager may already be active and conflicting with the
GNOME settings manager.
```

And yet gnome-settings-daemon is indeed running! This problem clears itself up on reboot but then breaks again.

I try to do #5 but in my current state when I start pavucontrol I get "Connection failed: Connection refused". Ah it says if I get that error to launch pulseaudio. I did. It says to go to the Output Devices and select your device. Well damn. The only "device" I have at this moment is "Dummy Output"!!! This is why I was asking to fix this problem first.

Well that's it I guess. It says "If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effect!". Doesn't mention 10.04... I'll log out and back in but I'm not hopeful...

EDIT: Well logged out and back in and as I expected it pretty much hasn't changed anything. Output device is still dummy output. Well I thought that a log out and back in was not strong enough so I rebooted. OK so not we've flipped the script - now Banshee, VLC and Skype work but Hulu Desktop, Boxee and Youtube/Hulu videos in browsers don't work anymore!

Hmmm... Putting my .asoundrc file back (which basically seems to set the default for pcm and ctl to pulse) I got the browsers and skype working!!! So everything is working but I still feel it's fragile and may break. I will continue to monitor the situation and report back if it changes. Fingers crossed (and that makes it hard to type!)

EDIT: Settings seem to be holding! Yay!

---

### Post by lost_seoul on 2010-09-02
i call upon the power of the lidex! seriously though my soundblaster card is not being detected so i removed it and now i am back to square one with no sound. 

when i do the following should i paste over the last line or just put the text at the bottom?:

Insert this line at the bottom:
 	Code:

 	 options snd-atiixp ac97_codec=0

---

### Post by lost_seoul on 2010-09-02
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

---

### Post by lidex on 2010-09-02
> **lost_seoul said:**
> i call upon the power of the lidex! seriously though my soundblaster card is not being detected so i removed it and now i am back to square one with no sound. 

when i do the following should i paste over the last line or just put the text at the bottom?:

Insert this line at the bottom:
 	Code:

 	 options snd-atiixp ac97_codec=0

Don't paste over, just add.

---

### Post by defaria on 2010-09-08
OK so it's been working for a few days and I was relatively happy, but suddenly, after my power supply died and I rebooted, noticed Skype not paying attention to DTFM tones and thus I could not use Skype for my daily conference call. Traced this down to the fact that my Webcam with its mic are no longer recognized nor present in pavucontrol. I know that the device is plugged in and works because I can go into Skype and see that the webcam portion shows my ugly mug, but there is no device listed in pavucontrol's Input Devices. It was there! I did not change anything except have to reboot when my power supply died and I replaced it.

What can I do to get it working again?

EDIT: Any ideas how to get my mic working again? Any info I can provide, things to try, debugging techniques?

---

### Post by defaria on 2010-09-14
Help! Still my mic is not working but the webcam is. Note the mic is part of the webcam and also it was working. Additionally the webcam is working and shows video. But pavucontrol does not show the webcam as an input device to seledct. This webcam is a Microsoft Lifecam Cinema. An lsusb shows:

```

$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 15a9:0004  
Bus 002 Device 002: ID 18e3:9102 Fitipower Integrated Technology Inc Multi car reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 045e:075d Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

What can I do to fix this? I did try to research this a bit but all articles I found talked about things like toggling on usage of the device in the Sound Preferences or turning up the volume - IOW all assuming the device showing as present to start with. But the device is not show as present and therefore not selectable in either pavucontrol nor the sound preferences you get by clicking on the speaker and select Sound Preferences (what's the executable for that and why do we have two different sound preferences? This one and gnome-sount-properties).

---

### Post by lidex on 2010-09-15
> **defaria said:**
> Help! Still my mic is not working but the webcam is. Note the mic is part of the webcam and also it was working. Additionally the webcam is working and shows video. But pavucontrol does not show the webcam as an input device to seledct. This webcam is a Microsoft Lifecam Cinema. An lsusb shows:

```

$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 15a9:0004  
Bus 002 Device 002: ID 18e3:9102 Fitipower Integrated Technology Inc Multi car reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 045e:075d Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

What can I do to fix this? I did try to research this a bit but all articles I found talked about things like toggling on usage of the device in the Sound Preferences or turning up the volume - IOW all assuming the device showing as present to start with. But the device is not show as present and therefore not selectable in either pavucontrol nor the sound preferences you get by clicking on the speaker and select Sound Preferences (what's the executable for that and why do we have two different sound preferences? This one and gnome-sount-properties).
Wow, something fishy with your system. Seems like one thing after another. Can you run the alsa-info script? Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

Also provide this output. ```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by defaria on 2010-09-16
Never asked for my username/password.

Your ALSA information is located at [http://www.alsa-project.org/db/?f=a53eaae7e97f78409cb99f2bed1c0f14347f019e](http://www.alsa-project.org/db/?f=a53eaae7e97f78409cb99f2bed1c0f14347f019e)

Here's the output from those two command (note I've long since configured sudo to not prompt me for a password. Also "Earth:" is my prompt):

```
Earth:sudo dmidecode -t bios
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Phoenix Technologies, LTD
	Version: 5.09
	Release Date: 12/23/2008
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/360 KB floppy services are supported (int 13h)
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
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 5.9

Earth:sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: MSI
	Product Name: Aspen
	Version: 1.0
	Serial Number: OEM

Earth:

```

---

### Post by lidex on 2010-09-17
*defaria:*
**Please** remove the options you added to alsa-base.conf and rename ```
~/.asoundrc
```
Now this:
```
sudo apt-get update
sudo apt-get upgrade
```
**Reboot**
Now follow the link in my sig to upgrade your alsa install - make sure to uninstall alsa-backports first, if installed.

---

### Post by defaria on 2010-09-18
I don't remember what I added to alsa-base.conf. There's been so many changes and attempts to fix things. Here's what I have:

```


# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

#options snd slots=snd-hda-intel
#alias snd-card-0 snd-hda-intel
#options snd-hda-intel probe_mask=1

```

I moved ~/.asoundrc aside and updated and upgraded as you said. Then I went though the AlsaUpgrade script for steps -d, -c and -i. The -c step failed again. As I told you before I had to add ARCH=x86 to all of the makes in the script and then it worked. Any chance that could be fixed.

Rebooted and alas I have Dummy Output again! I tried moving ~/.asoundrc back into place - rebooted. Nothing. Then I tried uncommenting those last 3 lines one at a time with reboots inbetween. No better. 

I can see my Lifecam Mic however but I've lost my sound!

So I went from a largely functioning audio system but with a missing Lifecam Mic to a Lifecam Mic that's present but only a Dummy Audio device and no sound! :cry:

I'm gonna try the AlsaUpgrade again, leave alsa-base.conf alone and ~/.asoundrc in place and see if I can get back to my prior state.

Could it be a timing thing? I thought I read somewhere where somebody was saying something about using probe_mask and depending on how the system booked the audio card would get renumbered to say device 1 or device 2 and the probe_mask would not work.

Also, why

```

options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel probe_mask=1

```

as opposed to 

```

options snd slots=snd-hda-intel
options snd-hda-intel probe_mask=1
alias snd-card-0 snd-hda-intel

```

or 

```
                                     
alias snd-card-0 snd-hda-intel
options snd slots=snd-hda-intel
options snd-hda-intel probe_mask=1

```

IOW is ordering important?

---

### Post by defaria on 2010-09-18
After rebooting I'm no better off. Pulseaudio cannot maintain a connection. Starting the PulseAudio Manager shows connected but then dies (See screen captures). Connecting again shows connected for a second or two and then dies again. 

Sound Preferences (BTW why are there two? On when clicking on the speaker icon and selecting Sound Preferences and another, totally different one under System: Preferences: Sound) shows my Internal Audio card an the LifeCam but about every 5 seconds a dialog pops up stating "Waiting for sound system to respond" along with a popping sound. (See screen captures)

Finally there's output in dmesg (attached).

---

### Post by defaria on 2010-09-18
And dmesg.log

EDIT: Had to reboot again and now all things appear to be working. I'm getting the feeling it's something to do with the order in which the kernel sets up the devices...

Keeping my fingers crossed...

---

### Post by lkjoel on 2010-09-25
> **stuque said:**
> My sound in Lucid was working fine (for months), and then, for no obvious reason, it stopped working today. I get no sound from any application. I have no idea what could have changed on my system to cause this.

When I re-boot Lucid, the login sound plays, and sound works briefly, but it always stops eventually after I login.

I am overwhelmed by the large number of different Ubuntu sound problem fixes, and none seem to help.

Any advice about what to do?
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by lidex on 2010-09-26
Have a look here:
[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

### Post by defaria on 2010-09-27
Not sure how much time I can dedicate to trying things here. I'm about to take a cross country move in about a week and right now packing's more important than playing with the computer. I but I appreciate the points and will follow up on things - it just might take a while...

Thanks.

Oh, just wanted to mention, after returning from the East coast and getting an address to live at I powered up the desktop and this time things are working well. I'm convinced this has something to do with the boot order that devices are assigned or something like that.

---

