---
title: "Soundcard not working (Philips Via  Envy24GT)"
date: 2013-01-07
forum: Multimedia Software
---

### Post by arry487 on 2013-01-07
Hello,

I can't seem to get this soundcard to output any signal although it seems to be installed correctly. 

It is the Philips ultimate edge based on the Via Envy24GT. I know that this card only supports 48 or 96khz.

Is there a way to send 48 or 98khz to the card?

Thanks

---

### Post by arry487 on 2013-01-07
Some additonal info

The sound chip is listed as VT1720/24 in system settings, I am trying to use the analogue output.

When i try to play a music file in rhythmbox nothing happens.

Thanks

Arry

---

### Post by BicyclerBoy on 2013-01-07
aplay -l
aplay -L

speaker-test -l 2 -c2 -r 48000 -D hw:1,0

To setup system-wide audio for normal ubuntu apps install/use 
pavucontrol

---

### Post by arry487 on 2013-01-08
Thank you for your help. I am not very familiar with Linux/Ubuntu.

I assume I have to open a terminal using ctrl alt t.

What command would I have to type to set Pulseaudio to only send 48khz to the sound card and resample if necessary? 

Are there any options to set the quality of the interpolation?

Thanks

Arry

---

### Post by BicyclerBoy on 2013-01-08
I know you are not familiar...that why there were a couple of commands posted that provides info required..

Yes pulseaudio (& alsa) can resample at many quality levels to any samplerate.
Hi quality resampling to 96KHz/24bit can use 50% of core2duo.

I can't help with debugging by adding more layers complication/confusion.

You might not want to use pulse-audio..
What's the point hi-Q resampling system sounds & internet lo-fi videos..

---

### Post by arry487 on 2013-01-09
Sorry I was not being lazy but at that point I did not even know how to open a terminal, perhaps i could have searched more.

I used the test command you provided and still got no sound. If I try to play a file in any player the file wil not start to play at all. The soundcard works in windows.

pavucontrol is useful, it would of been nice if it was installed by default even better if you could set the sample rate and bit depth within the gui.

I am now using my crap realtek onboard audio which is a shame as the pc is used mostly for music and movies.

---

### Post by Yellow Pasque on 2013-01-09
Make sure nothing's muted and the volumes are turned up in:
```
alsamixer
```

Also, try turning the pulseaudio volume way up (assuming no one's around :P ). I've seen cases where people needed to crank the pulseaudio volume before they got sound.

---

### Post by arry487 on 2013-01-09
> Make sure nothings muted and the volumes are turned up

I have tried this and other things such as moving pci slots.

If anyone has any other suggestions I am willing to learn.

Thanks
Arry

---

### Post by Yellow Pasque on 2013-01-09
Please post alsa info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by arry487 on 2013-01-10
Here is the alsa info ;-

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.61
!!################################

!!Script ran on: Thu Jan 10 16:53:25 UTC 2013


!!Linux Distribution
!!------------------

Ubuntu 12.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu quantal (12.10)"


!!DMI Information
!!---------------

Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      GA-MA790X-UD4P
Product Version:    
Firmware Version:  F10c


!!Kernel Information
!!------------------

Kernel release:    3.5.0-21-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.25
Library version:    1.0.25
Utilities version:  1.0.25


!!Loaded ALSA modules
!!-------------------

snd_ice1724
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [ICE1724        ]: ICE1724 - ICEnsemble ICE1724
                      ICEnsemble ICE1724 at 0xcf00, irq 20
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdefc000 irq 44


!!PCI Soundcards installed in the system
!!--------------------------------------

01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV770 HDMI Audio [Radeon HD 4850/4870]
03:06.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

01:00.1 0403: 1002:aa30
	Subsystem: 1682:aa30
--
03:06.0 0401: 1412:1724 (rev 01)
	Subsystem: 17ab:1906


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

!!Module: snd_ice1724
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)

