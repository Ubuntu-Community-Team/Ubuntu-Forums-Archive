---
title: "pulse audio Analog Stereo Input/Duplex is always &quot;available: no&quot;"
date: 2020-10-17
forum: Multimedia Software
---

### Post by mathiraj on 2020-10-17
I use ubuntu mate 20.04.1 (with all updates)
i can not get the microphone to work on my pc. Sound output works fine on the speakers.

"pactl list" returns the following. 

```
Card #2
	Name: alsa_card.pci-0000_00_1b.0
	Driver: module-alsa-card.c
	Owner Module: 9
	Properties:
		alsa.card = "2"
		alsa.card_name = "HDA Intel PCH"
		alsa.long_card_name = "HDA Intel PCH at 0xe131c000 irq 52"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card2"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "9ca0"
		device.product.name = "Wildcat Point-LP High Definition Audio Controller"
		device.form_factor = "internal"
		device.string = "2"
		device.description = "Built-in Audio"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Profiles:
		input:analog-stereo: Analog Stereo Input (sinks: 0, sources: 1, priority: 65, available: no)
		output:analog-stereo: Analog Stereo Output (sinks: 1, sources: 0, priority: 6500, available: yes)
		output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (sinks: 1, sources: 1, priority: 6565, available: no)
		off: Off (sinks: 0, sources: 0, priority: 0, available: yes)
	Active Profile: output:analog-stereo
	Ports:
		analog-input-mic: Microphone (priority: 8700, latency offset: 0 usec, not available)
			Properties:
				device.icon_name = "audio-input-microphone"
			Part of profile(s): input:analog-stereo, output:analog-stereo+input:analog-stereo
		analog-output-headphones: Headphones (priority: 9900, latency offset: 0 usec, available)
			Properties:
				device.icon_name = "audio-headphones"
			Part of profile(s): output:analog-stereo, output:analog-stereo+input:analog-stereo

```

I see that "**input:analog-stereo: Analog Stereo Input**" and "**output:analog-stereo+input:analog-stereo: Analog Stereo Duplex**" are always "**available: no**". Even if i plug in the microphone this does not become available.

pavucontrol shows "**Analog Stereo Input**" as **unplugged** and **unavailable** even if i connect the microphone.

My pc has a combo jack (headphone/mic). i use a splitter cable to connect speaker and microphone. Has anyone faced such problem? Any solutions?

Thanks in advance.
Appreciate all the help.

---

