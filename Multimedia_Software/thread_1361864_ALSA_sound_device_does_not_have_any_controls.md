---
title: "ALSA sound device does not have any controls"
date: 2009-12-22
forum: Multimedia Software
---

### Post by domarm on 2009-12-22
Hello, I've been working on installing ALSA 1.0.22 on Karmic Koala 9.10 on an Asus P6T Deluxe V2 motherboard, and I've run into a problem: when I open alsamixer it just says "**This sound device does not have any controls.**" Card: HDA Intel Chip: Analog Devices AD1989B

I'm pretty sure the drivers/lib/utils are installed correctly and that the headers are updated. I can run alsaconf and it runs without errors and at the end returns "use your favorite mixer to set volume". I followed the instructions here:

[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

Some potentially-helpful information:

**cat /proc/asound/cards**
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf7ff8000 irq 57


**lspci**
00:00.0 Host bridge: Intel Corporation X58 I/O Hub to ESI Port (rev 12)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 12)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 12)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 12)
00:10.0 PIC: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 12)
00:10.1 PIC: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 12)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 12)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 12)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 12)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 12)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
**00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller**
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 3
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
02:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 280] (rev a1)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
05:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
08:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)


**aplay -l**
**** List of PLAYBACK Hardware Devices ****


**ls -lart /dev/snd**
crw-rw----+  1 root audio 116, 33 2009-12-22 11:46 timer
crw-rw----+  1 root audio 116,  1 2009-12-22 11:46 seq
crw-rw----+  1 root audio 116,  4 2009-12-22 11:46 hwC0D0
crw-rw----+  1 root audio 116,  0 2009-12-22 11:46 controlC0
drwxr-xr-x   2 root root       60 2009-12-22 11:46 by-path
drwxr-xr-x   3 root root      140 2009-12-22 11:46 .
drwxr-xr-x  16 root root     3960 2009-12-22 11:46 ..


**cat /dev/sndstat**
Sound Driver:3.8.1a-980706 (ALSA v1.0.22 emulation code)
Kernel: Linux velocemente 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xf7ff8000 irq 57

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Analog Devices AD1989B


**lsmod | grep snd**
snd_hda_codec_analog    81888  0 
snd_hda_intel          32032  0 
snd_hda_codec          96032  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               9448  1 snd_hda_codec
snd_pcm_oss            44320  0 
snd_mixer_oss          19008  1 snd_pcm_oss
snd_pcm                92200  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3588  0 
snd_seq_oss            33664  0 
snd_seq_midi            8320  0 
snd_rawmidi            27200  1 snd_seq_midi
snd_seq_midi_event      8544  2 snd_seq_oss,snd_seq_midi
snd_seq                61216  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25840  2 snd_pcm,snd_seq
snd_seq_device          8532  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77736  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         11088  2 snd_hda_intel,snd_pcm



Thanks in advance for the help!



EDIT:


