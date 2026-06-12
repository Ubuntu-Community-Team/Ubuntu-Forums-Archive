---
title: "Upgrade to 12.10 borked sound and pulseaudio"
date: 2013-06-27
forum: Multimedia Software
---

### Post by trumpeteersman on 2013-06-27
My specs: Thinkpad T61
Kubuntu 12.10 64-bit
KDE 4.10.4
Kernels tested: 3.5.0-34-generic, 3.5.0-34-lowlatency, 3.9-6.dmz.2-liquorix-amd64
groups: *USER* adm disk dialout cdrom audio www-data plugdev fuse lpadmin netdev admin sambashare pulse vboxusers jupiter realtime

**Cannot get parts of my sound system to work.**

Ever since pulseaudio started being included in kde (I have had same system since before kde4), my single soundcard has multiplexed into many confusing variants as you can see by my attachment. Before, I managed to move around these device to the right position by using the test button. After I upgraded to 12.10(foolishly, but I wanted a working nepomuk) ALL of my sound stopped working.  After hours of purging/reinstalling pulseaudio, editing .asoundrc/alsa.conf/pulseaudio.conf I managed to get phonon to recognize my Intel soundcard again(the extra cards came back as well). I managed to get Amarok/VLC and the phonon tester to work, but not sound from *Firefox*(*Iron* sound works fine) and **MOST** importantly: I could not get jack to work for my music creation stuff. I get an error:

```
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open failed with -1
Failed to open server
00:54:43.629 JACK was stopped with exit status=255.
00:54:43.630 Post-shutdown script...
00:54:43.630 killall jackd
jackd: no process found
00:54:44.059 Post-shutdown script terminated with exit status=256.
00:54:45.281 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
```


