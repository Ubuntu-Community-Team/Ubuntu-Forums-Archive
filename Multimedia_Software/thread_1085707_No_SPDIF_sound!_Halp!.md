---
title: "No SPDIF sound! Halp!"
date: 2009-03-03
forum: Multimedia Software
---

### Post by sythem on 2009-03-03
Hey everyone,
   So I have an Inspiron e1505 with svideo adapter that contains a SPDIF output on it. The thing always worked in Windows and my past experience is that anything will work on linux if you just know what to do so I'm here.

In System->Preferences->Sound when I try to test HDA Intel STAC9200 Digital (ALSA) I get no error's and no sound.
When I try to test anything containing OSS I get the error:
```
audiotestsrc wave=sine freq=512 ! audioconvert 
! audioresample ! gconfaudiosink: Could not open audio device for playback. 
Device is being used by another application.
```

Listed in Volume Control:
HDA Intel (Alsa Mixer)
Sigmatel STAC9200 (OSS Mixer)
Playback: Alsa PCM on front (STAC 92xx) via DMA (PulseAudio Mixer)
Capture: ...
Capture: ...

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I've already played with all audio volumes in every option under each device in the volume control including the ones you have to enable in preferences and those contained in capture with no luck.

Well I think that's about as in-depth as I can be about what I know so far. Any leads on how to get this working would be wonderful. Oh yeah, using Ubuntu Intrepid.

---

### Post by fh_scott on 2009-05-09
did you ever get this working?

I have an Inspiron 6400 with the component video + s/pdif dongle.  Works perfectly in Windows.

I get no sound from it in Ubuntu.

-scott

---

### Post by geopteryx on 2009-07-19
I have the same problem on my Dell E1705/9400. After having tried for several years (!) I could never bring my S/PDIF output to work! I'm very disappointed indeed! Like you both, I use a "S-Video adapter that contains a SPDIF output on it". Everything works fine on XP/Vista.

Here my actual config: 
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
Codec: STAC9200

Kernel release:    2.6.28-13-generic
Operating System:  Ubuntu 9.04
Architecture:      i686

Alsa:
Driver version:     1.0.20
Library version:    1.0.20
Utilities version:  1.0.20

It did not work for me but you may try to add these lines at the bottom of your /etc/modprobe.d/alsa-base.conf file:
```

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m25
```

And reboot.
It's for the Inspiron E1505n/6400.
Mine *should* work with model=dell-m27 but never worked...](*,)

---

### Post by marczyn on 2010-01-08
Hi,
I have Dell D620 (Sigmatel STAC9200) connected through Docking station and exactly the same problem - no signal via spdif. 
I tried almost everything I was able to find via Google on Ubuntu 9.10 and Fedora 12: .asoundrc, alsamixer, updated ALSA to the latest 1.0.22.1, etc. etc.
Nothing works by now... 
I'm getting analog audio (internal speakers) without problems but not digital via spdif!


Under Windows XP SP3 everything is working just fine. AC3/DTS bitstream is being forwarded to the external decoder.

My config:

aplay -l

karta 0: Intel [HDA Intel], urz&#261;dzenie 0: STAC92xx Analog [STAC92xx Analog]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 0: Intel [HDA Intel], urz&#261;dzenie 1: STAC92xx Digital [STAC92xx Digital]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0



aplay -L

null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, STAC92xx Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output


AlsaMixer everything unmuted.


The problem seems to be more related to ALSA and intel-hda then to this particular laptop model or D-port. 


Alsa-info script results:
[http://pastebin.ca/1743209](http://pastebin.ca/1743209)

!!################################
!!ALSA Information Script v 0.4.48
!!################################

!!Script ran on: Fri Jan  8 22:24:48 CET 2010


!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"


!!Kernel Information
!!------------------

Kernel release:    2.6.31-14-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.22.1
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefffc000 irq 28


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 01)
    Subsystem: 1028:01c2


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


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1
beep_mode : 1,1,1,1,1,1,1,1
enable : Y,Y,Y,Y,Y,Y,Y,Y
enable_msi : -1
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<  NULL>
index : -1,-1,-1,-1,-1,-1,-1,-1
model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<  NULL>
patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<  NULL>
position_fix : 0,0,0,0,0,0,0,0
power_save : 10
power_save_controller : N
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
probe_only : N,N,N,N,N,N,N,N
single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: SigmaTel STAC9200
Address: 0
Function Id: 0x1
Vendor Id: 0x83847690
Subsystem Id: 0x102801c2
Revision Id: 0x102201
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
GPIO: io=4, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0xd0401: Stereo
  Device: name="STAC92xx Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x03 [Audio Input] wcaps 0x1d0541: Stereo
  Device: name="STAC92xx Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x0a
  Processing caps: benign=0, ncoeff=0
Node 0x04 [Audio Input] wcaps 0x140311: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
  Connection: 1
     0x08
