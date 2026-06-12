---
title: "CMI8788 [Oxygen HD Audio] Asus Xonar alsa ubuntu 12"
date: 2013-02-23
forum: Multimedia Software
---

### Post by golfcaddy on 2013-02-23
Hi all,

Im trying to get Alsa, and therefore pulseaudio to pick up my Asus Xonar card. It currently only only recognises my nvidia sound.

First output:

```
sudo lspci | grep Audio
01:00.1 Audio device: NVIDIA Corporation GF110 High Definition Audio Controller (rev a1)
09:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]

```

So as far as my naive kernel understanding goes the correct modules are loaded:

```
lsmod | grep snd_oxygen
snd_oxygen             20949  0 
snd_oxygen_lib         41274  1 snd_oxygen
snd_mpu401_uart        14170  1 snd_oxygen_lib
snd_pcm                96668  4 snd_oxygen_lib,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd                    78921  16 snd_oxygen,snd_oxygen_lib,snd_mpu401_uart,snd_seq,snd_rawmidi,snd_seq_device,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer

``` 

The kernnel module in question:

```
sudo modinfo snd-oxygen
filename:       /lib/modules/3.5.0-25-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
license:        GPL v2
description:    C-Media CMI8788 driver
author:         Clemens Ladisch <clemens@ladisch.de>
srcversion:     30EC2B98D94E53E6DA0B399
alias:          pci:v000013F6d00008788sv00007284sd00009781bc*sc*i*
alias:          pci:v000013F6d00008788sv00007284sd00009761bc*sc*i*
alias:          pci:v000013F6d00008788sv00005431sd0000017Abc*sc*i*
alias:          pci:v000013F6d00008788sv0000415Asd00005431bc*sc*i*
alias:          pci:v000013F6d00008788sv000014C3sd00001711bc*sc*i*
alias:          pci:v000013F6d00008788sv000014C3sd00001710bc*sc*i*
alias:          pci:v000013F6d00008788sv000013F6sd0000FFFFbc*sc*i*
alias:          pci:v000013F6d00008788sv000013F6sd00008782bc*sc*i*
alias:          pci:v000013F6d00008788sv00001043sd00008521bc*sc*i*
alias:          pci:v000013F6d00008788sv00001043sd00008467bc*sc*i*
alias:          pci:v000013F6d00008788sv00001A58sd00000910bc*sc*i*
alias:          pci:v000013F6d00008788sv0000147Asd0000A017bc*sc*i*
alias:          pci:v000013F6d00008788sv000013F6sd00008788bc*sc*i*
alias:          pci:v000013F6d00008788sv000013F6sd00000010bc*sc*i*
alias:          pci:v000013F6d00008788sv000013F6sd00000001bc*sc*i*
alias:          pci:v000013F6d00008788sv000010B0sd00000219bc*sc*i*
alias:          pci:v000013F6d00008788sv000010B0sd00000218bc*sc*i*
alias:          pci:v000013F6d00008788sv000010B0sd00000217bc*sc*i*
alias:          pci:v000013F6d00008788sv000010B0sd00000216bc*sc*i*
depends:        snd-oxygen-lib,snd
intree:         Y
vermagic:       3.5.0-25-generic SMP mod_unload modversions 
parm:           index:card index (array of int)
parm:           id:ID string (array of charp)
parm:           enable:enable card (array of bool)

```

However, things start to get dodgy with alsa:

```
aplay -l                 
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

pacmd output for the curious:

```
pacmd
Welcome to PulseAudio! Use "help" for usage information.
>>> list-cards
1 card(s) available.
    index: 0
	name: <alsa_card.pci-0000_01_00.1>
	driver: <module-alsa-card.c>
	owner module: 4
	properties:
		alsa.card = "0"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xf7080000 irq 17"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:01:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "NVIDIA Corporation"
		device.product.name = "GF110 High Definition Audio Controller"
		device.string = "0"
		device.description = "GF110 High Definition Audio Controller"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	profiles:
		output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400)
		output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 300)
		output:hdmi-stereo-extra1: Digital Stereo (HDMI) Output (priority 5200)
		output:hdmi-stereo-extra2: Digital Stereo (HDMI) Output (priority 5200)
		output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI) Output (priority 100)
		output:hdmi-stereo-extra3: Digital Stereo (HDMI) Output (priority 5200)
		output:hdmi-surround-extra3: Digital Surround 5.1 (HDMI) Output (priority 100)
		off: Off (priority 0)
	active profile: <off>
	ports:
		hdmi-output-0: HDMI / DisplayPort (priority 5900, available: no)
			properties:
				
		hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, available: yes)
			properties:
				
		hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, available: no)
			properties:
				
		hdmi-output-3: HDMI / DisplayPort 4 (priority 5600, available: no)
			properties:

``` 

Trying to reload alsa:

```
sudo alsactl init                                                                      
Found hardware: "HDA-Intel" "Nvidia GPU 18 HDMI/DP" "HDA:10de0018,10de0101,00100100" "0x1462" "0x2571"
Hardware is initialized using a generic method

```

version numbers for those so inclined:

```
sudo alsactl init                                                                      
Found hardware: "HDA-Intel" "Nvidia GPU 18 HDMI/DP" "HDA:10de0018,10de0101,00100100" "0x1462" "0x2571"
Hardware is initialized using a generic method

```

```
alsactl -v   
alsactl version 1.0.25

```

Running cards, as above:

```
 cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf7080000 irq 17

```

So my sound card is not been picked up anywhere, only the nvidia ****, which i dont want to use. I am well out of my depth now with this, any help would be epic!

Thanks!

---

### Post by Yellow Pasque on 2013-02-23
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by golfcaddy on 2013-02-23
Thanks for the reply, output is here - [http://www.alsa-project.org/db/?f=3866d0c401b787a6949987d563209fe9a9579731]("http://www.alsa-project.org/db/?f=3866d0c401b787a6949987d563209fe9a9579731")

---

### Post by golfcaddy on 2013-03-07
Hi, 

/bumping this

Apparently this card should work fine with 1.0.25 under xubuntu 12.10. Any ideas? 

Thanks!

---

