---
title: "Pulseaudio oddities (sorta long)"
date: 2010-04-28
forum: Multimedia Software
---

### Post by aceracer24 on 2010-04-28
Ok I will try to be as brief but specific as I can. 

Fresh install of Ubuntu 9.10 (or lucid for that matter). I am using the optical out from my sound card(listed below)so this is an SPDIF out to a Sony home stereo. 

I want 5.1 surround for ALL audio be it MP3s, DVDs or system sound. This part I know has been discussed extensively but isn't the main reason for this topic. I only include it to set up the oddities. So with that said, I have changed and or updated every file/setting known to man to accomplish this with no luck at all. Now on to the oddities...

When I have pulseaudio set to Analog 5.1 I get basic stereo sound from the right and left front speakers. If I set it to one of or any of the 3 digital settings be it duplex or stereo, the subwoofer starts to work and I get sound from only one front speaker (front or left..random). Change it back to Analog and then back to digital and the sound from the front speaker (left or right side..random)will change to the other front speaker. If I use the pulseaudio application that shows the individual channels for a 5.1 system, all channels are moving to the beat of the music but the actual sound, again, is only coming from the subwoofer and one of the front speakers. Changing back to analaog removes the subwooofer but pumps sound to both front speakers again but the application for the channels still shows all channels recieving sound. 

Install Kubuntu (Kubuntu-desktop on Ubuntu system) and now you have access to Kubuntu's sound properties by going to system/preferences/system settings/multimedia (I think this is it. Going by memory since I am at work). Here I have a large selection of audio profiles. One of these is another digital profile. If I select it and test it, the subwoofer will work again and the test tones will play properly through both front speakers. However if I set this same profile to preferred and restart the system, the woofer will still work but now the sound is only going through one of the front speakers agian. 

I have tried every configuration I can find and nothing seems to work right. I wanted 5.1 for all sound but I would be just peachy if I could get stereo with sub working but for some reason, only a test works and actually selecting that profile doesn't. This is very frustrating.

---

### Post by aceracer24 on 2010-04-28
OK...no comments/explinations or some help understanding why it seems to work but not?

---

### Post by aceracer24 on 2010-04-29
Wow, is this normal behavior then for pulseaudio?

---

### Post by lidex on 2010-04-29
Have a look here:
[http://ubuntuforums.org/showthread.php?t=877811]("http://ubuntuforums.org/showthread.php?t=877811")

---

### Post by aceracer24 on 2010-04-29
> **lidex said:**
> Have a look here:
[http://ubuntuforums.org/showthread.php?t=877811]("http://ubuntuforums.org/showthread.php?t=877811")

Hey lidex, thank you for the link. I will give it a try and see how well it works.

---

### Post by aceracer24 on 2010-04-30
Well I followed the link and I followed the directions. WHat I ended up with was basically the same outcome as before. When the digital is being used, the sub works but only one of the front speakers gets sound. So any more info/help would be appreciated.

---

### Post by lidex on 2010-04-30
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by aceracer24 on 2010-05-01
Here you go. FYI, I am having a new problem now since installing Lucid a second time. But aside from the install, no hardware had changed.

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat May  1 04:31:16 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


!!DMI Information
!!---------------

Manufacturer:       
Product Name:       


!!Kernel Information
!!------------------

Kernel release:    2.6.32-21-generic
Operating System:  GNU/Linux
Architecture:      x86_64
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
snd_ctxfi


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

 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfd8fc000 irq 19
 1 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K1 SB073x


!!PCI Soundcards installed in the system
!!--------------------------------------

01:07.0 Multimedia audio controller: Creative Labs SB X-Fi
05:00.1 Audio device: ATI Technologies Inc HD48x0 audio


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

01:07.0 0401: 1102:0005
	Subsystem: 1102:0031
--
05:00.1 0403: 1002:aa30
	Subsystem: 1002:aa30


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
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
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

!!Module: snd_ctxfi
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	multiple : 2
	reference_rate : 48000
	use_system_timer : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
Function Id: 0x1
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Converter: stream=0, channel=0
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

crw-rw----+ 1 root audio 116, 13 Apr 30 22:17 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 10 Apr 30 22:17 /dev/snd/controlC1
crw-rw----+ 1 root audio 116, 12 Apr 30 22:17 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 11 Apr 30 22:31 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  9 Apr 30 22:31 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  8 Apr 30 22:31 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116,  7 Apr 30 22:17 /dev/snd/pcmC1D1p
crw-rw----+ 1 root audio 116,  6 Apr 30 22:17 /dev/snd/pcmC1D2p
crw-rw----+ 1 root audio 116,  5 Apr 30 22:17 /dev/snd/pcmC1D3p
crw-rw----+ 1 root audio 116,  4 Apr 30 22:31 /dev/snd/pcmC1D4p
crw-rw----+ 1 root audio 116,  3 Apr 30 22:17 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Apr 30 22:17 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Apr 30 22:17 .
drwxr-xr-x 3 root root 300 Apr 30 22:17 ..
lrwxrwxrwx 1 root root  12 Apr 30 22:17 pci-0000:01:07.0 -> ../controlC1
lrwxrwxrwx 1 root root  12 Apr 30 22:17 pci-0000:05:00.1 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

Home directory /home/david not ours.
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

ARECORD

Home directory /home/david not ours.
**** List of CAPTURE Hardware Devices ****
card 1: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [HDMI]

Card hw:0 'HDMI'/'HDA ATI HDMI at 0xfd8fc000 irq 19'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100100'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [XFi]

Card hw:1 'XFi'/'Creative X-Fi 20K1 SB073x'
  Mixer name	: '20K1'
  Components	: ''
  Controls      : 29
  Simple ctrls  : 10
Simple mixer control 'Master',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB]
  Front Right: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB]
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [on]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Center/LFE',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Line-in',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume cvolume cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
Simple mixer control 'S/PDIF-in',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
Simple mixer control 'S/PDIF-out',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]


