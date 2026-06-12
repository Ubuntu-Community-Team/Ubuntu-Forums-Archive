---
title: "Mic NOT Working in Ubuntu 9.04"
date: 2009-06-11
forum: Multimedia Software
---

### Post by drkameleon on 2009-06-11
Hi guys!

OK. Here's my case :

- I'm using a Fujitsu-Siemens Amilo Pa 1510 running Ubuntu 9.04 (32-bit)
- Sound is working fine (except for the mic)
- I'm able to hear my own voice through the speakers but not to capture (I've already tried with Sound Recorder, Ekiga, Skype, Audacity)
- Upgraded ALSA, using [http://ubuntuforums.org/showthread.php?t=1046137]("http://ubuntuforums.org/showthread.php?t=1046137")

*Just to mention - my Mic (+ Skype - that's where I wanna use it) was working absolutely fine under Windows XP SP2, Vista and 7 beta. (well YES, Windows s*cks but Linux seems like a real pain in the *ss even for simple stuff)*

**uname -r**
```
2.6.28-11-generic
```
[B]
lspci[/B]
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
05:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
05:04.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
05:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
05:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```
[B]
cat /prov/asound/version[/B]
```
Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on Jun 11 2009 for kernel 2.6.28-11-generic (SMP)
```

**cat /proc/asound/card0/codec#1**
```
Codec: Realtek ALC861
Address: 1
Function Id: 0x1
Vendor Id: 0x10ec0861
Subsystem Id: 0x17340000
Revision Id: 0x100300
No Modem Function Group found
Default PCM:
    rates [0x140]: 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x03 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
Node 0x07 [Audio Output] wcaps 0x605: Stereo Digital Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  Power: setting=D0, actual=D0
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x02, nsteps=0x0d, stepsize=0x0b, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x140]: 48000 96000
    bits [0x2]: 16
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 6
     0x0d* 0x0c 0x0f 0x10 0x11 0x15
Node 0x09 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001f: OUT HP Detect Trigger ImpSense
  Pin Default 0x0121101f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x16
Node 0x0c [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x19
Node 0x0d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000337: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x18
Node 0x0e [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000017: OUT Detect Trigger ImpSense
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x19
Node 0x0f [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000033f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50
  Pin Default 0x99030110: [Fixed] Line Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x1a
Node 0x10 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000033f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50
  Pin Default 0x01a19930: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x1b
Node 0x11 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000063: IN Balanced Trigger ImpSense
  Pin Default 0x9933013e: [Fixed] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x3, Sequence = 0xe
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x12 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01451120: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x07
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x0d 0x10
Node 0x15 [Audio Mixer] wcaps 0x20050f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x0c, nsteps=0x17, stepsize=0x0b, mute=1
  Amp-In vals:  [0x0c 0x0c] [0x0d 0x0d] [0x0b 0x0b]
  Amp-Out caps: ofs=0x0c, nsteps=0x0c, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x0c 0x0c]
  Power: setting=D0, actual=D0
  Connection: 3
     0x11 0x14 0x1c
Node 0x16 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x15
Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x15
Node 0x18 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x05 0x15
Node 0x19 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x06 0x15
Node 0x1a [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x00 0x00] [0x00 0x00]
  Connection: 4
     0x04 0x06 0x15 0x03
Node 0x1b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 4
     0x04 0x06 0x15 0x03
Node 0x1c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x0c 0x0f
Node 0x1d [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1f [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000017: OUT Detect Trigger ImpSense
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x18
Node 0x20 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000017: OUT Detect Trigger ImpSense
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x17
  Processing Coefficient: 0x00
  Coefficient Index: 0x00
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x23 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x0f, nsteps=0x0f, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x8f]

```
[B]
amixer[/B]
```
Simple mixer control 'Master',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 194 [76%] [-12.20dB]
  Front Right: Playback 194 [76%] [-12.20dB]
Simple mixer control 'Front',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Front Mic',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Surround',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Center',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 23
  Mono:
  Front Left: Playback 11 [48%] [-3.00dB] [on]
  Front Right: Playback 11 [48%] [-3.00dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 23
  Mono:
  Front Left: Playback 12 [52%] [0.00dB] [on]
  Front Right: Playback 12 [52%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 23
  Mono:
  Front Left: Playback 13 [57%] [3.00dB] [on]
  Front Right: Playback 13 [57%] [3.00dB] [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 15
  Mono:
  Front Left: Playback 15 [100%] [0.00dB] [off]
  Front Right: Playback 15 [100%] [0.00dB] [off]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 78 [65%] [9.00dB]
  Front Right: Capture 78 [65%] [9.00dB]
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

```

**cat /etc/modprobe.d/alsa-base.conf**
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
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=3stack

```

**Opening *System->Preferences->Sound***
```

Sound Events / Sound Playback = PulseAudio Sound Server
Music & Movies / Sound Playback = PulseAudio Sound Server

Audio Conferencing / Sound playback = PulseAudio Sound Server
Audio Conferencing / Sound capture  = HDA ATI SB ALC861 Analog (ALSA)

Default Mixer Tracks / Device = Playback: HDA ATI SB - ALC861 Analog (PulseAudio)

```

**Opening *Volume Control***
```

HDA ATI SB (Alsa Mixer) is selected.

There are 4 items :

PCM, Line-In, CD, Microphone - all set to Maximum and UNmuted.

There is a tab, saying "Recording" with JuST 1 item "Digital" which - although I UNMUTE it - it always drops back to "MUTED" whenever I close the window.

```

**Using *Volume Control->Preferences*, that's what I see :**
```

Playback
----------
PCM
Line-In
CD
Microphone
Beep          (un-ticked)

Recording
----------
Digital

Switches
----------
Master
Headphone
Front
Front Mic
Surround         (un-ticked)
Center           (un-ticked)
LFE              (un-ticked)
Caller-ID        (un-ticked)
Off-Hook         (un-ticked)

Options
-------------
Channel Mode


```

I've already spent COUNTLESS hours in order to fix this. :evil::evil::evil: 

If you can help FINALLY make it WORK, I'd be grateful. :D

Thanks in advance! ;)

Dr.Kameleon

---

### Post by drkameleon on 2009-06-11
Up ^

---

### Post by gradinaruvasile on 2009-06-11
If u can hear your voice it might be a setting problem in the mixer.
Run "alsamixer" in a terminal.
Change the View to Capture (TAB). You will have some volume Items (the bars with labels) there, i cant tell which, it differs with hardware. You should have something like front mic there which should have the volume up, also Capture (might have more than 1). 
Go with the arrow keys to the first Capture item, check if it has CAPTUR  (red) written under it. If not, it has a dotted line, press space to set it as the capture device. Another thing is the Input source (Input So is seen only), go to it with the arrow keys, press the up/down keys, it should change - select front mic, test if not working, select mic. capture and Digital should have the volume levels up (if you hear noise, you might try lowering Digital).
On the Playback tab, mute front mic, mic,CD, line (go to the specific item, press m, you will see MM appearing .You should do this while running sound recorder (monitor the sound level on the lower right corner). The changes should apply immediately run time, no need to close alsamixer.

If you cannot find a working combination, try setting everything to ALSA and killing the pulseaudio process (killall pulseaudio in terminal). If u want to use ALSA only, make sure you edit the [COLOR="red"]/etc/pulse/client.con[/COLOR]f file and set [COLOR="Red"]autospawn = no[/COLOR].

The ALSA upgrading stuff can be a double edged something... I did it and run into problems - downgrading on the other hand is a  pain in the a** (libasound2 seems to be the corner stone of Ubuntu or something grrr...) I never touch it again if not absolutely required.

---

### Post by drkameleon on 2009-06-11
Hi Gradinaruvasile,

thanks for the reply.

I opened alsamixer through the console but I was unable to see anything of what you suggested.

I then tried to set everything to HDA ATI SB ALC861 Analog (ALSA) + changed autospawn = no and I'm now unable to hear any sound.... :(

Any suggestions?

---

### Post by gradinaruvasile on 2009-06-11
Different indeed. 
I see PCM (this one controls the playback volume i think) has no volume. Raise it by navigating to it with the arrow keys and press up. Unmute front by pressing m while on it. Mute mic (only here in the playback tab, it means you will not hear your own sounds all the time). Mute CD, line. Raise mic volume (for now).
Please show me the capture tab aswell (just press tab) from this screen).

Did you select your devices like this (screenshot)?

---

### Post by drkameleon on 2009-06-11
> **gradinaruvasile said:**
> Different indeed. 
I see PCM (this one controls the playback volume i think) has no volume. Raise it by navigating to it with the arrow keys and press up. Unmute front by pressing m while on it. Mute mic (only here in the playback tab, it means you will not hear your own sounds all the time). Mute CD, line. Raise mic volume (for now).
Please show me the capture tab aswell (just press tab) from this screen).

Did you select your devices like this (screenshot)?

Hi again (I've been offline for a few hours),

I set everything in Sound->Preferences to "ALSA - Advanced Linux Sound Architecture", except for the the Default Mixer Track -> Device which is set to "HDA ATI SB (Alsa Mixer)" and after rebooting, sound is back!

Using alsamixer, through console, I've also set PCM at maximum volume 100/100. However, there is nothing new & the "CAPTURE" tab has nothing but a "Digital" item (UNMUTED). Another strange thing is that there ARE also 2 items ("front" and "front mix") appearing in the "Playback" tab which seem disabled, and I cannot alter their "0/100" volume.

Opening the Volume Control window, in the "Recording tab" - although the only item - "Digital" - is set to Maximum, it is always MUTED, even after I unmute it and close the window (it reverts to its previous status) -- weird stuff... ](*,)

I really appreciate your help... ;)

Do you think there is anything left to be done from here?

Dr.Kameleon

P.S. Btw, I think I once had managed to make a "Capture" option appear somewhere in the Options (in Volume Control) but without getting the Mic to work. Now - probably after the Alsa Upgrade - it's gone... :(

---

### Post by drkameleon on 2009-06-12
Up ^

---

### Post by gradinaruvasile on 2009-06-12
You are using a pre release ALSA version. The default jaunty ALSA version is 1.0.18. I suggest downgrade to the stable version. search in the synaptic for "alsa" click on the "installed version" column header and select every package that has 1.0.20 version and press ctrl-e, select 1.0.18-whateverisbigger. You might hava a problem at the libasound2 package - try leaving that alone.

Another thing - i forgot to tell you to remove the pulseaudio startup link... not that in this case would matter.
sudo mv /etc/X11/Xsession.d/70pulseaudio ~/

Another thing would be to boot the laptop with a live cd and check alsamixer... See what devices you have there.

---

### Post by drkameleon on 2009-06-12
Hi again,

> **gradinaruvasile said:**
> You are using a pre release ALSA version. The default jaunty ALSA version is 1.0.18. I suggest downgrade to the stable version. search in the synaptic for "alsa" click on the "installed version" column header and select every package that has 1.0.20 version and press ctrl-e, select 1.0.18-whateverisbigger. You might hava a problem at the libasound2 package - try leaving that alone.


I've looked for "alsa" in Synaptic but the only alsa* packages installed are of a 1.0.18-XXXX version and there are no "1.0.20" packages...

> **gradinaruvasile said:**
> 
Another thing - i forgot to tell you to remove the pulseaudio startup link... not that in this case would matter.
sudo mv /etc/X11/Xsession.d/70pulseaudio ~/


I did that.

> **gradinaruvasile said:**
> 
Another thing would be to boot the laptop with a live cd and check alsamixer... See what devices you have there.

I might look for some burnt LiveCD and check this out as well - what's the purpose for that? To see the un-touched configuration (i mean BEFORE all these hacks, and alsa-upgrades, etc)?

Thanks again, ;)

Dr.Kameleon

---

### Post by gradinaruvasile on 2009-06-12
> **drkameleon said:**
> 
I might look for some burnt LiveCD and check this out as well - what's the purpose for that? To see the un-touched configuration (i mean BEFORE all these hacks, and alsa-upgrades, etc)?


Dr.Kameleon

Exactly :)

Not even alsa-utils has 1.0.20? that package contains alsamixer.
I have another idea... try reinstalling alsa from ground so to speak. Look here:

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by mihaimm on 2009-06-12
I know I had serious problems in using the mic on Ubuntu, in all versions... however 9.04 was the worst of all.

Regardless... the following works for Skype (at least for me and a number of co-workers):
- in the Skype->Preferences->Sound Devices make sure you don't allow Skype to adjust your mixer levels. For some reason, Skype mutes my microphone if I let it adjust the levels.
- As Sound In try anything but pulse and make sure you test each of the devices listed.
- Repeatedly do multiple tests with the above and various configurations in Alsa Mixer to see if anything changes.

Since I don't actually have a HDA ATI Audio Controller I can't provide more help... but I can tell you that HDA Intel is pretty much a pain also... 
If this does not work I would also suggest to try it from the bootable CD in order to make sure it's not something you messed by previous attempts to make it work.

---

### Post by drkameleon on 2009-06-12
> **gradinaruvasile said:**
> Exactly :)

Not even alsa-utils has 1.0.20? that package contains alsamixer.


Nope, not even this one - it's of a "1.0.18-sth" version.

> **gradinaruvasile said:**
> 
I have another idea... try reinstalling alsa from ground so to speak. Look here:

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")


I've thought about this as well - as in the very beginning I think there was at least some 'CAPTURE' option, and sth other things that I cannot find now. And moreover, having built a PERFECT Developper's station under Ubuntu, I'm really NOT willing to start all this from scratch - because of 1-2 ridiculous problems...

I'm going to revert to the beginning (fresh installing Alsa) and I'll be back...

---

### Post by drkameleon on 2009-06-12
Hi Mihaimm!

> **mihaimm said:**
> 
- in the Skype->Preferences->Sound Devices make sure you don't allow Skype to adjust your mixer levels. For some reason, Skype mutes my microphone if I let it adjust the levels.
- As Sound In try anything but pulse and make sure you test each of the devices listed.
- Repeatedly do multiple tests with the above and various configurations in Alsa Mixer to see if anything changes.


I've tried countless of these variations but nothing yet was successful. My MAIN problem is that I cannot CAPTURE the sound from my Mic. Probably, my nest great problem would be (after I have captured it) to make Skype work - but this is gonna be an extra step... lol


> **mihaimm said:**
> 
If this does not work I would also suggest to try it from the bootable CD in order to make sure it's not something you messed by previous attempts to make it work.

Well, truth is that even from my LiveCD, the Mic was NOT working... I truly do not know...

Anyway, thanks!;)

