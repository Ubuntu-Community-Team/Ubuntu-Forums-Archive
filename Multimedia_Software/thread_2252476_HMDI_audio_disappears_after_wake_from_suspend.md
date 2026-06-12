---
title: "HMDI audio disappears after wake from suspend ?"
date: 2014-11-12
forum: Multimedia Software
---

### Post by dave153 on 2014-11-12
Have found my way here many times to solve various issues but this time have not had as much luck so first time poster. 

I have an ION330 machine as a MythTV/XBMC frontend running 12.04.5 LTS which is configured to use suspend to RAM when inactive. It is connected to an A/V Receiver via HDMI which does switching to the TV. On wake, the machine relaunches XBMC and never had an issue before. 

I wanted to upgrade to XBMC 13.x for a reason which eludes me now and both kernel and Nvidia packages were upgraded as I went from 12.04.01? (At least I think it was). In any case after the upgrade I noticed that when the machine woke from suspend, HDMI audio was not functioning or available. The audio devices in XBMC no longer listed HDMI, only the Optical and Analog devices. Switching to mythtvfrontend also resulted in no sound (A/V Receiver indicated no signal) so I assumed not application specific. I suspected maybe faulty HDMI cable or TV/Receiver impacting the handshake process. However ensuring TV and Receiver are on well before wake along with swapping cables showed no improvement.

What is odd, is that if I immediately suspend and then wake the machine again, HDMI audio returns. In between doing this, the state of aplay -l changes only slightly with respect to the HDMI subdevice but not sure what that means?

# first wake 
```
root@lounge:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

# second suspend/resume
```
root@lounge:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1        
  Subdevice #0: subdevice #0

```

Last known good state that I can recall was kernel 3.2.0-32, XBMC 12.x but unsure of the Nvidia drivers at the time (I assume they could impact HDMI Audio?). I am currently on 3.2.0-70 and tried 3.2.0-69 before that.
Output of alsa-info.sh below on first wake. I ran through the troubleshooting wiki page and the only thing I noted was a difference in ALSA versions but re-installing as per the wiki did not correct it. 

Is anyone able to offer any insight on how to resolve this minor inconvenience? Any help would be much appreciated.


```
root@lounge:~# bash alsa-info.sh --stdout


upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################


!!Script ran on: Wed Nov 12 11:26:21 UTC 2014




!!Linux Distribution
!!------------------


Ubuntu 12.04.5 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04.5 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu precise (12.04.5 LTS)"




!!DMI Information
!!---------------


Manufacturer:      To Be Filled By O.E.M.
Product Name:      To Be Filled By O.E.M.
Product Version:   To Be Filled By O.E.M.
Firmware Version:  P1.60




!!Kernel Information
!!------------------


Kernel release:    3.2.0-70-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     1.0.24
Library version:    1.0.25
Utilities version:  1.0.25




!!Loaded ALSA modules
!!-------------------


snd_hda_intel




!!Sound Servers on this system
!!----------------------------


No sound servers found.




!!Soundcards recognised by ALSA
!!-----------------------------


 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfae78000 irq 21




!!PCI Soundcards installed in the system
!!--------------------------------------


00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


00:08.0 0403: 10de:0ac0 (rev b1)
        Subsystem: 1849:0397




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




!!Loaded sound module options
!!---------------------------


!!Module: snd_hda_intel
        align_buffer_size : Y
        bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
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
        snoop : Y




!!HDA-Intel Codec information
!!---------------------------
--startcollapse--


Codec: VIA VT1708S
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x11060397
Subsystem Id: 0x18490397
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=1, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x10 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="VT1708S Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x2a 0x2a]
  Converter: stream=7, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x2a 0x2a]
  Converter: stream=7, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="VT1708S Digital", type="SPDIF", device=1
  Converter: stream=7, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x13 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="VT1708S Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x17
Node 0x14 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x1e
Node 0x15 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x16 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Control: name="PCM Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="PCM Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=3, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=3, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x0e 0x0e] [0x80 0x80] [0x97 0x97] [0x97 0x97] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 7
     0x10 0x1f 0x1a 0x1b 0x1e 0x1d 0x25