!!Module: snd_hda_intel
	align_buffer_size : -1
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

Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
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
  Converter: stream=1, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x02
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---T+ 1 root audio 116,  5 Jan 10 16:27 /dev/snd/controlC0
crw-rw---T+ 1 root audio 116,  8 Jan 10 16:27 /dev/snd/controlC1
crw-rw---T+ 1 root audio 116,  7 Jan 10 16:27 /dev/snd/hwC1D0
crw-rw---T+ 1 root audio 116,  4 Jan 10 16:27 /dev/snd/pcmC0D0c
crw-rw---T+ 1 root audio 116,  3 Jan 10 16:37 /dev/snd/pcmC0D0p
crw-rw---T+ 1 root audio 116,  2 Jan 10 16:37 /dev/snd/pcmC0D1p
crw-rw---T+ 1 root audio 116,  6 Jan 10 16:27 /dev/snd/pcmC1D3p
crw-rw---T+ 1 root audio 116,  1 Jan 10 16:27 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 Jan 10 16:27 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Jan 10 16:27 .
drwxr-xr-x 3 root root 240 Jan 10 16:27 ..
lrwxrwxrwx 1 root root  12 Jan 10 16:27 pci-0000:01:00.1 -> ../controlC1
lrwxrwxrwx 1 root root  12 Jan 10 16:27 pci-0000:03:06.0 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: ICE1724 [ICEnsemble ICE1724], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICE1724 [ICEnsemble ICE1724], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: ICE1724 [ICEnsemble ICE1724], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [ICE1724]

Card hw:0 'ICE1724'/'ICEnsemble ICE1724 at 0xcf00, irq 20'
  Mixer name	: 'ICE1724 - multitrack'
  Components	: ''
  Controls      : 11
  Simple ctrls  : 6
Simple mixer control 'IEC958',0
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',1
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'Multi Track Internal Clock',0
  Capabilities: enum
  Items: '8000' '9600' '11025' '12000' '16000' '22050' '24000' '32000' '44100' '48000' '64000' '88200' '96000'
  Item0: '44100'
Simple mixer control 'Multi Track Rate Locking',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Multi Track Rate Reset',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [HDMI]

Card hw:1 'HDMI'/'HDA ATI HDMI at 0xfdefc000 irq 44'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100100'
  Controls      : 6
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!--------------

