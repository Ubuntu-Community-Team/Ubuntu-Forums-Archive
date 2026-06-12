---
title: "USB headset does not work anymore"
date: 2011-01-13
forum: Multimedia Software
---

### Post by michaelkr on 2011-01-13
Hey out there!

I've got the following problem:

My USB Headset with C-Media chipset used to work on my Ubuntu 10.04 machine for a long time until about three days ago. Now the device is still listed as sink in pulseaudio:

```
index: 5
	name: <alsa_output.usb-0d8c_C-Media_USB_Headphone_Set-00-default.analog-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: RUNNING
	suspend cause: 
	priority: 9449
	volume: 0:  77% 1:  77%
	        0: -6,97 dB 1: -6,97 dB
	        balance 0,00
	base volume: 100%
	             0,00 dB
	volume steps: 65537
	muted: no
	current latency: 26,21 ms
	max request: 3 KiB
	max rewind: 344 KiB
	monitor source: 9
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 1
	linked by: 3
	configured latency: 20,00 ms; range is 0,50 .. 2000,00 ms
	card: 3 <alsa_card.usb-0d8c_C-Media_USB_Headphone_Set-00-default>
	module: 24
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "USB Audio"
		alsa.id = "USB Audio"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "1"
		alsa.card_name = "C-Media USB Headphone Set"
		alsa.long_card_name = "C-Media USB Headphone Set   at usb-0000:00:13.1-3, full speed"
		alsa.driver_name = "snd_usb_audio"
		device.bus_path = "pci-0000:00:13.1-usb-0:3:1.0"
		sysfs.path = "/devices/pci0000:00/0000:00:13.1/usb6/6-3/6-3:1.0/sound/card1"
		udev.id = "usb-0d8c_C-Media_USB_Headphone_Set-00-default"
		device.bus = "usb"
		device.vendor.id = "0d8c"
		device.vendor.name = "C-Media Electronics, Inc."
		device.product.id = "000c"
		device.product.name = "Audio Adapter"
		device.serial = "0d8c_C-Media_USB_Headphone_Set"
		device.form_factor = "headphone"
		device.string = "front:1"
		device.buffering.buffer_size = "352800"
		device.buffering.fragment_size = "176400"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Audio Adapter Analog Stereo"
		alsa.mixer_name = "USB Mixer"
		alsa.components = "USB0d8c:000c"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-headphones-usb"
	ports:
		analog-output: Analog Output (priority 9900)
		analog-output-speaker: Analog Speakers (priority 10000)
	active port: <analog-output-speaker>
```

In the pulseaudio vu control the volume bars are blinking but there is no sound coming out of the speakers. If i switch over to the onboard sound card, there is sound coming out of my boxes. The headset seems to work, as it still does work on my other machine.

Has anybody an idea on how to fix the problem?

By the way - how can i find out, what packets I updated the last three days?

Any help is appreciated

---