[LIST=1]
[*][COLOR=brown][FONT=monospace]**################################**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**ALSA Information Script v 0.4.58**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**################################**[/FONT][/COLOR]
[*]
[*][COLOR=brown][FONT=monospace]**Script ran on: Tue Dec 22 18:56:57 UTC 2009**[/FONT][/COLOR]
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
[*]Manufacturer:      System manufacturer
[*]Product Name:      System Product Name
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Kernel Information**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------------**[/FONT][/COLOR]
[*]
[*]Kernel release:    2.6.31-16-generic
[*]Operating System:  GNU/Linux
[*]Architecture:      x86_64
[*]Processor:         unknown
[*]SMP Enabled:       Yes
[*]
[*]
[*][COLOR=brown][FONT=monospace]**ALSA Version**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------**[/FONT][/COLOR]
[*]
[*]Driver version:     1.0.22
[*]Library version:    1.0.22
[*]Utilities version:  1.0.22
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
[*]Pulseaudio:
[*]      Installed - Yes (/usr/bin/pulseaudio)
[*]      Running - Yes
[*]
[*]ESound Daemon:
[*]      Installed - Yes (/usr/bin/esd)
[*]      Running - No
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Soundcards recognised by ALSA**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-----------------------------**[/FONT][/COLOR]
[*]
[*] 0 [Intel          ]: HDA-Intel - HDA Intel
[*]                      HDA Intel at 0xf7ff8000 irq 57
[*]
[*]
[*][COLOR=brown][FONT=monospace]**PCI Soundcards installed in the system**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**--------------------------------------**[/FONT][/COLOR]
[*]
[*]00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Advanced information - PCI Vendor/Device/Susbsystem ID's**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**--------------------------------------------------------**[/FONT][/COLOR]
[*]
[*]00:1b.0 0403: 8086:3a3e
[*]        Subsystem: 1043:82ea
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
[*]snd-pcsp: index=-2
[*]snd-hda-intel: model=ICH10
[*]snd-hda-intel: enable_msi=1
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Loaded sound module options**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**--------------------------**[/FONT][/COLOR]
[*]
[*][COLOR=brown][FONT=monospace]**Module: snd_hda_intel**[/FONT][/COLOR]
[*]        bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1
[*]        beep_mode : 1,1,1,1,1,1,1,1
[*]        enable : Y,Y,Y,Y,Y,Y,Y,Y
[*]        enable_msi : 1
[*]        id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
[*]        index : -1,-1,-1,-1,-1,-1,-1,-1
[*]        model : ICH10,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
[*]        patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
[*]        position_fix : 0,0,0,0,0,0,0,0
[*]        power_save : 10
[*]        power_save_controller : N
[*]        probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
[*]        probe_only : N,N,N,N,N,N,N,N
[*]        single_cmd : N
[*]
[*]
[*][COLOR=brown][FONT=monospace]**HDA-Intel Codec information**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**---------------------------**[/FONT][/COLOR]
[*][(following section hidden - click to display)]("javascript:showColl(1)")
[/LIST]