Here is the output of alsa-info.sh:
```

!!Linux Distribution
!!------------------

Ubuntu 12.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu quantal (12.10)"


!!DMI Information
!!---------------

Manufacturer:      LENOVO
Product Name:      765801U
Product Version:   ThinkPad T61


!!Kernel Information
!!------------------

Kernel release:    3.9-6.dmz.2-liquorix-amd64
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.9-6.dmz.2-liquorix-amd64
Library version:    1.0.25
Utilities version:  1.0.25


!!Loaded ALSA modules
!!-------------------

snd_virmidi
snd_hda_intel
thinkpad_acpi


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [VirMIDI        ]: VirMIDI - VirMIDI
                      Virtual MIDI Card 1
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe020000 irq 51
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw 7KHT24WW-1.08


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:284b (rev 03)
	Subsystem: 17aa:20ac


!!Modprobe options (Sound related)
!!--------------------------------

snd-virtuoso: index=0
snd-hda-intel: index=1
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

!!Module: snd_virmidi
	enable : Y,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	midi_devs : 4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4

!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N
	snoop : Y

!!Module: thinkpad_acpi
	brightness_enable : 2
	brightness_mode : 4
	enable : Y
	experimental : 0
	fan_control : Y
	force_load : N
	hotkey_report_mode : 0
	id : ThinkPadEC
	index : -536870912
	volume_capabilities : 0
	volume_control : N
	volume_mode : 3


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Analog Devices AD1984
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x11d41984
Subsystem Id: 0x17aa20d7
Revision Id: 0x100400
No Modem Function Group found
Default PCM:
    rates [0x7ff]: 8000 11025 16000 22050 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Default Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
State of AFG node 0x01:
  Power states:  D0 D3
  Power: setting=D0, actual=D0
GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=1, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x30311: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Control: name="IEC958 Playback Source", index=0, device=0
  Device: name="AD198x Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 3 samples
  Connection: 3
     0x01* 0x08 0x09
Node 0x03 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Control: name="PCM Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="AD198x Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
  Amp-Out vals:  [0x27 0x27]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x05 [Audio Input] wcaps 0x10050b: Stereo Amp-In
  Amp-In caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
  Amp-In vals:  [0xa7 0xa7]
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x17
Node 0x06 [Audio Input] wcaps 0x10050b: Stereo Amp-In
  Amp-In caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
  Amp-In vals:  [0xa7 0xa7]
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x18
Node 0x07 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x22 0x21
Node 0x08 [Audio Input] wcaps 0x100501: Stereo
  Device: name="AD198x Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x09 [Audio Input] wcaps 0x100501: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x0a [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x21
Node 0x0b [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x0f 0x21
Node 0x0c [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Input Source", index=0, device=0
  Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 5
     0x14 0x15* 0x16 0x20 0x25
Node 0x0d [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Input Source", index=1, device=0
  Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 5
     0x14* 0x15 0x16 0x20 0x25
Node 0x0e [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x03 0x04*
Node 0x0f [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x03* 0x04
Node 0x10 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x0f, nsteps=0x0f, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x8f]
Node 0x11 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000001f: OUT HP Detect Trigger ImpSense
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x07
Node 0x12 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001001f: OUT HP EAPD Detect Trigger ImpSense
  EAPD 0x2: EAPD
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x0a
Node 0x13 [Pin Complex] wcaps 0x40050c: Mono Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00010010: OUT EAPD
  EAPD 0x0:
  Pin Default 0x511301f0: [N/A] Speaker at Int Rear
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x14 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003727: IN Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a15021: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Red
    DefAssociation = 0x2, Sequence = 0x1
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x15 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003727: IN Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x90a7012e: [Fixed] Mic at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x2, Sequence = 0xe
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x16 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
  Pin Default 0x593301f0: [N/A] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0b
Node 0x17 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x55a601f0: [N/A] Mic at Int Top
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN
Node 0x18 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x55a601f0: [N/A] Mic at Int Top
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x19 [Power Widget] wcaps 0x500500: Mono
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x20 0x21
Node 0x1a [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x91f311f0: [Fixed] Other at Int Rear
    Conn = ATAPI, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1b [Pin Complex] wcaps 0x40030d: Stereo Digital Amp-Out
  Control: name="IEC958 Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=1
  Amp-Out vals:  [0x0f 0x0f]
  Pincap 0x00000010: OUT
  Pin Default 0x214411a0: [Jack] SPDIF Out at Sep Rear
    Conn = RCA, Color = Black
    DefAssociation = 0xa, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x02
Node 0x1c [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x21a15020: [Jack] Mic at Sep Rear
    Conn = 1/8, Color = Red
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x24
Node 0x1d [Vendor Defined Widget] wcaps 0xf00100: Mono
  Connection: 25
     0x07* 0x19 0x0a 0x0b 0x0c 0x0d 0x0e 0x0f 0x1a 0x1c 0x11 0x12 0x13 0x14 0x15 0x16 0x1e 0x1f 0x20 0x21 0x22 0x23 0x24 0x25 0x26
Node 0x1e [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x0e 0x21
Node 0x1f [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x1e
Node 0x20 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Internal Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Internal Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=3, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=3, ofs=0
  Control: name="Dock Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Dock Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x07 0x07] [0x80 0x80] [0x80 0x80] [0x8f 0x80] [0x00 0x00]
  Connection: 5
     0x14 0x15 0x16 0x1a 0x25
Node 0x21 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1f 0x1f]
  Connection: 1
     0x20
Node 0x22 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x03 0x04*
Node 0x23 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x03* 0x04
Node 0x24 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x23 0x21
Node 0x25 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Dock Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x1c
Node 0x26 [Vendor Defined Widget] wcaps 0xf00100: Mono
  Connection: 3
     0x14* 0x15 0x1c
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---T+ 1 root audio 116,  6 Jun 27 00:53 /dev/snd/controlC0
crw-rw---T+ 1 root audio 116, 12 Jun 27 00:53 /dev/snd/controlC1
crw-rw---T+ 1 root audio 116,  7 Jun 27 00:53 /dev/snd/controlC29
crw-rw---T+ 1 root audio 116, 11 Jun 27 00:53 /dev/snd/hwC1D0
crw-rw---T+ 1 root audio 116,  5 Jun 27 00:53 /dev/snd/midiC0D0
crw-rw---T+ 1 root audio 116,  4 Jun 27 00:53 /dev/snd/midiC0D1
crw-rw---T+ 1 root audio 116,  3 Jun 27 00:53 /dev/snd/midiC0D2
crw-rw---T+ 1 root audio 116,  2 Jun 27 00:53 /dev/snd/midiC0D3
crw-rw---T+ 1 root audio 116, 10 Jun 27 00:54 /dev/snd/pcmC1D0c
crw-rw---T+ 1 root audio 116,  9 Jun 27 01:17 /dev/snd/pcmC1D0p
crw-rw---T+ 1 root audio 116,  8 Jun 27 01:17 /dev/snd/pcmC1D1p
crw-rw---T+ 1 root audio 116,  1 Jun 27 00:53 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 Jun 27 00:53 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root 100 Jun 27 00:53 .
drwxr-xr-x 3 root root 320 Jun 27 00:53 ..
lrwxrwxrwx 1 root root  12 Jun 27 00:53 pci-0000:00:1b.0 -> ../controlC1
lrwxrwxrwx 1 root root  12 Jun 27 00:53 platform-snd_virmidi.0 -> ../controlC0
lrwxrwxrwx 1 root root  13 Jun 27 00:53 platform-thinkpad_acpi -> ../controlC29


!!ALSA configuration files
!!------------------------

!!User specific config file (~/.asoundrc)

pcm.!default {
    type hw
    card 1
}
 
ctl.!default {
    type hw
    card 1
}


!!System wide config file (/etc/asound.conf)

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 1: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [VirMIDI]

Card hw:0 'VirMIDI'/'Virtual MIDI Card 1'
  Mixer name	: ''
  Components	: ''
  Controls      : 0
  Simple ctrls  : 0

!!-------Mixer controls for card 1 [Intel]

Card hw:1 'Intel'/'HDA Intel at 0xfe020000 irq 51'
  Mixer name	: 'Analog Devices AD1984'
  Components	: 'HDA:11d41984,17aa20d7,00100400'
  Controls      : 34
  Simple ctrls  : 19
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Speaker',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB]
  Front Right: Playback 39 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 7 [23%] [-24.00dB] [on]
  Front Right: Playback 7 [23%] [-24.00dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 15 [38%] [-36.00dB] [on]
  Front Right: Playback 15 [38%] [-36.00dB] [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'PCM' 'ADC'
  Item0: 'PCM'
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 15 [48%] [-12.00dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 0 [0%] [-58.50dB] [on]
  Front Right: Capture 0 [0%] [-58.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 0 [0%] [-58.50dB] [on]
  Front Right: Capture 0 [0%] [-58.50dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 0 [0%] [-30.00dB]
  Front Right: Capture 0 [0%] [-30.00dB]
Simple mixer control 'Dock Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Dock Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Internal Mic' 'Mix' 'Dock Mic'
  Item0: 'Internal Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Internal Mic' 'Mix' 'Dock Mic'
  Item0: 'Mic'
Simple mixer control 'Internal Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]

!!-------Mixer controls for card 29 [ThinkPadEC]

Card hw:29 'ThinkPadEC'/'ThinkPad Console Audio Control at EC reg 0x30, fw 7KHT24WW-1.08'
  Mixer name	: 'ThinkPad EC 7KHT24WW-1.08'
  Components	: ''
  Controls      : 1
  Simple ctrls  : 1
Simple mixer control 'Console',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.VirMIDI {
	control {
	}
}
state.Intel {
	control.1 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 39
		value.1 39
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 39'
			dbmin -5850
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.2 {
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
	control.3 {
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
	control.4 {
		iface MIXER
		name 'Mic Playback Volume'
		value.0 7
		value.1 7
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -2400
			dbvalue.1 -2400
		}
	}
	control.5 {
		iface MIXER
		name 'Mic Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.6 {
		iface MIXER
		name 'Internal Mic Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.7 {
		iface MIXER
		name 'Internal Mic Playback Switch'
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
		name 'Beep Playback Volume'
		value.0 15
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -1200
			dbvalue.1 -3450
		}
	}
	control.9 {
		iface MIXER
		name 'Beep Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.10 {
		iface MIXER
		name 'Dock Mic Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.11 {
		iface MIXER
		name 'Dock Mic Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.12 {
		iface MIXER
		name 'Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.13 {
		iface MIXER
		name 'Internal Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.14 {
		iface MIXER
		name 'Dock Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.15 {
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 54'
			dbmin -5850
			dbmax 2250
			dbvalue.0 -5850
			dbvalue.1 -5850
		}
	}
	control.16 {
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.17 {
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 54'
			dbmin -5850
			dbmax 2250
			dbvalue.0 -5850
			dbvalue.1 -5850
		}
	}
	control.18 {
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.19 {
		iface MIXER
		name 'Input Source'
		value 'Internal Mic'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Mic
			item.1 'Internal Mic'
			item.2 Mix
			item.3 'Dock Mic'
		}
	}
	control.20 {
		iface MIXER
		name 'Input Source'
		index 1
		value Mic
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Mic
			item.1 'Internal Mic'
			item.2 Mix
			item.3 'Dock Mic'
		}
	}
	control.21 {
		iface MIXER
		name 'IEC958 Playback Volume'
		value.0 15
		value.1 15
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 39'
			dbmin -5850
			dbmax 0
			dbvalue.0 -3600
			dbvalue.1 -3600
		}
	}
	control.22 {
		iface MIXER
		name 'IEC958 Playback Source'
		value PCM
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 PCM
			item.1 ADC
		}
	}
	control.23 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.24 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.25 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.26 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.27 {
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.28 {
		iface MIXER
		name 'Master Playback Volume'
		value 39
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 39'
			dbmin -5850
			dbmax 0
			dbvalue.0 0
		}
	}
	control.29 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.30 {
		iface PCM
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.31 {
		iface PCM
		name 'Capture Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.32 {
		iface PCM
		name 'Capture Channel Map'
		index 1
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.33 {
		iface PCM
		device 1
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.34 {
		iface MIXER
		name 'Digital Capture Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 120'
			tlv '0000000100000008fffff44800000032'
			dbmin -3000
			dbmax 3000
			dbvalue.0 -3000
			dbvalue.1 -3000
		}
	}
}
state.ThinkPadEC {
	control.1 {
		iface MIXER
		name 'Console Playback Switch'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
iptable_filter
ip_tables
x_tables
af_packet
nfsd
bnep
rfcomm
bluetooth
nfs_acl
auth_rpcgss
parport_pc
ppdev
binfmt_misc
nfs
fscache
lockd
sunrpc
dm_crypt
snd_hda_codec_analog
coretemp
arc4
kvm_intel
iwl3945
iwlegacy
mac80211
kvm
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
cfg80211
snd_pcm
snd_page_alloc
thinkpad_acpi
joydev
psmouse
microcode
snd_virmidi
snd_seq_virmidi
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
pcmcia
dm_multipath
snd_timer
snd_seq_device
scsi_dh
ehci_pci
tp_smapi
thinkpad_ec
snd
serio_raw
rtc_cmos
soundcore
ehci_hcd
yenta_socket
rfkill
uinput
nvram
pcmcia_rsrc
pcmcia_core
lpc_ich
ac
battery
evdev
lp
parport
fuse
ext2
appletalk
ipx
p8022
psnap
llc
p8023
ext4
jbd2
mbcache
crc16
btrfs
raid6_pq
zlib_deflate
xor
crc32c
libcrc32c
hid_generic
usbhid
dm_mirror
dm_region_hash
dm_log
dm_mod
sr_mod
cdrom
ata_generic
sd_mod
pata_acpi
i915
drm_kms_helper
drm
i2c_algo_bit
i2c_core
video
thermal
wmi
ahci
libahci
ata_piix
libata
scsi_mod
button
xhci_hcd
intel_agp
intel_gtt
e1000e
ptp
pps_core
uhci_hcd


!!Sysfs Files
!!-----------

/sys/class/sound/hwC1D0/init_pin_configs:
0x11 0x0221401f
0x12 0x90170110
0x13 0x511301f0
0x14 0x02a15021
0x15 0x90a7012e
0x16 0x593301f0
0x17 0x55a601f0
0x18 0x55a601f0
0x1a 0x91f311f0
0x1b 0x214411a0
0x1c 0x21a15020

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
hda_intel: probe_mask set to 0x1 for device 17aa:20ac
snd_hda_intel 0000:00:1b.0: irq 51 for MSI/MSI-X
iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s

```