--startcollapse--
state.ICE1724 {
	control.1 {
		iface CARD
		name 'ICE1724 EEPROM'
		value '190617ab1c01428030c1ff0000ff0000ff0000000c0d0d000c000000000000000000000000000000ff000000ff000000ff000000'
		comment {
			access read
			type BYTES
			count 52
		}
	}
	control.2 {
		iface MIXER
		name 'Multi Track Internal Clock'
		value '44100'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 '8000'
			item.1 '9600'
			item.2 '11025'
			item.3 '12000'
			item.4 '16000'
			item.5 '22050'
			item.6 '24000'
			item.7 '32000'
			item.8 '44100'
			item.9 '48000'
			item.10 '64000'
			item.11 '88200'
			item.12 '96000'
		}
	}
	control.3 {
		iface MIXER
		name 'Multi Track Rate Locking'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'Multi Track Rate Reset'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.5 {
		iface PCM
		name 'Multi Track Peak'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		value.8 0
		value.9 0
		value.10 164
		value.11 4
		value.12 0
		value.13 0
		value.14 0
		value.15 0
		value.16 0
		value.17 0
		value.18 0
		value.19 0
		value.20 0
		value.21 0
		comment {
			access read
			type INTEGER
			count 22
			range '0 - 255'
		}
	}
	control.6 {
		iface MIXER
		name 'IEC958 Playback Route'
		value 'PCM Out'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'PCM Out'
			item.1 'H/W In 0'
			item.2 'H/W In 1'
			item.3 'IEC958 In L'
			item.4 'IEC958 In R'
		}
	}
	control.7 {
		iface MIXER
		name 'IEC958 Playback Route'
		index 1
		value 'PCM Out'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'PCM Out'
			item.1 'H/W In 0'
			item.2 'H/W In 1'
			item.3 'IEC958 In L'
			item.4 'IEC958 In R'
		}
	}
	control.8 {
		iface MIXER
		name 'IEC958 Output Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.9 {
		iface PCM
		device 1
		name 'IEC958 Playback Default'
		value '0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.10 {
		iface PCM
		device 1
		name 'IEC958 Playback Con Mask'
		value '3fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.11 {
		iface PCM
		device 1
		name 'IEC958 Playback Pro Mask'
		value df00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
		comment {
			access read
			type IEC958
			count 1
		}
	}
}
state.HDMI {
	control.1 {
		iface CARD
		name 'HDMI/DP,pcm=3 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.3 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.5 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.6 {
		iface PCM
		device 3
		name ELD
		value ''
		comment {
			access read
			type BYTES
			count 0
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
bnep
rfcomm
bluetooth
parport_pc
ppdev
snd_hda_codec_hdmi
kvm
snd_ice1724
snd_hda_intel
snd_ice17xx_ak4xxx
snd_hda_codec
snd_ac97_codec
ac97_bus
snd_ak4xxx_adda
snd_hwdep
snd_ak4114
snd_pt2258
snd_i2c
snd_ak4113
snd_seq_midi
snd_rawmidi
joydev
snd_pcm
snd_seq_midi_event
serio_raw
snd_seq
snd_timer
snd_seq_device
microcode
snd
radeon
ttm
drm_kms_helper
soundcore
snd_page_alloc
drm
k10temp
i2c_algo_bit
sp5100_tco
wmi
edac_core
edac_mce_amd
mac_hid
i2c_piix4
lp
parport
hid_generic
pata_atiixp
r8169
usbhid
hid


!!Sysfs Files
!!-----------

/sys/class/sound/hwC1D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!--------------

[   14.000426] [drm] Initialized radeon 2.18.0 20080528 for 0000:01:00.0 on minor 0
[   14.000485] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
[   14.000548] snd_hda_intel 0000:01:00.1: irq 44 for MSI/MSI-X
[   14.047289] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input5
[   14.067492] init: failsafe main process (796) killed by TERM signal


Hope that helps

---

### Post by BicyclerBoy on 2013-01-11
If you have an HDMI receiver then the HDMI HDA output will be superior to the soundcard.

I avoid AMD like the plague & am guessing your h/w is supported by radeon (it is loaded on your PC)..
The foss radeon driver supports some AMD GPUs HDA but it needs a grub option.
[http://www.x.org/wiki/RadeonFeature#fnref-72849d6d6eb3927d486f50ece74a739042965a6c](http://www.x.org/wiki/RadeonFeature#fnref-72849d6d6eb3927d486f50ece74a739042965a6c)

The mobo soundcard (digital output) is probably more than a match for the soundcard.
Some do 96KHz & 192KHz/24bit stereo.

Discrete soundcards have a use for analogue output.

How are you connecting to audio output (from PC)?

---

### Post by arry487 on 2013-01-12
I am using a 2 channel analogue amp. I have disabled the AMD HDMI audio in pavucontrol. The motherboard has a realtek soundchip which works but sounds poor, the Philips has a good wolfson dac. I had disabled the realtek before posting the alsa info to avoid any conflict.

I am trying to use the Philips ultimate edge soundcard (PSC724) which uses the Envy24GT chip. Philips abandoned support even before vista launched but its works in windows using the via driver and adding the device id to the inf file.

---

### Post by BicyclerBoy on 2013-01-13
That soundcard is so special it has it's own tool
[http://alsa.opensrc.org/Envy24control](http://alsa.opensrc.org/Envy24control)

Some of these examples are old but prob still good.
[http://alsa.opensrc.org/1712_.asoundrc](http://alsa.opensrc.org/1712_.asoundrc)

---

### Post by Yellow Pasque on 2013-01-14
^Those links are for ice1712 cards, while the OP's card is ice1724.

> I know that this card only supports 48 or 96khz.
I have a card (M-Audio Revolution 5.1) with the same Envy24GT chip and it can play 44.1kHz without resampling. Nevertheless, if you want to force 48kHz, the setting is in daemon.conf (remove the leading ';' to uncomment the line). Then, you have to restart pulseaudio:
```
pulseaudio -k
```

My next suggestion would be to try a Lubuntu LiveUSB (or CD-RW) since it doesn't use pulseaudio at all.

---

### Post by BicyclerBoy on 2013-01-14
Sorry for getting the OPs hopes up..

---