!!Alsactl output
!!-------------

--startcollapse--
state.HDMI {
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
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
}
state.XFi {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 256
		value.1 256
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 256
		value.1 256
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Line-in Playback Volume'
		value.0 256
		value.1 256
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'S/PDIF-in Playback Volume'
		value.0 256
		value.1 256
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'S/PDIF-out Playback Volume'
		value.0 256
		value.1 256
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 256
		value.1 256
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 256
		value.1 256
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Center/LFE Playback Volume'
		value.0 256
		value.1 256
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Side Playback Volume'
		value.0 256
		value.1 256
	}
	control.11 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Master Capture Volume'
		value.0 256
		value.1 256
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'PCM Capture Volume'
		value.0 256
		value.1 256
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Line-in Capture Volume'
		value.0 256
		value.1 256
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Mic Capture Volume'
		value.0 0
		value.1 0
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 256'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'S/PDIF-in Capture Volume'
		value.0 256
		value.1 256
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Capture Switch'
		value true
	}
	control.17 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line-in Capture Switch'
		value true
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Capture Switch'
		value false
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'S/PDIF-in Capture Switch'
		value true
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line-in Playback Switch'
		value false
	}
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'S/PDIF-out Playback Switch'
		value true
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'S/PDIF-in Playback Switch'
		value false
	}
	control.23 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Front Playback Switch'
		value true
	}
	control.24 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Surround Playback Switch'
		value true
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center/LFE Playback Switch'
		value true
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Side Playback Switch'
		value true
	}
	control.27 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		device 4
		name 'IEC958 Playback Mask'
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.28 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		device 4
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.29 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		device 4
		name 'IEC958 Playback PCM Stream'
		value '0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_utf8
udf
crc_itu_t
cryptd
aes_x86_64
aes_generic
ipt_MASQUERADE
xt_state
ipt_REJECT
xt_tcpudp
iptable_filter
nf_nat_h323
nf_conntrack_h323
nf_nat_pptp
nf_conntrack_pptp
nf_conntrack_proto_gre
nf_nat_proto_gre
nf_nat_tftp
nf_conntrack_tftp
nf_nat_sip
nf_conntrack_sip
nf_nat_irc
nf_conntrack_irc
nf_nat_ftp
nf_conntrack_ftp
iptable_nat
nf_nat
nf_conntrack_ipv4
nf_conntrack
nf_defrag_ipv4
ip_tables
x_tables
binfmt_misc
ppdev
snd_hda_codec_atihdmi
arc4
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_ctxfi
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
ath9k
snd_seq_midi_event
mac80211
ath
snd_seq
snd_timer
snd_seq_device
fbcon
tileblit
font
bitblit
softcursor
cfg80211
joydev
led_class
psmouse
serio_raw
snd
fglrx
vga16fb
vgastate
k8temp
edac_core
edac_mce_amd
soundcore
snd_page_alloc
lp
parport
i2c_nforce2
usbhid
hid
usb_storage
pata_amd
forcedeth
sata_nv


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   14.225843]   alloc kstat_irqs on node 0
[   14.225850] HDA Intel 0000:05:00.1: PCI INT B -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[   14.225873] HDA Intel 0000:05:00.1: setting latency timer to 64
[   14.226633] ath: EEPROM regdomain: 0x10
--
[   16.205323] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   20.595130] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   22.815140] wlan0: deauthenticating from 00:1c:f0:6a:aa:00 by local choice (reason=3)


```

---

### Post by aceracer24 on 2010-05-05
I have been patiently waiting for further assistance on this. This problem is making it very difficult to accept Linux as my main OS. 

Along with this odd problem with sound only working from one speaker at a time, I am also having a ton of distorted sounds. Like it is over amplified but lowering volumes doesn't work.

---

### Post by lidex on 2010-05-05
Sorry, got called out of town unexpectedly for two days. Creative X-fi? Awesome. Are you using onboard sound? How about disabling it?

---

### Post by aceracer24 on 2010-05-05
It has onboard sound but it is already disabled. The HDMI is coming from the ATI 4870 card. Although I have no HDMI output slot, I assume it can do HDMI over DVI. Anyway, yep, X-Fi Xtremegamer.

---

### Post by aceracer24 on 2010-05-06
Soooo.. any suggestions?

---

### Post by lidex on 2010-05-06
OK. Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

---

