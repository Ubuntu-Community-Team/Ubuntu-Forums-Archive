---
title: "No Sound through DisplayPort Nvidia GPU"
date: 2020-12-10
forum: Multimedia Software
---

### Post by midnightferret on 2020-12-10
Hello,

I am running Ubuntu 20.04.1 on a Lenovo Legion Y540 which is connected by a mini DiplayPort to an AOPEN monitor which is connected to my speakers through an audio port on the monitor. I cannot get the DisplayPort/monitor device to show up in the sound settings. (it does work in Windows, so I know it's possible.) I have tried a couple of fixes but I haven't been able to get the device to show up. Below I have included my system info and the output of the alsa-info.sh script. Please let me know if I can provide more info. Thank you in advance if you can help me solve this issue - I'm clearly in over my head.

System Info:

```
      -+ssssssssssssssssssyyssss+-         OS: Ubuntu 20.04.1 LTS x86_64 
    .ossssssssssssssssssdMMMNysssso.       Host: 81SX Legion Y540-15IRH 
   /ssssssssssshdmmNNmmyNMMMMhssssss/      Kernel: 5.4.0-56-generic 
  +ssssssssshmydMMMMMMMNddddyssssssss+     Uptime: 20 mins 
 /sssssssshNMMMyhhyyyyhmNMMMNhssssssss/    Packages: 2555 (dpkg), 26 (snap) 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Shell: bash 5.0.17 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   Resolution: 1920x1080, 2560x1440 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   DE: GNOME 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   WM: Mutter 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   WM Theme: Adwaita 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Theme: Yaru-dark [GTK2/3] 
 /sssssssshNMMMyhhyyyyhdNMMMNhssssssss/    Icons: Yaru [GTK2/3] 
  +sssssssssdmydMMMMMMMMddddyssssssss+     Terminal: gnome-terminal 
   /ssssssssssshdmNNNNmyNMMMMhssssss/      CPU: Intel i7-9750H (12) @ 4.500GHz 
    .ossssssssssssssssssdMMMNysssso.       GPU: NVIDIA GeForce GTX 1660 Ti Mobile 
      -+sssssssssssssssssyyyssss+-         Memory: 2543MiB / 15931MiB 
```

Output of alsa-info.txt:

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.65
!!################################

!!Script ran on: Thu Dec 10 15:22:30 UTC 2020


!!Linux Distribution
!!------------------

Ubuntu 20.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 20.04.1 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 20.04.1 LTS" HOME_URL="https://www.ubuntu.com/" SUPPORT_URL="https://help.ubuntu.com/" BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/" PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy" UBUNTU_CODENAME=focal


!!DMI Information
!!---------------

Manufacturer:      LENOVO
Product Name:      81SX
Product Version:   Legion Y540-15IRH
Firmware Version:  BHCN36WW
System SKU:        LENOVO_MT_81SX_BU_idea_FM_Legion Y540-15IRH
Board Vendor:      LENOVO
Board Name:        LNVNB161216


!!ACPI Device Status Information
!!---------------

/sys/bus/acpi/devices/ACPI0003:00/status 	 15
/sys/bus/acpi/devices/ACPI000C:00/status 	 15
/sys/bus/acpi/devices/ACPI000E:00/status 	 15
/sys/bus/acpi/devices/INT33A1:00/status 	 15
/sys/bus/acpi/devices/INT3400:00/status 	 15
/sys/bus/acpi/devices/INT3403:00/status 	 15
/sys/bus/acpi/devices/INT3403:01/status 	 15
/sys/bus/acpi/devices/INT3403:02/status 	 15
/sys/bus/acpi/devices/INT3403:03/status 	 15
/sys/bus/acpi/devices/INT3403:04/status 	 15
/sys/bus/acpi/devices/INT340E:00/status 	 15
/sys/bus/acpi/devices/INT3450:00/status 	 15
/sys/bus/acpi/devices/INT3F0D:00/status 	 15
/sys/bus/acpi/devices/LNXPOWER:00/status 	 1
/sys/bus/acpi/devices/LNXPOWER:01/status 	 255
/sys/bus/acpi/devices/LNXPOWER:02/status 	 1
/sys/bus/acpi/devices/LNXPOWER:03/status 	 15
/sys/bus/acpi/devices/LNXPOWER:04/status 	 1
/sys/bus/acpi/devices/LNXPOWER:07/status 	 1
/sys/bus/acpi/devices/LNXPOWER:08/status 	 1
/sys/bus/acpi/devices/LNXPOWER:09/status 	 1
/sys/bus/acpi/devices/LNXPOWER:0a/status 	 1
/sys/bus/acpi/devices/LNXPOWER:0c/status 	 1
/sys/bus/acpi/devices/LNXVIDEO:00/status 	 15
/sys/bus/acpi/devices/MSFT0001:00/status 	 15
/sys/bus/acpi/devices/MSFT0001:01/status 	 15
/sys/bus/acpi/devices/MSFT0101:00/status 	 15
/sys/bus/acpi/devices/PNP0103:00/status 	 15
/sys/bus/acpi/devices/PNP0C02:00/status 	 3
/sys/bus/acpi/devices/PNP0C02:01/status 	 3
/sys/bus/acpi/devices/PNP0C02:04/status 	 3
/sys/bus/acpi/devices/PNP0C04:00/status 	 31
/sys/bus/acpi/devices/PNP0C09:00/status 	 15
/sys/bus/acpi/devices/PNP0C0A:00/status 	 31
/sys/bus/acpi/devices/PNP0C0C:00/status 	 15
/sys/bus/acpi/devices/PNP0C0D:00/status 	 15
/sys/bus/acpi/devices/PRP00001:00/status 	 11
/sys/bus/acpi/devices/USBC000:00/status 	 15
/sys/bus/acpi/devices/VPC2004:00/status 	 15
/sys/bus/acpi/devices/device:24/status 	 15


!!Kernel Information
!!------------------

Kernel release:    5.4.0-56-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k5.4.0-56-generic
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
                      HDA Intel PCH at 0xb451c000 irq 126


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.3 Audio device [0403]: Intel Corporation Cannon Lake PCH cAVS [8086:a348] (rev 10)
	Subsystem: Lenovo Cannon Lake PCH cAVS [17aa:380f]


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
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	pm_blacklist : Y
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : N
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : -1
	snoop : -1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC257
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0257
Subsystem Id: 0x17aa3810
Revision Id: 0x100001
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
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x57 0x57]
  Converter: stream=1, channel=0
  PCM:
    rates [0x60]: 44100 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC257 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=1, channel=0
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
Node 0x07 [Audio Input] wcaps 0x10051b: Stereo Amp-In
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
     0x24
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC257 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x33 0x33]
  Converter: stream=1, channel=0
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
Node 0x0b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0d [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x90a60120: [Fixed] Mic at Int N/A
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40000000: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
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
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x02
Node 0x15 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x16 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
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
  Pin Default 0x04a11030: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
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
  Pincap 0x00013734: IN OUT EAPD Detect
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
     0x02* 0x03
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40661b45: [N/A] Modem Line at Ext N/A
    Conn = Digital, Color = Black
    DefAssociation = 0x4, Sequence = 0x5
    Misc = NO_PRESENCE
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
  Processing caps: benign=0, ncoeff=142
Node 0x21 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x0421101f: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x02 0x03*
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x13
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x00 0x00]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x12
Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x12* 0x13
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  5 Dec 10 09:15 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  4 Dec 10 09:15 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  3 Dec 10 09:17 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  2 Dec 10 09:17 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  1 Dec 10 09:15 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Dec 10 09:15 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Dec 10 09:15 .
drwxr-xr-x 3 root root 180 Dec 10 09:15 ..
lrwxrwxrwx 1 root root  12 Dec 10 09:15 pci-0000:00:1f.3 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC257 Analog [ALC257 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC257 Analog [ALC257 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card PCH

Card hw:0 'PCH'/'HDA Intel PCH at 0xb451c000 irq 126'
  Mixer name	: 'Realtek ALC257'
  Components	: 'HDA:10ec0257,17aa3810,00100001'
  Controls      : 18
  Simple ctrls  : 8
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 0 [0%] [-65.25dB] [off]
  Front Right: Playback 0 [0%] [-65.25dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 254 [100%] [-0.20dB]
  Front Right: Playback 254 [100%] [-0.20dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 63
  Front Left: Capture 51 [81%] [21.00dB] [on]
  Front Right: Capture 51 [81%] [21.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]


!!Alsactl output
!!--------------

--startcollapse--
state.PCH {
	control.1 {
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 -6525
			dbvalue.1 -6525
		}
	}
	control.2 {
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.3 {
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
	control.4 {
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
	control.5 {
		iface MIXER
		name 'Auto-Mute Mode'
		value Enabled
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 Enabled
		}
	}
	control.6 {
		iface MIXER
		name 'Capture Volume'
		value.0 51
		value.1 51
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 63'
			dbmin -1725
			dbmax 3000
			dbvalue.0 2100
			dbvalue.1 2100
		}
	}
	control.7 {
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
	control.8 {
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
	control.9 {
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
	control.10 {
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
	control.11 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.12 {
		iface CARD
		name 'Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.13 {
		iface CARD
		name 'Internal Mic Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.14 {
		iface CARD
		name 'Headphone Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.15 {
		iface CARD
		name 'Speaker Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.16 {
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
	control.17 {
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
	control.18 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 254
		value.1 254
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 255'
			tlv '0000000100000008ffffec1400000014'
			dbmin -5100
			dbmax 0
			dbvalue.0 -20
			dbvalue.1 -20
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

8250_dw
ac97_bus
acpi_pad
acpi_tad
acpi_thermal_rel
aesni_intel
af_alg
ahci
algif_hash
algif_skcipher
autofs4
binfmt_misc
bluetooth
bnep
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
ecc
ecdh_generic
fb_sys_fops
ghash_clmulni_intel
glue_helper
hid
hid_generic
hid_multitouch
i2c_hid
i2c_i801
i2c_nvidia_gpu
ideapad_laptop
idma64
input_leds
int3400_thermal
int3403_thermal
int340x_thermal_zone
intel_cstate
intel_lpss
intel_lpss_pci
intel_pch_thermal
intel_powerclamp
intel_rapl_common
intel_rapl_msr
intel_soc_dts_iosf
intel_wmi_thunderbolt
ip_tables
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
mc
mei
mei_hdcp
mei_me
nf_tables
nfnetlink
nls_iso8859_1
nvidia
nvidia_drm
nvidia_modeset
nvidia_uvm
nvme
nvme_core
parport
parport_pc
pinctrl_cannonlake
pinctrl_intel
ppdev
processor_thermal_device
r8169
rapl
realtek
rfcomm
sch_fq_codel
serio_raw
snd
snd_compress
snd_hda_codec
snd_hda_codec_generic
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
sparse_keymap
syscopyarea
sysfillrect
sysimgblt
typec
typec_ucsi
ucsi_acpi
ucsi_ccg
uhid
usbhid
uvcvideo
vboxdrv
vboxnetadp
vboxnetflt
video
videobuf2_common
videobuf2_memops
videobuf2_v4l2
videobuf2_vmalloc
videodev
virt_dma
wmi
wmi_bmof
x86_pkg_temp_thermal
x_tables


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x12 0x90a60120
0x13 0x40000000
0x14 0x90170110
0x18 0x411111f0
0x19 0x04a11030
0x1a 0x411111f0
0x1b 0x411111f0
0x1d 0x40661b45
0x1e 0x411111f0
0x21 0x0421101f

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:


!!ALSA/HDA dmesg
!!--------------

[    0.147335] ACPI: Added _OSI(Linux-Dell-Video)
[    0.147335] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.147335] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
--
[   17.921387] proc_thermal 0000:00:04.0: Creating sysfs group for PROC_THERMAL_PCI
[   18.690994] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[   19.639421] dw-apb-uart.2: ttyS4 at MMIO 0xb452a000 (irq = 20, base_baud = 115200) is a 16550A
--
[   19.964094] Copyright(c) 2003- 2015 Intel Corporation
[   20.108692] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC257: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   20.108712] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   20.108713] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   20.108713] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   20.108714] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   20.108714] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x19
[   20.108715] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
[   20.155414] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input19
[   20.155444] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input20
[   20.301467] iwlwifi 0000:00:14.3: Found debug destination: EXTERNAL_DRAM


!!Packages installed
!!--------------------

ii  alsa-topology-conf                                          1.2.2-1                                                     all          ALSA topology configuration files
ii  alsa-ucm-conf                                               1.2.2-1ubuntu0.5                                            all          ALSA Use Case Manager configuration files
ii  alsa-utils                                                  1.2.2-1ubuntu2                                              amd64        Utilities for configuring and using ALSA

```

---

### Post by CelticWarrior on 2020-12-10
Have you installed Nvidia drivers? Which version?

---

### Post by midnightferret on 2020-12-10
I am using the "NVIDIA driver metapackage from nvidia-driver-450 (proprietary)" 

[IMG]https://ibb.co/yRbmQ4N[/IMG][https://ibb.co/yRbmQ4N]("https://ibb.co/yRbmQ4N")

---

### Post by CelticWarrior on 2020-12-10
So likely that is the problem.
[https://www.nvidia.com/Download/driverResults.aspx/146629/en-us](https://www.nvidia.com/Download/driverResults.aspx/146629/en-us)

As you can see Nvidia recommends 430 for your card.

---

### Post by midnightferret on 2020-12-11
Thank you for your reply. I am trying this version of the driver, but as it was not available in the autoinstall, I downloaded it and attempted to install it. I managed to disable the GUI and unload the  nvidia-drm and start the install, but at the end it threw an error that the "binary package for nvidia 430.09 not found" and "Bad return status for module build on kernel: 5.4.0-56 generic(x86_64)"

I'm looking for guides on resolving this - so that's why I haven't reported back on whether it works. Thanks!

---

### Post by Yellow Pasque on 2020-12-11
> **CelticWarrior said:**
> As you can see Nvidia recommends 430 for your card.

That is weird. Why would Nvidia recommend 430 when similar cards and older generations of hardware are supported? Check the PCI ID of the card against:
[https://download.nvidia.com/XFree86/Linux-x86_64/455.45.01/README/supportedchips.html](https://download.nvidia.com/XFree86/Linux-x86_64/455.45.01/README/supportedchips.html)

---

### Post by midnightferret on 2020-12-12
> **Yellow Pasque said:**
> That is weird. Why would Nvidia recommend 430 when similar cards and older generations of hardware are supported? Check the PCI ID of the card against:
[https://download.nvidia.com/XFree86/Linux-x86_64/455.45.01/README/supportedchips.html](https://download.nvidia.com/XFree86/Linux-x86_64/455.45.01/README/supportedchips.html)

Hi,thank you for the reply - according to this info, PCI ID 2191 is supported by the 455 driver. However, changing to this driver does not enable the monitor DP to show up as an output device in sound settings. Should I keep trying to install the 430 version?

---

