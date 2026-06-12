---
title: "Pulseaudio doesn't see all alsa sinks"
date: 2016-06-15
forum: Multimedia Software
---

### Post by el_rico on 2016-06-15
Hello,

I'm on Ubuntu 15.10 and and pulseaudio has just lost audio sinks. All the sinks are present in Alsa and I've tested them by playing a sample:
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
But
```

pactl list sinks
Sink #0
	State: IDLE
	Name: alsa_output.pci-0000_01_00.1.hdmi-stereo
	Description: HDA NVidia Digital Stereo (HDMI)
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 6
	Mute: no
	Volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
	        balance 0.00
	Base Volume: 65536 / 100% / 0.00 dB
	Monitor Source: alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor
	Latency: 371501 usec, configured 371519 usec
	Flags: HARDWARE DECIBEL_VOLUME LATENCY SET_FORMATS 
	Properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "HDMI 0"
		alsa.id = "HDMI 0"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "3"
		alsa.card = "1"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xf7080000 irq 17"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:01:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "NVIDIA Corporation"
		device.product.id = "0fba"
		device.string = "hdmi:1"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "hdmi-stereo"
		device.profile.description = "Digital Stereo (HDMI)"
		device.description = "HDA NVidia Digital Stereo (HDMI)"
		alsa.mixer_name = "Nvidia GPU 72 HDMI/DP"
		alsa.components = "HDA:10de0072,38422962,00100100"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Ports:
		hdmi-output-0: HDMI / DisplayPort (priority: 5900, not available)
	Active Port: hdmi-output-0
	Formats:
		pcm

```
So, while there are 3 functional sinks in Alsa (1 analog/1 digital for on-board ALC892 + HDMI), only 1 sink is seen by pulseaudio (HDMI).

Oh, and yes, it was working before (and I cannot relate this to any change - even though it must be!)

Any idea of what could be wrong?

Thanks!

---

### Post by el_rico on 2016-06-17
```
pulseaudio -vvvvv
``` does not show any obvious problem: what should I pay attention to?

Thanks!

---

### Post by el_rico on 2016-06-19
It works when using a Live Ubuntu. I've also tried re-installing pulseaudio stack, without success (but I may not do this the right way).

Any hint?...

---

### Post by yoshii on 2016-06-22
QasMixer settings?

---

### Post by marseille2 on 2016-06-23
Try reloading alsa, then reboot to see if they return:

```
$ sudo alsa force-reload
```

---

### Post by el_rico on 2016-06-25
> **marseille2 said:**
> Try reloading alsa, then reboot to see if they return:

```
$ sudo alsa force-reload
```

It's making progress: alsa force-reload make the lost devices appear again. But those are lost at each reboot. How can I fix it permanently? 

Thanks!

---

### Post by marseille2 on 2016-06-27
You might want to take a look at this [thread]("https://wiki.archlinux.org/index.php/PulseAudio/Examples#Set_default_input_sources") over at ArchLinux. It covers forcing Pulseaudio (PA) to load specific sinks. But IMO it might be overkill during the early troubleshooting stage. And just looking at the output of pactl shows that PA wants to use the video card as the default sound card. So IMO, if you haven't already done so, a decent first step is to install pasystray... which shows all your sinks and sources that get loaded, as well as let you switch them on the fly. (If no sinks and/or sources get loaded on boot... pasystray won't show any, and if you lose them while the computer is on... it's going to report that the 'Dummy' sink in effect so). ... BTW, I saw the [package]("https://launchpad.net/ubuntu/wily/+package/pasystray") in Launchpad (I'm not on 15.10 so I have no idea what's going on in its package manager, etc.).

After pasystray is installed (and to avoid extra steps), I would suspend PA and delete its cookies:

1. Suspend PA:
```
$ echo autospawn = no > $HOME/.config/pulse/client.conf
```

2. Delete cookie folder in /home: "**.config/pulse**"

3. Reboot

4. Start pasystray to inspect the sinks and/or sources, and switch as needed.

----

If that's not enough (and assuming that ALSA isn't buggy) ... then I'd take a look at the files in /etc/pulse (see Arch), starting with:

1. /etc/pulse/default.pa
2. /etc/pulse/client.conf

---