Node 0x17 [Audio Selector] wcaps 0x300501: Stereo
  Control: name="Input Source", index=0, device=0
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 6
     0x1f 0x1a* 0x1b 0x1e 0x1d 0x16
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x11
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410110f2: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x2
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x18
Node 0x1a [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Jack", index=0, device=0
  Pincap 0x00002334: IN OUT Detect
    Vref caps: HIZ 50 100
  Pin Default 0x01a19036: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x6
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x26
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Line Jack", index=0, device=0
  Pincap 0x00002334: IN OUT Detect
    Vref caps: HIZ 50 100
  Pin Default 0x0181303e: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x3, Sequence = 0xe
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=03, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x18
Node 0x1c [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Line-Out Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x16
Node 0x1d [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000233c: IN OUT HP Detect
    Vref caps: HIZ 50 100
  Pin Default 0x422140f0: [N/A] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 2
     0x16* 0x25
Node 0x1e [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000233c: IN OUT HP Detect
    Vref caps: HIZ 50 100
  Pin Default 0x42a190f8: [N/A] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0xf, Sequence = 0x8
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 2
     0x16* 0x25
Node 0x1f [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x503701f7: [N/A] CD at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x7
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x20 [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x074511f0: [Jack] SPDIF Out at Ext Rear Panel
    Conn = Optical, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x474411f0: [N/A] SPDIF Out at Ext Rear Panel
    Conn = RCA, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x15
Node 0x22 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410160f1: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0xf, Sequence = 0x1
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x26
Node 0x23 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410120f4: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0xf, Sequence = 0x4
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x27
Node 0x24 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x2a 0x2a]
  Converter: stream=7, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
Node 0x25 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x2a 0x2a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x26 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x24
Node 0x27 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x25
Codec: Nvidia MCP79/7A HDMI
Address: 3
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de0007
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
Node 0x04 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x18560110: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x07 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560121: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x08 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x09 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560122: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x2
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x08
Node 0x0a [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0b [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560123: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x3
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0a
Node 0x0c [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0d [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560124: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x4
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0c
--endcollapse--




!!ALSA Device nodes
!!-----------------


crw-rw---T 1 root audio 116,  8 Nov  3 20:35 /dev/snd/controlC0
crw-rw---T 1 root audio 116,  7 Nov  3 20:35 /dev/snd/hwC0D0
crw-rw---T 1 root audio 116,  6 Nov  3 20:35 /dev/snd/hwC0D3
crw-rw---T 1 root audio 116,  5 Nov  3 20:35 /dev/snd/pcmC0D0c
crw-rw---T 1 root audio 116,  4 Nov 12 22:24 /dev/snd/pcmC0D0p
crw-rw---T 1 root audio 116,  3 Nov  3 20:35 /dev/snd/pcmC0D1p
crw-rw---T 1 root audio 116,  2 Nov 12 22:24 /dev/snd/pcmC0D3p
crw-rw---T 1 root audio 116,  1 Nov  3 20:35 /dev/snd/seq
crw-rw---T 1 root audio 116, 33 Nov  3 20:35 /dev/snd/timer


/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Nov  3 20:35 .
drwxr-xr-x 3 root root 240 Nov  3 20:35 ..
lrwxrwxrwx 1 root root  12 Nov  3 20:35 pci-0000:00:08.0 -> ../controlC0




!!Aplay/Arecord output
!!--------------------


APLAY


**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ARECORD


**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1


!!Amixer output
!!-------------


!!-------Mixer controls for card 0 [NVidia]


Card hw:0 'NVidia'/'HDA NVidia at 0xfae78000 irq 21'
  Mixer name    : 'Nvidia MCP79/7A HDMI'
  Components    : 'HDA:11060397,18490397,00100000 HDA:10de0007,10de0101,00100100'
  Controls      : 36
  Simple ctrls  : 17
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 42
  Mono: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 14 [45%] [-13.50dB] [on]
  Front Right: Playback 14 [45%] [-13.50dB] [on]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 42 [100%] [0.00dB] [on]
  Front Right: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 42 [100%] [0.00dB] [on]
  Front Right: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 42
  Mono: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 42
  Mono: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Dynamic Power-Control',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Line' 'Stereo Mixer'
  Item0: 'Mic'
Simple mixer control 'Smart 5.1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]




!!Alsactl output
!!--------------


--startcollapse--
state.NVidia {
        control.1 {
                iface MIXER
                name 'Front Playback Volume'
                value.0 42
                value.1 42
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 42'
                        dbmin -6300
                        dbmax 0
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
        control.2 {
                iface MIXER
                name 'Front Playback Switch'
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
                name 'Surround Playback Volume'
                value.0 42
                value.1 42
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 42'
                        dbmin -6300
                        dbmax 0
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
        control.4 {
                iface MIXER
                name 'Surround Playback Switch'
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
                name 'Center Playback Volume'
                value 42
                comment {
                        access 'read write'
                        type INTEGER
                        count 1
                        range '0 - 42'
                        dbmin -6300
                        dbmax 0
                        dbvalue.0 0
                }
        }
        control.6 {
                iface MIXER
                name 'Center Playback Switch'
                value true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 1
                }
        }
        control.7 {
                iface MIXER
                name 'LFE Playback Volume'
                value 42
                comment {
                        access 'read write'
                        type INTEGER
                        count 1
                        range '0 - 42'
                        dbmin -6300
                        dbmax 0
                        dbvalue.0 0
                }
        }
        control.8 {
                iface MIXER
                name 'LFE Playback Switch'
                value true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 1
                }
        }
        control.9 {
                iface MIXER
                name 'PCM Playback Volume'
                value.0 14
                value.1 14
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 31'
                        dbmin -3450
                        dbmax 1200
                        dbvalue.0 -1350
                        dbvalue.1 -1350
                }
        }
        control.10 {
                iface MIXER
                name 'PCM Playback Switch'
                value.0 true
                value.1 true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.11 {
                iface MIXER
                name 'Capture Volume'
                value.0 0
                value.1 0
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 31'
                        dbmin -1650
                        dbmax 3000
                        dbvalue.0 -1650
                        dbvalue.1 -1650
                }
        }
        control.12 {
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
        control.13 {
                iface MIXER
                name 'Capture Volume'
                index 1
                value.0 0
                value.1 0
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 31'
                        dbmin -1650
                        dbmax 3000
                        dbvalue.0 -1650
                        dbvalue.1 -1650
                }
        }
        control.14 {
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
        control.15 {
                iface MIXER
                name 'Input Source'
                value Mic
                comment {
                        access 'read write'
                        type ENUMERATED
                        count 1
                        item.0 Mic
                        item.1 Line
                        item.2 'Stereo Mixer'
                }
        }
        control.16 {
                iface MIXER
                name 'Mic Playback Volume'
                value.0 23
                value.1 23
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 31'
                        dbmin -3450
                        dbmax 1200
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
        control.17 {
                iface MIXER
                name 'Mic Playback Switch'
                value.0 false
                value.1 false
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.18 {
                iface MIXER
                name 'Line Playback Volume'
                value.0 23
                value.1 23
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 31'
                        dbmin -3450
                        dbmax 1200
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
        control.19 {
                iface MIXER
                name 'Line Playback Switch'
                value.0 false
                value.1 false
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.20 {
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
                        dbmax 3075
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
        control.21 {
                iface MIXER
                name 'Smart 5.1'
                value false
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 1
                }
        }
        control.22 {
                iface MIXER
                name 'Dynamic Power-Control'
                value Disabled
                comment {
                        access 'read write'
                        type ENUMERATED
                        count 1
                        item.0 Disabled
                        item.1 Enabled
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
                value '0482000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
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
                value 42
                comment {
                        access 'read write'
                        type INTEGER
                        count 1
                        range '0 - 42'
                        dbmin -6300
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
                iface CARD
                name 'Line-Out Jack'
                value false
                comment {
                        access read
                        type BOOLEAN
                        count 1
                }
        }
        control.31 {
                iface CARD
                name 'Mic Jack'
                value false
                comment {
                        access read
                        type BOOLEAN
                        count 1
                }
        }
        control.32 {
                iface CARD
                name 'Line Jack'
                value false
                comment {
                        access read
                        type BOOLEAN
                        count 1
                }
        }
        control.33 {
                iface MIXER
                name 'IEC958 Playback Con Mask'
                index 1
                value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
                comment {
                        access read
                        type IEC958
                        count 1
                }
        }
        control.34 {
                iface MIXER
                name 'IEC958 Playback Pro Mask'
                index 1
                value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
                comment {
                        access read
                        type IEC958
                        count 1
                }
        }
        control.35 {
                iface MIXER
                name 'IEC958 Playback Default'
                index 1
                value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
                comment {
                        access 'read write'
                        type IEC958
                        count 1
                }
        }
        control.36 {
                iface MIXER
                name 'IEC958 Playback Switch'
                index 1
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
rfcomm
bluetooth
nvidia
snd_hda_codec_hdmi
ir_lirc_codec
lirc_dev
snd_hda_codec_via
ir_mce_kbd_decoder
ir_sony_decoder
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
ir_jvc_decoder
snd_rawmidi
snd_seq_midi_event
ir_rc6_decoder
snd_seq
ir_rc5_decoder
ir_nec_decoder
snd_timer
psmouse
snd_seq_device
rc_rc6_mce
mceusb
joydev
serio_raw
rc_core
i2c_nforce2
snd
shpchp
usbhid
soundcore
hid
snd_page_alloc
mac_hid
wmi
lp
parport
nfsd
nfs
lockd
fscache
auth_rpcgss
nfs_acl
sunrpc
forcedeth




!!Sysfs Files
!!-----------


/sys/class/sound/hwC0D0/init_pin_configs:
0x19 0x410110f2
0x1a 0x01a19036
0x1b 0x0181303e
0x1c 0x01014010
0x1d 0x422140f0
0x1e 0x42a190f8
0x1f 0x503701f7
0x20 0x074511f0
0x21 0x474411f0
0x22 0x410160f1
0x23 0x410120f4


/sys/class/sound/hwC0D0/driver_pin_configs:


/sys/class/sound/hwC0D0/user_pin_configs:


/sys/class/sound/hwC0D0/init_verbs:


/sys/class/sound/hwC0D0/hints:


/sys/class/sound/hwC0D3/init_pin_configs:
0x05 0x18560110
0x07 0x58560121
0x09 0x58560122
0x0b 0x58560123
0x0d 0x58560124


/sys/class/sound/hwC0D3/driver_pin_configs:


/sys/class/sound/hwC0D3/user_pin_configs:


/sys/class/sound/hwC0D3/init_verbs:


/sys/class/sound/hwC0D3/hints:




!!ALSA/HDA dmesg
!!--------------


[   11.943357] IR JVC protocol handler initialized
[   12.238734] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[   12.238756] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[   12.239605] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   12.239941] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   12.239957] hda_intel: Disabling MSI
[   12.240091] snd_hda_intel 0000:00:08.0: setting latency timer to 64
[   12.456811] IR Sony protocol handler initialized
--
[   13.239117] IR LIRC bridge handler initialized
[   13.776351] input: HDA NVidia Line as /devices/pci0000:00/0000:00:08.0/sound/card0/input6
[   13.776741] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:08.0/sound/card0/input7
[   13.777101] input: HDA NVidia Line-Out as /devices/pci0000:00/0000:00:08.0/sound/card0/input8
[   13.832622] nvidia: module license 'NVIDIA' taints kernel.
--
[10463.380493] sd 0:0:0:0: [sda] Stopping disk
[10463.444059] snd_hda_intel 0000:00:08.0: PCI INT A disabled
[10463.460244] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D3
[10463.460256] PM: suspend of drv:snd_hda_intel dev:0000:00:08.0 complete after 261.839 msecs
[10463.998782] PM: suspend of drv:sd dev:0:0:0:0 complete after 801.537 msecs
--
[10464.338598] ehci_hcd 0000:00:04.1: PME# disabled
[10464.338630] snd_hda_intel 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[10464.338698] forcedeth 0000:00:0a.0: restoring config space at offset 0x7 (was 0x0, writing 0xfae7e400)
--
[10464.340003] ehci_hcd 0000:00:04.1: setting latency timer to 64
[10464.340133] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10464.340152] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10464.340197] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10464.340244] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10464.340291] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[10464.340421] snd_hda_intel 0000:00:08.0: setting latency timer to 64
[10464.340440] pci 0000:00:09.0: setting latency timer to 64
--
[10503.856308] sd 0:0:0:0: [sda] Stopping disk
[10504.012091] snd_hda_intel 0000:00:08.0: PCI INT A disabled
[10504.028175] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D3
[10504.028189] PM: suspend of drv:snd_hda_intel dev:0000:00:08.0 complete after 244.267 msecs
[10504.474990] PM: suspend of drv:sd dev:0:0:0:0 complete after 693.838 msecs
--
[10504.794648] ehci_hcd 0000:00:04.1: PME# disabled
[10504.794680] snd_hda_intel 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[10504.794747] forcedeth 0000:00:0a.0: restoring config space at offset 0x7 (was 0x0, writing 0xfae7e400)
--
[10504.796305] pci 0000:00:09.0: setting latency timer to 64
[10504.796353] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10504.796410] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10504.796487] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10504.796568] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10504.796588] pci 0000:00:10.0: setting latency timer to 64
[10504.796594] ahci 0000:00:0b.0: setting latency timer to 64
[10504.796614] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[10504.796644] snd_hda_intel 0000:00:08.0: setting latency timer to 64
[10504.798127] sd 0:0:0:0: [sda] Starting disk
--
[10605.896062] ehci_hcd 0000:00:04.1: PCI INT B disabled
[10606.060081] snd_hda_intel 0000:00:08.0: PCI INT A disabled
[10606.076165] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D3
[10606.076179] PM: suspend of drv:snd_hda_intel dev:0000:00:08.0 complete after 244.461 msecs
[10606.463503] PM: suspend of drv:sd dev:0:0:0:0 complete after 634.364 msecs
--
[10606.786785] ehci_hcd 0000:00:04.1: PME# disabled
[10606.786816] snd_hda_intel 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[10606.786884] forcedeth 0000:00:0a.0: restoring config space at offset 0x7 (was 0x0, writing 0xfae7e400)
--
[10606.789088] ahci 0000:00:0b.0: setting latency timer to 64
[10606.789460] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10606.789481] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10606.789500] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10606.789514] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10606.789539] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[10606.789557] snd_hda_intel 0000:00:08.0: setting latency timer to 64
[10606.789704] sd 0:0:0:0: [sda] Starting disk
--
[10636.032075] ehci_hcd 0000:00:04.1: PCI INT B disabled
[10636.196079] snd_hda_intel 0000:00:08.0: PCI INT A disabled
[10636.212166] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D3
[10636.212179] PM: suspend of drv:snd_hda_intel dev:0000:00:08.0 complete after 245.273 msecs
[10636.279716] sd 0:0:0:0: [sda] Stopping disk
--
[10637.218834] ehci_hcd 0000:00:04.1: PME# disabled
[10637.218866] snd_hda_intel 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[10637.218934] forcedeth 0000:00:0a.0: restoring config space at offset 0x7 (was 0x0, writing 0xfae7e400)
--
[10637.220409] pci 0000:00:09.0: setting latency timer to 64
[10637.220420] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10637.220442] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10637.220578] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10637.220619] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10637.220716] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[10637.220733] ahci 0000:00:0b.0: setting latency timer to 64
[10637.220749] snd_hda_intel 0000:00:08.0: setting latency timer to 64
[10637.220823] pci 0000:00:10.0: setting latency timer to 64
--
[10768.392060] ehci_hcd 0000:00:04.1: PCI INT B disabled
[10768.556076] snd_hda_intel 0000:00:08.0: PCI INT A disabled
[10768.572161] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D3
[10768.572175] PM: suspend of drv:snd_hda_intel dev:0000:00:08.0 complete after 245.117 msecs
[10768.988678] PM: suspend of drv:sd dev:0:0:0:0 complete after 663.522 msecs
--
[10769.310831] ehci_hcd 0000:00:04.1: PME# disabled
[10769.310863] snd_hda_intel 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[10769.310931] forcedeth 0000:00:0a.0: restoring config space at offset 0x7 (was 0x0, writing 0xfae7e400)
--
[10769.313733] ahci 0000:00:0b.0: setting latency timer to 64
[10769.314380] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10769.314415] sd 0:0:0:0: [sda] Starting disk
[10769.314618] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10769.314773] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10769.314873] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[10769.314897] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[10769.314928] snd_hda_intel 0000:00:08.0: setting latency timer to 64
[10769.377972] forcedeth 0000:00:0a.0: eth0: no link during initialization
--
[16651.401201] sd 0:0:0:0: [sda] Stopping disk
[16651.452077] snd_hda_intel 0000:00:08.0: PCI INT A disabled
[16651.468161] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D3
[16651.468174] PM: suspend of drv:snd_hda_intel dev:0000:00:08.0 complete after 245.520 msecs
[16652.019027] PM: suspend of drv:sd dev:0:0:0:0 complete after 801.668 msecs
--
[16652.338670] ehci_hcd 0000:00:04.1: PME# disabled
[16652.338702] snd_hda_intel 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[16652.338769] forcedeth 0000:00:0a.0: restoring config space at offset 0x7 (was 0x0, writing 0xfae7e400)
--
[16652.341017] ahci 0000:00:0b.0: setting latency timer to 64
[16652.341269] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[16652.341291] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[16652.341310] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[16652.341326] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[16652.341350] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[16652.341381] snd_hda_intel 0000:00:08.0: setting latency timer to 64
[16652.341519] sd 0:0:0:0: [sda] Starting disk
--
[16808.728060] ehci_hcd 0000:00:04.1: PCI INT B disabled
[16808.892098] snd_hda_intel 0000:00:08.0: PCI INT A disabled
[16808.908163] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D3
[16808.908176] PM: suspend of drv:snd_hda_intel dev:0000:00:08.0 complete after 244.993 msecs
[16809.298244] PM: suspend of drv:sd dev:0:0:0:0 complete after 637.141 msecs
--
[16809.618904] ehci_hcd 0000:00:04.1: PME# disabled
[16809.618936] snd_hda_intel 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[16809.619004] forcedeth 0000:00:0a.0: restoring config space at offset 0x7 (was 0x0, writing 0xfae7e400)
--
[16809.620493] pci 0000:00:09.0: setting latency timer to 64
[16809.620587] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[16809.620622] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[16809.620662] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[16809.620695] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[16809.620770] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[16809.620794] snd_hda_intel 0000:00:08.0: setting latency timer to 64
[16809.620840] ahci 0000:00:0b.0: setting latency timer to 64
--
[44954.896072] ehci_hcd 0000:00:04.1: PCI INT B disabled
[44955.064079] snd_hda_intel 0000:00:08.0: PCI INT A disabled
[44955.080161] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D3
[44955.080174] PM: suspend of drv:snd_hda_intel dev:0000:00:08.0 complete after 247.481 msecs
[44955.500184] PM: suspend of drv:sd dev:0:0:0:0 complete after 670.839 msecs
--
[44955.822808] ehci_hcd 0000:00:04.1: PME# disabled
[44955.822840] snd_hda_intel 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[44955.822908] forcedeth 0000:00:0a.0: restoring config space at offset 0x7 (was 0x0, writing 0xfae7e400)
--
[44955.824325] pci 0000:00:09.0: setting latency timer to 64
[44955.824366] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[44955.824405] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[44955.824489] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[44955.824546] snd_hda_intel 0000:00:08.0: power state changed by ACPI to D0
[44955.824606] pci 0000:00:10.0: setting latency timer to 64
[44955.824627] ahci 0000:00:0b.0: setting latency timer to 64
[44955.824634] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[44955.824657] snd_hda_intel 0000:00:08.0: setting latency timer to 64
[44955.825132] sd 0:0:0:0: [sda] Starting disk



```

---

