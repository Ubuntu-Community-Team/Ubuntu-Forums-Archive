---
title: "Help needed getting sound to work on Ubuntu Desktop 20.4"
date: 2020-07-30
forum: Multimedia Software
---

### Post by tristanbrotherton on 2020-07-30
I'm having trouble locating the issue that is preventing my internal sound card from working on Focal - In the GUI I only get the dummy device.
 Hardware probe: [https://linux-hardware.org/?probe=d01cc4f5cf](https://linux-hardware.org/?probe=d01cc4f5cf)


Running  `alsa-info --stdout`  gives me the below output:


```

alsactl: save_state:1595: No soundcards found...
cat: /tmp/alsa-info.eCla7TDuLz/alsactl.tmp: No such file or directory
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################


!!Script ran on: Thu Jul 30 19:57:32 UTC 2020




!!Linux Distribution
!!------------------


Ubuntu 20.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 20.04.1 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 20.04.1 LTS" HOME_URL="https://www.ubuntu.com/" SUPPORT_URL="https://help.ubuntu.com/" BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/" PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy" UBUNTU_CODENAME=focal




!!DMI Information
!!---------------


Manufacturer:      Intel(R) Client Systems
Product Name:      NUC8i5BEK
Product Version:   J72742-308
Firmware Version:  BECFL357.86A.0077.2019.1127.1452
Board Vendor:      Intel Corporation
Board Name:        NUC8BEB




!!ACPI Device Status Information
!!---------------


/sys/bus/acpi/devices/ACPI000C:00/status     15
/sys/bus/acpi/devices/ACPI000E:00/status     15
/sys/bus/acpi/devices/INT33A1:00/status      15
/sys/bus/acpi/devices/INT340E:00/status      15
/sys/bus/acpi/devices/INT34BB:00/status      15
/sys/bus/acpi/devices/INT3F0D:00/status      15
/sys/bus/acpi/devices/LNXPOWER:00/status     15
/sys/bus/acpi/devices/LNXPOWER:01/status     1
/sys/bus/acpi/devices/LNXPOWER:02/status     1
/sys/bus/acpi/devices/LNXPOWER:03/status     1
/sys/bus/acpi/devices/LNXPOWER:04/status     1
/sys/bus/acpi/devices/MSFT0101:00/status     15
/sys/bus/acpi/devices/PNP0103:00/status      15
/sys/bus/acpi/devices/PNP0C02:00/status      3
/sys/bus/acpi/devices/PNP0C02:04/status      3
/sys/bus/acpi/devices/PNP0C02:06/status      3
/sys/bus/acpi/devices/PNP0C09:00/status      11
/sys/bus/acpi/devices/PNP0C0C:00/status      15
/sys/bus/acpi/devices/PNP0C0E:00/status      11
/sys/bus/acpi/devices/PNP0C0F:00/status      9
/sys/bus/acpi/devices/PNP0C0F:01/status      9
/sys/bus/acpi/devices/PNP0C0F:02/status      9
/sys/bus/acpi/devices/PNP0C0F:03/status      9
/sys/bus/acpi/devices/PNP0C0F:04/status      9
/sys/bus/acpi/devices/PNP0C0F:05/status      9
/sys/bus/acpi/devices/PNP0C0F:06/status      9
/sys/bus/acpi/devices/PNP0C0F:07/status      9
/sys/bus/acpi/devices/PRP00001:00/status     11




!!Kernel Information
!!------------------


Kernel release:    5.4.0-42-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     k5.4.0-42-generic
Library version:    1.2.2
Utilities version:  1.2.2




!!Loaded ALSA modules
!!-------------------


snd_hda_intel




!!Sound Servers on this system
!!----------------------------


Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes




!!Soundcards recognised by ALSA
!!-----------------------------


 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xa8a20000 irq 142




!!PCI Soundcards installed in the system
!!--------------------------------------


00:1f.3 Audio device [0403]: Intel Corporation Cannon Point-LP High Definition Audio Controller [8086:9dc8] (rev 30) (prog-if 80)
    Subsystem: Intel Corporation Cannon Point-LP High Definition Audio Controller [8086:2074]




!!Modprobe options (Sound related)
!!--------------------------------


snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_hda_intel: model=auto


!!Loaded sound module options
!!---------------------------


!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    dmic_detect : Y
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    model : auto,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    pm_blacklist : Y
    position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    power_save : 1
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : -1
    snoop : -1




!!HDA-Intel Codec information
!!---------------------------
--startcollapse--


Codec: Realtek ALC233
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0235
Subsystem Id: 0x80862074
Revision Id: 0x100002
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 D3cold CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC233 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x3c 0x3c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x60]: 44100 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x57 0x57]
  Converter: stream=0, channel=0
  PCM:
    rates [0x60]: 44100 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC233 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x27 0x27]
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
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x97 0x97]
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
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 5
     0x18 0x19 0x1a 0x1b 0x1d
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x03 0x0b
Node 0x0e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0f [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00]
  Connection: 1
     0x0d
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x90a60150: [Fixed] Mic at Int N/A
    Conn = Digital, Color = Unknown
    DefAssociation = 0x5, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00010014: OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x40000000: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x15 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x16 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x17 [Pin Complex] wcaps 0x40050c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x19 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a11040: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1a [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001373c: IN OUT HP EAPD Detect
    Vref caps: HIZ 50 GRD 80 100
  EAPD 0x2: EAPD
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40900001: [N/A] Aux at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=76
Node 0x21 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Master Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x02211010: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=03, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x0c* 0x0d
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x00 0x00]
  Connection: 7
     0x18 0x19 0x1a 0x1b 0x1d 0x0b 0x12
Codec: Intel Kabylake HDMI
Address: 2
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x8086280b
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0, Clock-stop-OK
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1a]: 16 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1a]: 16 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1a]: 16 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x06 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x07 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x08 [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--




!!ALSA Device nodes
!!-----------------


crw-rw----+ 1 root audio 116, 11 Jul 30 12:46 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  9 Jul 30 12:46 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 10 Jul 30 12:46 /dev/snd/hwC0D2
crw-rw----+ 1 root audio 116,  3 Jul 30 12:46 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  2 Jul 30 12:46 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  8 Jul 30 12:46 /dev/snd/pcmC0D10p
crw-rw----+ 1 root audio 116,  4 Jul 30 12:46 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  5 Jul 30 12:46 /dev/snd/pcmC0D7p
crw-rw----+ 1 root audio 116,  6 Jul 30 12:46 /dev/snd/pcmC0D8p
crw-rw----+ 1 root audio 116,  7 Jul 30 12:46 /dev/snd/pcmC0D9p
crw-rw----+ 1 root audio 116,  1 Jul 30 12:46 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jul 30 12:46 /dev/snd/timer


/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jul 30 12:46 .
drwxr-xr-x 3 root root 300 Jul 30 12:46 ..
lrwxrwxrwx 1 root root  12 Jul 30 12:46 pci-0000:00:1f.3 -> ../controlC0




!!Aplay/Arecord output
!!--------------------


APLAY


aplay: device_list:274: no soundcards found...


ARECORD


arecord: device_list:274: no soundcards found...


!!Amixer output
!!-------------


!!-------Mixer controls for card PCH


Invalid card number.
Usage: amixer <options> [command]


!!Alsactl output
!!--------------
!!All Loaded Modules
!!------------------


ac97_bus
acpi_pad
acpi_tad
aesni_intel
af_alg
ahci
algif_hash
algif_skcipher
autofs4
bluetooth
bnep
bpfilter
btbcm
btintel
btrtl
btusb
ccm
cfg80211
cmac
coretemp
crc32_pclmul
crct10dif_pclmul
cryptd
crypto_simd
drm
drm_kms_helper
e1000e
ecc
ecdh_generic
fb_sys_fops
ghash_clmulni_intel
glue_helper
hid
hid_generic
i2c_algo_bit
i2c_i801
i915
input_leds
intel_cstate
intel_pch_thermal
intel_powerclamp
intel_rapl_common
intel_rapl_msr
intel_rapl_perf
intel_wmi_thunderbolt
ip6_tables
ip6table_filter
ip_tables
iptable_filter
iwlmvm
iwlwifi
joydev
kvm
kvm_intel
ledtrig_audio
libahci
libarc4
lp
mac80211
mac_hid
mei
mei_hdcp
mei_me
memstick
nls_iso8859_1
parport
parport_pc
pinctrl_cannonlake
pinctrl_intel
ppdev
rfcomm
rtsx_pci
rtsx_pci_ms
rtsx_pci_sdmmc
sch_fq_codel
snd
snd_compress
snd_hda_codec
snd_hda_codec_generic
snd_hda_codec_hdmi
snd_hda_codec_realtek
snd_hda_core
snd_hda_ext_core
snd_hda_intel
snd_hwdep
snd_intel_dspcfg
snd_pcm
snd_pcm_dmaengine
snd_rawmidi
snd_seq
snd_seq_device
snd_seq_midi
snd_seq_midi_event
snd_soc_acpi
snd_soc_acpi_intel_match
snd_soc_core
snd_soc_hdac_hda
snd_sof
snd_sof_intel_byt
snd_sof_intel_hda
snd_sof_intel_hda_common
snd_sof_intel_ipc
snd_sof_pci
snd_sof_xtensa_dsp
snd_timer
soundcore
syscopyarea
sysfillrect
sysimgblt
thunderbolt
uas
usb_storage
usbhid
video
wmi
wmi_bmof
x86_pkg_temp_thermal
x_tables
xt_multiport




!!Sysfs Files
!!-----------


/sys/class/sound/hwC0D0/init_pin_configs:
0x12 0x90a60150
0x14 0x40000000
0x17 0x411111f0
0x18 0x411111f0
0x19 0x02a11040
0x1a 0x411111f0
0x1b 0x411111f0
0x1d 0x40900001
0x1e 0x411111f0
0x21 0x02211010


/sys/class/sound/hwC0D0/driver_pin_configs:


/sys/class/sound/hwC0D0/user_pin_configs:


/sys/class/sound/hwC0D0/init_verbs:


/sys/class/sound/hwC0D0/hints:


/sys/class/sound/hwC0D2/init_pin_configs:
0x05 0x18560010
0x06 0x18560010
0x07 0x18560010


/sys/class/sound/hwC0D2/driver_pin_configs:


/sys/class/sound/hwC0D2/user_pin_configs:


/sys/class/sound/hwC0D2/init_verbs:


/sys/class/sound/hwC0D2/hints:




!!ALSA/HDA dmesg
!!--------------


[    0.178206] ACPI: Added _OSI(Linux-Dell-Video)
[    0.178206] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.178207] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
--
[    4.084021] iwlwifi 0000:00:14.3 wlp0s20f3: renamed from wlan0
[    4.145596] snd_hda_intel 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040380
[    4.150302] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    4.156923] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    4.160669] intel_rapl_common: Found RAPL domain package
--
[    4.160672] intel_rapl_common: Found RAPL domain dram
[    4.214280] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC233: line_outs=1 (0x21/0x0/0x0/0x0/0x0) type:hp
[    4.214281] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    4.214282] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    4.214283] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    4.214283] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    4.214284] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x19
[    4.214285] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
[    4.488039] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input8
[    4.488081] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input9
[    4.488116] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input10
[    4.488146] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input11
[    4.488180] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
[    4.488211] input: HDA Intel PCH HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
[    4.488239] input: HDA Intel PCH HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
[    4.537048] audit: type=1400 audit(1596138400.814:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=738 comm="apparmor_parser"

```

---

### Post by linuxhw on 2020-07-31
Try kernel 5.7: [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7.11/amd64/]("https://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v5.7.11/amd64/")
 I see new commits in the drivers listed for your problem device: [https://linux-hardware.org/?id=pci:8086-9dc8-8086-2074](https://linux-hardware.org/?id=pci:8086-9dc8-8086-2074)

---