P.S. Btw, it's quite strange that I've already found countless threads concerning HDA-INTEL-SB, but NOT... mine (HDA-ATI-SB)...

---

### Post by gradinaruvasile on 2009-06-12
I looked over the link you gave in the first post... It isnt at that version because it wasnt installed via dpkg/apt-get... It is not advised to make changes such as these unless you are willing to risk a broken system. I suggest to everyone to use the repositories if possible. From my experience the default drivers worked best (i mean most stable).

And another thing ... i also searched for your card ant it isnt looking that good... It seems other people also had problems with it...
The card is:
ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
This might help:

[http://ubuntuforums.org/showthread.php?p=5148501]("http://ubuntuforums.org/showthread.php?p=5148501")

And this is a link to the newer 1.0.19 drivers - try it if all else fails:

[https://launchpad.net/~pgquiles/+archive/ppa]("https://launchpad.net/~pgquiles/+archive/ppa")

---

### Post by drkameleon on 2009-06-12
I reinstalled Alsa from scratch - sound works, my Sound Card is recognised - EXCEPT for the Mic (again)...
[B]
lspci|grep Audio[/B]
```
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
```

However, some things seem to be changed in a... positive way.:)

Please, have a look at the attached screenshots and tell me what you think about it...

(For some reason, although I UNmute them every single time, the "Digital" and "Capture" options [in the "Recording" tab] get Muted again, just after I close the "Volume Control" Window....):(

P.S. NOW, I'm NOT able to hear my own voice through the speakers... hmm...

---

### Post by gradinaruvasile on 2009-06-12
Ok... This looks better
Try to unmute everything from alsamixer and see if u can hear your voice back in the spaekers. On the capture tab see if u can change the mic (pressing up).

---

### Post by drkameleon on 2009-06-12
> **gradinaruvasile said:**
> Ok... This looks better
Try to unmute everything from alsamixer and see if u can hear your voice back in the spaekers. On the capture tab see if u can change the mic (pressing up).

Well, in the AlsaMixer window... EVERYTHING is UNmuted - (On the "capture" tab, the "Capture" Option is set @ MAX and the 2nd option - input source - is set Mic)

HOWEVER, There is STILL now sound coming from the speakers... :(

---

### Post by gradinaruvasile on 2009-06-12
Tried to switch the mic (on the capture tab at input_so?
In the attached image i see 3 muted items: iec958 caller id offhook. Did u unmuted them?
Also can u hear the test sound from the System->Preferences->Sound?

---

### Post by solitary.angler on 2011-09-18
Hi,
I don't know if this is relevant anymore in 2011, but I just installed Linux Mint 11 (Ubuntu based) on a very similar system and had the same problem. I think I solved it. Works fine. 

I updated the thread here:
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
Do read the thread to understand how to use this information.

Here it is in full copy:
**Fujitsu Siemens AMILO Pa1510 Realtek ALC861**
AMD-Turion64
ATI Radeon Xpress 1100

/etc/modprobe.d/alsa-base.conf :
**options snd-hda-intel model=3stack-660 position_fix=1 enable=yes**

~ $ uname -a
Linux Capucine 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
(Linux Mint 11 Katya)

~ $ lspci -v
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
        Subsystem: Fujitsu Technology Solutions Realtek High Definition Audio
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

~ $ more /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0000000 irq 16

~ $ more /proc/asound/card0/codec#1
Codec: Realtek ALC861

~ $ more /proc/asound/modules 
 0 snd_hda_intel

~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~ $ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

AlsaMixer v1.0.24.2

---------------------------------------

Thank you,

 -Auro

PS: Internal speakers and Headphones were working fine. I had to add  this to get the external mic working. I don't think this laptop has an  internal mic. I don't see one (the laptop belongs to a friend). Now I  can use headphones or the internal speakers with an external mic to use  Skype for example.

---

### Post by Dale61 on 2011-09-21
I replied to a similar post earlier, but here goes again.  An internal microphone is mono, but default settings think it is stereo.  Find where the sliders adjust microphone volume, unlock so each can be controlled separately, slide one to zero; the other to about 50%, then lock the sliders.  You may need to reboot, but this fixed my microphone after weeks of frustration.

---