My .asoundrc:
```
pcm.!default {
    type hw
    card 1
}
 
ctl.!default {
    type hw
    card 1
}
```

My /usr/share/alsa/alsa.conf.d/50-pulseaudio.conf:
```
# Add a specific named PulseAudio pcm and ctl (typically useful for testing)

pcm.pulse {
    type pulse
    hint {
        show on
        description "PulseAudio Sound Server"
    }
}

ctl.pulse {
    type pulse
}

```

Pulseaudio makes KDE require users to have well-rounded linux expertise to troubleshoot. This has struck beyond my expertise. It would be nice to *Reset* the sound system configurations. But purging/reinstalling pulseaudio did nothing. I wanted to just upgrade again to the next dist-release, but I only have 1.59GB left on root(to upgrade requires more than 2GB), and I do not trust resizing important partitions. I am however, considering moving /var to the same partition as /home which would give me enough space.

My belief is that the problem is with the card order. Here is my /proc/asound/cards:
```
 
0 [VirMIDI        ]: VirMIDI - VirMIDI
                      Virtual MIDI Card 1
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe020000 irq 51
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw 7KHT24WW-1.08
```

I don't know what to do. Can someone please help me?

---

### Post by trumpeteersman on 2013-07-09
More information: Sometimes sound in Firefox works but then regresses without changs being made. I don't like this feature ... :(