Node 0x05 [Audio Output] wcaps 0x40211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="STAC92xx Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x1e0]: 44100 48000 88200 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x06 [Vendor Defined Widget] wcaps 0xf30201: Stereo Digital
  Delay: 3 samples
Node 0x07 [Audio Selector] wcaps 0x300901: Stereo R/L
  Connection: 3
     0x02* 0x08 0x0a
Node 0x08 [Pin Complex] wcaps 0x430681: Stereo Digital
  Pincap 0x00010024: IN EAPD Detect
  EAPD 0x0:
  Pin Default 0x40c003fa: [N/A] SPDIF In at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xa
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 3 samples
Node 0x09 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x0144131f: [Jack] SPDIF Out at Ext Rear
    Conn = RCA, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 2
     0x05* 0x0a
Node 0x0a [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x0c
Node 0x0b [Audio Selector] wcaps 0x300105: Stereo Amp-Out
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Master Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x13 0x13]
  Connection: 1
     0x07
Node 0x0c [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Mux Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 5
     0x10 0x0f* 0x0e 0x0d 0x12
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0000003f: IN OUT HP Detect Trigger ImpSense
  Pin Default 0x0321121f: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x0b
Node 0x0e [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0000003f: IN OUT HP Detect Trigger ImpSense
  Pin Default 0x90170310: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0b
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
  Pin Default 0x90a70321: [Fixed] Mic at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0b
Node 0x10 [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00001737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x03a11020: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Connection: 1
     0x0b
Node 0x11 [Pin Complex] wcaps 0x400104: Mono Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00]
  Pincap 0x00000010: OUT
  Pin Default 0x401003fb: [N/A] Speaker at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xb
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 1
     0x13
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x40f000fc: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xc
  Pin-ctls: 0x00:
Node 0x13 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x07
Node 0x14 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
Codec: Conexant ID 2bfa
Address: 1
Function Id: 0x2
Vendor Id: 0x14f12bfa
Subsystem Id: 0x14f100c3
Revision Id: 0x90000
Modem Function Group: 0x2
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 2010-01-08 22:13 /dev/snd/controlC0
crw-rw----  1 root audio 116,  4 2010-01-08 22:13 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  5 2010-01-08 22:13 /dev/snd/hwC0D1
crw-rw----  1 root audio 116, 24 2010-01-08 22:14 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 2010-01-08 22:14 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 17 2010-01-08 22:14 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  1 2010-01-08 22:13 /dev/snd/seq
crw-rw----  1 root audio 116, 33 2010-01-08 22:13 /dev/snd/timer

/dev/snd/by-path:
razem 0
drwxr-xr-x 2 root root  60 2010-01-08 22:13 .
drwxr-xr-x 3 root root 220 2010-01-08 22:13 ..
lrwxrwxrwx 1 root root  12 2010-01-08 22:13 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** Lista PLAYBACK urz&#261;dze&#324; ****
karta 0: Intel [HDA Intel], urz&#261;dzenie 0: STAC92xx Analog [STAC92xx Analog]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 0: Intel [HDA Intel], urz&#261;dzenie 1: STAC92xx Digital [STAC92xx Digital]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0

ARECORD

**** Lista CAPTURE urz&#261;dze&#324; ****
karta 0: Intel [HDA Intel], urz&#261;dzenie 0: STAC92xx Analog [STAC92xx Analog]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 19 [61%] [-18.00dB] [on]
  Front Right: Playback 19 [61%] [-18.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 251 [98%] [0.80dB]
  Front Right: Playback 251 [98%] [0.80dB]
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
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Mic'
Simple mixer control 'Mux',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 19
        value.1 19
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Master Playback Switch'
        value.0 true
        value.1 true
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 15'
        comment.dbmin 0
        comment.dbmax 2250
        iface MIXER
        name 'Capture Volume'
        value.0 0
        value.1 0
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 false
        value.1 false
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 4'
        comment.dbmin 0
        comment.dbmax 4000
        iface MIXER
        name 'Mux Capture Volume'
        value.0 0
        value.1 0
    }
    control.6 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 'Front Mic'
        iface MIXER
        name 'Input Source'
        value Mic
    }
    control.7 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
value '0fff000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 000'
    }
    control.8 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
value '0f00000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 000'
    }
    control.9 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
value '0400000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 000'
    }
    control.10 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value true
    }
    control.12 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.tlv '0000000100000008ffffec1400000014'
        comment.dbmin -5100
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 251
        value.1 251
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
isofs
udf
crc_itu_t
binfmt_misc
ppdev
snd_hda_codec_idt
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
pcmcia
snd_seq_midi_event
snd_seq
yenta_socket
iptable_filter
snd_timer
rsrc_nonstatic
ip_tables
snd_seq_device
arc4
pcmcia_core
x_tables
snd
ecb
joydev
nvidia
psmouse
serio_raw
dell_wmi
b43
mac80211
soundcore
snd_page_alloc
dell_laptop
dcdbas
cfg80211
led_class
lp
parport
usb_storage
tg3
video
output
ssb
intel_agp
agpgart



Any help appreciated!

---