[LIST]
[*]
[*]Codec: Analog Devices AD1989B
[*]Address: 0
[*]Function Id: 0x1
[*]Vendor Id: 0x11d4989b
[*]Subsystem Id: 0x10438372
[*]Revision Id: 0x100300
[*]No Modem Function Group found
[*]Default PCM:
[*]    rates [0x7ff]: 8000 11025 16000 22050 32000 44100 48000 88200 96000 176400 192000
[*]    bits [0xe]: 16 20 24
[*]    formats [0x1]: PCM
[*]Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]Default Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
[*]GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
[*]  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
[*]  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=1, unsol=0
[*]  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
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
[*]  Power states:  D0 D3
[*]  Power: setting=D0, actual=D0
[*]Node 0x04 [Audio Output] wcaps 0x405: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Converter: stream=0, channel=0
[*]  Power states:  D0 D3
[*]  Power: setting=D0, actual=D0
[*]Node 0x05 [Audio Output] wcaps 0x405: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Converter: stream=0, channel=0
[*]  Power states:  D0 D3
[*]  Power: setting=D0, actual=D0
[*]Node 0x06 [Audio Output] wcaps 0x405: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Converter: stream=0, channel=0
[*]  Power states:  D0 D3
[*]  Power: setting=D0, actual=D0
[*]Node 0x07 [Audio Input] wcaps 0x130391: Stereo Digital
[*]  Converter: stream=0, channel=0
[*]  SDI-Select: 0
[*]  Digital:
[*]  Digital category: 0x0
[*]  PCM:
[*]    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
[*]    bits [0xe]: 16 20 24
[*]    formats [0x5]: PCM AC3
[*]  Unsolicited: tag=00, enabled=0
[*]  Delay: 3 samples
[*]  Connection: 1
[*]     0x1c
[*]Node 0x08 [Audio Input] wcaps 0x100501: Stereo
[*]  Converter: stream=0, channel=0
[*]  SDI-Select: 0
[*]  Power states:  D0 D3
[*]  Power: setting=D0, actual=D0
[*]  Connection: 1
[*]     0x0c
[*]Node 0x09 [Audio Input] wcaps 0x100501: Stereo
[*]  Converter: stream=0, channel=0
[*]  SDI-Select: 0
[*]  Power states:  D0 D3
[*]  Power: setting=D0, actual=D0
[*]  Connection: 1
[*]     0x0d
[*]Node 0x0a [Audio Output] wcaps 0x405: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Converter: stream=0, channel=0
[*]  Power states:  D0 D3
[*]  Power: setting=D0, actual=D0
[*]Node 0x0b [Audio Output] wcaps 0x30211: Stereo Digital
[*]  Converter: stream=0, channel=0
[*]  Digital:
[*]  Digital category: 0x0
[*]  PCM:
[*]    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
[*]    bits [0xe]: 16 20 24
[*]    formats [0x5]: PCM AC3
[*]  Delay: 3 samples
[*]Node 0x0c [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
[*]  Amp-Out vals:  [0xa7 0xa7]
[*]  Connection: 11
[*]     0x38 0x39* 0x3a 0x3b 0x3c 0x18 0x24 0x25 0x3d 0x20 0x1f
[*]Node 0x0d [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
[*]  Amp-Out vals:  [0xa7 0xa7]
[*]  Connection: 10
[*]     0x38 0x39* 0x3a 0x3b 0x3c 0x18 0x24 0x25 0x3d 0x20
[*]Node 0x0e [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
[*]  Amp-Out vals:  [0xa7 0xa7]
[*]  Connection: 10
[*]     0x38 0x39* 0x3a 0x3b 0x3c 0x18 0x24 0x25 0x3d 0x20
[*]Node 0x0f [Audio Input] wcaps 0x100501: Stereo
[*]  Converter: stream=0, channel=0
[*]  SDI-Select: 0
[*]  Power states:  D0 D3
[*]  Power: setting=D0, actual=D0
[*]  Connection: 1
[*]     0x0e
[*]Node 0x10 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
[*]  Amp-Out caps: ofs=0x0f, nsteps=0x0f, stepsize=0x0b, mute=1
[*]  Amp-Out vals:  [0x00]
[*]Node 0x11 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Pincap 0x0000373f: IN OUT HP Detect Trigger ImpSense
[*]    Vref caps: HIZ 50 GRD 80 100
[*]  Pin Default 0x02214030: [Jack] HP Out at Ext Front
[*]    Conn = 1/8, Color = Green
[*]    DefAssociation = 0x3, Sequence = 0x0
[*]  Pin-ctls: 0xc0: OUT HP VREF_HIZ
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 1
[*]     0x22
[*]Node 0x12 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Pincap 0x0000373f: IN OUT HP Detect Trigger ImpSense
[*]    Vref caps: HIZ 50 GRD 80 100
[*]  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
[*]    Conn = 1/8, Color = Green
[*]    DefAssociation = 0x1, Sequence = 0x0
[*]  Pin-ctls: 0x40: OUT VREF_HIZ
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 1
[*]     0x29
[*]Node 0x13 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
[*]  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
[*]  Amp-Out vals:  [0x00]
[*]  Pincap 0x00000010: OUT
[*]  Pin Default 0x511711f0: [N/A] Speaker at Int Rear
[*]    Conn = Analog, Color = Black
[*]    DefAssociation = 0xf, Sequence = 0x0
[*]    Misc = NO_PRESENCE
[*]  Pin-ctls: 0x40: OUT
[*]  Connection: 1
[*]     0x2d
[*]Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x80 0x80]
[*]  Pincap 0x0000373f: IN OUT HP Detect Trigger ImpSense
[*]    Vref caps: HIZ 50 GRD 80 100
[*]  Pin Default 0x02a1902e: [Jack] Mic at Ext Front
[*]    Conn = 1/8, Color = Pink
[*]    DefAssociation = 0x2, Sequence = 0xe
[*]  Pin-ctls: 0x24: IN VREF_80
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 1
[*]     0x2b
[*]Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x80 0x80]
[*]  Pincap 0x00003737: IN OUT Detect Trigger ImpSense
[*]    Vref caps: HIZ 50 GRD 80 100
[*]  Pin Default 0x01813021: [Jack] Line In at Ext Rear
[*]    Conn = 1/8, Color = Blue
[*]    DefAssociation = 0x2, Sequence = 0x1
[*]  Pin-ctls: 0x20: IN VREF_HIZ
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 1
[*]     0x2c
[*]Node 0x16 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
[*]  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
[*]    Conn = 1/8, Color = Black
[*]    DefAssociation = 0x1, Sequence = 0x2
[*]  Pin-ctls: 0x40: OUT
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 1
[*]     0x2a
[*]Node 0x17 [Pin Complex] wcaps 0x40098d: Stereo Amp-Out R/L
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x80 0x80]
[*]  Pincap 0x00003737: IN OUT Detect Trigger ImpSense
[*]    Vref caps: HIZ 50 GRD 80 100
[*]  Pin Default 0x01a19020: [Jack] Mic at Ext Rear
[*]    Conn = 1/8, Color = Pink
[*]    DefAssociation = 0x2, Sequence = 0x0
[*]  Pin-ctls: 0x24: IN VREF_80
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 1
[*]     0x26
[*]Node 0x18 [Pin Complex] wcaps 0x400081: Stereo
[*]  Pincap 0x00000024: IN Detect
[*]  Pin Default 0x99331122: [Fixed] CD at Int ATAPI
[*]    Conn = ATAPI, Color = Black
[*]    DefAssociation = 0x2, Sequence = 0x2
[*]    Misc = NO_PRESENCE
[*]  Pin-ctls: 0x20: IN
[*]  Unsolicited: tag=00, enabled=0
[*]Node 0x19 [Power Widget] wcaps 0x500500: Mono
[*]  Power states:  D0 D3
[*]  Power: setting=D0, actual=D0
[*]  Connection: 2
[*]     0x20 0x21
[*]Node 0x1a [Pin Complex] wcaps 0x400000: Mono
[*]  Pincap 0x00000020: IN
[*]  Pin Default 0x511711f0: [N/A] Speaker at Int Rear
[*]    Conn = Analog, Color = Black
[*]    DefAssociation = 0xf, Sequence = 0x0
[*]    Misc = NO_PRESENCE
[*]  Pin-ctls: 0x20: IN
[*]Node 0x1b [Pin Complex] wcaps 0x40030d: Stereo Digital Amp-Out
[*]  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=1
[*]  Amp-Out vals:  [0x27 0x27]
[*]  Pincap 0x00000010: OUT
[*]  Pin Default 0x0145f1a0: [Jack] SPDIF Out at Ext Rear
[*]    Conn = Optical, Color = Other
[*]    DefAssociation = 0xa, Sequence = 0x0
[*]    Misc = NO_PRESENCE
[*]  Pin-ctls: 0x40: OUT
[*]  Connection: 1
[*]     0x02
[*]Node 0x1c [Pin Complex] wcaps 0x40020b: Stereo Digital Amp-In
[*]  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
[*]  Amp-In vals:  [0x97 0x97]
[*]  Pincap 0x00000020: IN
[*]  Pin Default 0x41c5f160: [N/A] SPDIF In at Ext Rear
[*]    Conn = Optical, Color = Other
[*]    DefAssociation = 0x6, Sequence = 0x0
[*]    Misc = NO_PRESENCE
[*]  Pin-ctls: 0x20: IN
[*]Node 0x1d [Pin Complex] wcaps 0x40030d: Stereo Digital Amp-Out
[*]  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=1
[*]  Amp-Out vals:  [0x27 0x27]
[*]  Pincap 0x00000010: OUT
[*]  Pin Default 0x1856f1b0: [Jack] Digital Out at Int HDMI
[*]    Conn = Digital, Color = Other
[*]    DefAssociation = 0xb, Sequence = 0x0
[*]    Misc = NO_PRESENCE
[*]  Pin-ctls: 0x40: OUT
[*]  Connection: 1
[*]     0x0b
[*]Node 0x1e [Audio Mixer] wcaps 0x200103: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x80 0x80]
[*]  Connection: 2
[*]     0x36 0x21
[*]Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
[*]Node 0x20 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
[*]  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
[*]  Connection: 8
[*]     0x39 0x33 0x38 0x3d 0x34 0x3b 0x18 0x1a
[*]Node 0x21 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
[*]  Amp-Out vals:  [0x1f 0x1f]
[*]  Connection: 1
[*]     0x20
[*]Node 0x22 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x80 0x80]
[*]  Connection: 2
[*]     0x37 0x21
[*]Node 0x23 [Vendor Defined Widget] wcaps 0xf00100: Mono
[*]  Connection: 18
[*]     0x11* 0x12 0x13 0x14 0x15 0x16 0x17 0x18 0x24 0x25 0x38 0x39 0x3a 0x3b 0x3c 0x3d 0x20 0x21
[*]Node 0x24 [Pin Complex] wcaps 0x40098d: Stereo Amp-Out R/L
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
[*]  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
[*]    Conn = 1/8, Color = Orange
[*]    DefAssociation = 0x1, Sequence = 0x1
[*]  Pin-ctls: 0x40: OUT
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 1
[*]     0x27
[*]Node 0x25 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
[*]  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
[*]    Conn = 1/8, Color = Grey
[*]    DefAssociation = 0x1, Sequence = 0x4
[*]  Pin-ctls: 0x40: OUT
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 1
[*]     0x28
[*]Node 0x26 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x80 0x80]
[*]  Connection: 2
[*]     0x32 0x21
[*]Node 0x27 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x80 0x80]
[*]  Connection: 2
[*]     0x05 0x21
[*]Node 0x28 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x80 0x80]
[*]  Connection: 2
[*]     0x0a 0x21
[*]Node 0x29 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x80 0x80]
[*]  Connection: 2
[*]     0x04 0x21
[*]Node 0x2a [Audio Mixer] wcaps 0x200103: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x80 0x80]
[*]  Connection: 2
[*]     0x06 0x21
[*]Node 0x2b [Audio Mixer] wcaps 0x200103: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x80 0x80]
[*]  Connection: 2
[*]     0x30 0x21
[*]Node 0x2c [Audio Mixer] wcaps 0x200103: Stereo Amp-In
[*]  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-In vals:  [0x80 0x80] [0x80 0x80]
[*]  Connection: 2
[*]     0x31 0x21
[*]Node 0x2d [Audio Mixer] wcaps 0x200100: Mono
[*]  Connection: 1
[*]     0x1e
[*]Node 0x2e [Vendor Defined Widget] wcaps 0xf00000: Mono
[*]Node 0x2f [Vendor Defined Widget] wcaps 0xf00100: Mono
[*]  Connection: 6
[*]     0x11* 0x12 0x14 0x15 0x16 0x17
[*]Node 0x30 [Audio Selector] wcaps 0x300101: Stereo
[*]  Connection: 3
[*]     0x03* 0x04 0x06
[*]Node 0x31 [Audio Selector] wcaps 0x300101: Stereo
[*]  Connection: 2
[*]     0x04* 0x0a
[*]Node 0x32 [Audio Selector] wcaps 0x300101: Stereo
[*]  Connection: 2
[*]     0x05* 0x04
[*]Node 0x33 [Audio Selector] wcaps 0x300101: Stereo
[*]  Connection: 3
[*]     0x3a* 0x25 0x24
[*]Node 0x34 [Audio Selector] wcaps 0x300101: Stereo
[*]  Connection: 3
[*]     0x3c* 0x25 0x24
[*]Node 0x35 [Vendor Defined Widget] wcaps 0xf00000: Mono
[*]Node 0x36 [Audio Selector] wcaps 0x300101: Stereo
[*]  Connection: 3
[*]     0x03 0x04* 0x06
[*]Node 0x37 [Audio Selector] wcaps 0x300101: Stereo
[*]  Connection: 3
[*]     0x03 0x04* 0x06
[*]Node 0x38 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Connection: 1
[*]     0x11
[*]Node 0x39 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Connection: 1
[*]     0x14
[*]Node 0x3a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Connection: 1
[*]     0x15
[*]Node 0x3b [Vendor Defined Widget] wcaps 0xf00000: Mono
[*]Node 0x3c [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Connection: 1
[*]     0x17
[*]Node 0x3d [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Connection: 1
[*]     0x12
[*](end collapsed section)
[/LIST]

[LIST]
[*]
[*]
[*][COLOR=brown][FONT=monospace]**ALSA Device nodes**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-----------------**[/FONT][/COLOR]
[*]
[*]crw-rw----  1 root audio 116,  0 Dec 22 11:46 /dev/snd/controlC0
[*]crw-rw----  1 root audio 116,  4 Dec 22 11:46 /dev/snd/hwC0D0
[*]crw-rw----  1 root audio 116,  1 Dec 22 11:46 /dev/snd/seq
[*]crw-rw----  1 root audio 116, 33 Dec 22 11:46 /dev/snd/timer
[*]
[*]/dev/snd/by-path:
[*]total 0
[*]drwxr-xr-x 2 root root  60 Dec 22 11:46 .
[*]drwxr-xr-x 3 root root 140 Dec 22 11:46 ..
[*]lrwxrwxrwx 1 root root  12 Dec 22 11:46 pci-0000:00:1b.0 -> ../controlC0
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Aplay/Arecord output**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------**[/FONT][/COLOR]
[*]
[*]APLAY
[*]
[*]**** List of PLAYBACK Hardware Devices ****
[*]
[*]ARECORD
[*]
[*]**** List of CAPTURE Hardware Devices ****
[*]
[*][COLOR=brown][FONT=monospace]**Amixer output**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-------------**[/FONT][/COLOR]
[*]
[*][COLOR=brown][FONT=monospace]**-------Mixer controls for card 0 [Intel]**[/FONT][/COLOR]
[*]
[*]Card hw:0 'Intel'/'HDA Intel at 0xf7ff8000 irq 57'
[*]  Mixer name        : 'Analog Devices AD1989B'
[*]  Components        : 'HDA:11d4989b,10438372,00100300'
[*]  Controls      : 0
[*]  Simple ctrls  : 0
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Alsactl output**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-------------**[/FONT][/COLOR]
[*]
[*][(following section hidden - click to display)]("javascript:showColl(2)")
[/LIST]

[LIST]
[*]state.Intel {
[*]        control {
[*]        }
[*]}
[*](end collapsed section)
[/LIST]

[LIST]
[*]
[*]
[*][COLOR=brown][FONT=monospace]**All Loaded Modules**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------------**[/FONT][/COLOR]
[*]
[*]Module
[*]binfmt_misc
[*]ppdev
[*]snd_hda_codec_analog
[*]snd_hda_intel
[*]snd_hda_codec
[*]snd_hwdep
[*]snd_pcm_oss
[*]snd_mixer_oss
[*]snd_pcm
[*]snd_seq_dummy
[*]snd_seq_oss
[*]snd_seq_midi
[*]snd_rawmidi
[*]snd_seq_midi_event
[*]snd_seq
[*]iptable_filter
[*]ip_tables
[*]snd_timer
[*]snd_seq_device
[*]x_tables
[*]usblp
[*]snd
[*]psmouse
[*]serio_raw
[*]soundcore
[*]snd_page_alloc
[*]asus_atk0110
[*]nvidia
[*]lp
[*]parport
[*]hid_logitech
[*]ff_memless
[*]usbhid
[*]ohci1394
[*]ieee1394
[*]sky2
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Sysfs Files**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-----------**[/FONT][/COLOR]
[*]
[*]/sys/class/sound/hwC0D0/init_pin_configs:
[*]0x11 0x02214030
[*]0x12 0x01014010
[*]0x13 0x511711f0
[*]0x14 0x02a1902e
[*]0x15 0x01813021
[*]0x16 0x01011012
[*]0x17 0x01a19020
[*]0x18 0x99331122
[*]0x1a 0x511711f0
[*]0x1b 0x0145f1a0
[*]0x1c 0x41c5f160
[*]0x1d 0x1856f1b0
[*]0x24 0x01016011
[*]0x25 0x01012014
[*]
[*]/sys/class/sound/hwC0D0/driver_pin_configs:
[*]
[*]/sys/class/sound/hwC0D0/user_pin_configs:
[*]
[*]/sys/class/sound/hwC0D0/init_verbs:
[*]
[*]
[*][COLOR=brown][FONT=monospace]**ALSA/HDA dmesg**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------------**[/FONT][/COLOR]
[*]
[*][   14.433026]   alloc kstat_irqs on node 0
[*][   14.433032] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[*][   14.433077]   alloc irq_desc for 57 on node 0
[*][   14.433078]   alloc kstat_irqs on node 0
[*][   14.433085] HDA Intel 0000:00:1b.0: irq 57 for MSI/MSI-X
[*][   14.433106] HDA Intel 0000:00:1b.0: setting latency timer to 64
[*][   14.433129]   alloc irq_desc for 24 on node 0
[*]--
[*][   14.566351] type=1505 audit(1261504012.182:21): operation="profile_replace" pid=1009 name=/usr/sbin/tcpdump
[*][   14.924904] hda_codec: AD1989B: BIOS auto-probing.
[*][   14.924960] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[*][   14.927141] hda_codec: cannot build controlsfor #0 (error -22)
[*][   14.940069] ppdev: user-space parallel port driver
[/LIST]

---

### Post by VertexPusher on 2009-12-22
> **domarm said:**
> when I open alsamixer it just says "**This sound device does not have any controls.**" Card: HDA Intel Chip: Analog Devices AD1989B
Did the same thing happen before you upgraded ALSA?

---

### Post by domarm on 2009-12-22
i was having all kinds of sound quality issues (crackling, skipping, stopping) before i upgraded, but i could adjust the volume. so no, i didn't get this error before

---

### Post by VertexPusher on 2009-12-22
> **domarm said:**
> i was having all kinds of sound quality issues (crackling, skipping, stopping) before i upgraded
And you are sure they were caused by ALSA?

Intel HDA is pretty much standard these days. I had 4 of those over the past few years. If there was a driver bug, I should have noticed.

The #1 source of crackling, skipping and drop-outs these days is PulseAudio. So before you upgrade ALSA (which is a non-trivial operation), you should first remove PulseAudio (which is trivial and easily reversible) to test if the issues go away. Usually they will.

---

### Post by domarm on 2009-12-22
Upgrading to the new version (1.0.22) of ALSA involves removing pulseaudio - it was removed before I upgraded. I even reinstalled the OS and followed the instructions again - I got fewer errors in the process, but I'm still having the problem that now I get no sound and it says "This sound device does not have any controls."

By the way the whole reason this is a problem in the first place is because the crackling and such started in a game that I'm running through WINE.

---

### Post by kbs1 on 2009-12-27
I have exactly the same problem, please help! I needed to install alsa 1.0.22, because my surround sound was not working. Now I have no sound at all, it's unbearable :(

---

### Post by Shrek01 on 2009-12-28
I use gnome-alsamixer, and I placed a shortcut on the taskbar for convenience.

---

### Post by SlugSlug on 2009-12-28
> **Shrek01 said:**
> I use gnome-alsamixer, and I placed a shortcut on the taskbar for convenience.


me too !

---

### Post by kbs1 on 2009-12-28
thats pointless, even the main system volume control is not visible, so no mixer works. Please give some ideas on what to try next, I'm out of any more ideas.

---

### Post by SlugSlug on 2009-12-28
> **Shrek01 said:**
> I use gnome-alsamixer, and I placed a shortcut on the taskbar for convenience.
  

 ^^


that will give you volume control

---

### Post by kbs1 on 2009-12-28
okay the problem here is that ALSA fails to recognize any controls for this sooud card, so that no mixer will work. Gnome-alsamixer does not work either.

This is the problem:

```
[kbs1@localhost ~]$ aplay -l
**** List of PLAYBACK Hardware Devices ****
[kbs1@localhost ~]$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
[kbs1@localhost ~]$ 
```

Now THAT is bad and I (we) really don't know how to fix this. Original poster: have you solved this issue?

Thank you!

---

### Post by kbs1 on 2009-12-28
**ALSA 1.0.22.1 FIXES THIS ISSUE!!!**

released just today. GREAT WORK ALSA TEAM!

---

### Post by domarm on 2010-01-29
> **kbs1 said:**
> Original poster: have you solved this issue?

Thank you!

indeed. as stated, ALSA 1.0.22.1 fixed this issue

---