---

### Post by trumpeteersman on 2013-08-04
Still playing hackey sack with multiple "Sound Devices" in phonon because Amarok/VLC/Firefox/Chrome decides to change the default device. 

Any ideas?

---

### Post by Yellow Pasque on 2013-08-04
With that .asoundrc, you're basically bypassing pulseaudio and giving programs direct access to the sound device. That's generally not a good idea, unless you have a good soundcard  with a hardware mixer. It's not good for your user to be in the audio group, either (if that's what you meant when you listed the groups).

If you remove the asound customizations, what happens then?

---

### Post by trumpeteersman on 2013-08-10
Sorry, it has been a while. I set my default sound card to 1:0 and most sound works except my Jack stuff and Firefox (Chrome works fine).

pulseaudo apparently doesn't run at all:
```
$ pulseaudio 
E: [pulseaudio] main.c: Assertion 'execv(rp, argv) == 0' failed at daemon/main.c:450, function main(). Aborting.
Aborted (core dumped)
```

Removed .asoundrc. No change.

Why is it bad to be in the audio group?

---

### Post by Yellow Pasque on 2013-08-10
> **trumpeteersman said:**
> Why is it bad to be in the audio group?

If you have multiple users logged in, they can end up blocking each other from the sound device. 

What other pulseaudio or alsa configuration files have you changed along the way?

---

### Post by trumpeteersman on 2013-08-10
I also changed the default.pa file, but reverted back to the origional months ago trying to fix this. I removed/reinstalled pulseaudio: No change. There are probably a few alsa configs that were changed for use with my Jack system back when I installed it years ago. I believe that some of the Jack stuff I did a while back required me to add the audio group. Only one user on this machine.

---

### Post by trumpeteersman on 2013-08-12
Since a reboot after the pulseaudio reinstall, I no longer have ANY sound. Phonon only shows "Pulseaudio sound server". Autoremoved pulseaudio and its packages, and I got most of my sound back. Still back to square one. Apparently pulseaudio does not like to run on my machine anymore.

---

