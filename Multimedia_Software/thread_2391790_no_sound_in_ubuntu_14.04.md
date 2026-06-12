---
title: "no sound in ubuntu 14.04"
date: 2018-05-13
forum: Multimedia Software
---

### Post by mixtutor on 2018-05-13
Hi guys, i am having an issue that there is no sound in ubuntu 14. It is fresh install on desktop pc with motherboard ASUS H110M-R.
```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```
```
pacmd list-cards
Welcome to PulseAudio! Use "help" for usage information.
>>> 1 card(s) available.
    index: 0
	name: <alsa_card.pci-0000_00_1f.3>
	driver: <module-alsa-card.c>
	owner module: 5
	properties:
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xf7120000 irq 139"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1f.3"
		sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "a170"
		device.form_factor = "internal"
		device.string = "0"
		device.description = "Built-in Audio"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	profiles:
		input:analog-stereo: Analog Stereo Input (priority 60, available: unknown)
		output:analog-stereo: Analog Stereo Output (priority 6000, available: unknown)
		output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060, available: unknown)
		off: Off (priority 0, available: unknown)
	active profile: <output:analog-stereo>
	sinks:
		alsa_output.pci-0000_00_1f.3.analog-stereo/#0: Built-in Audio Analog Stereo
	sources:
		alsa_output.pci-0000_00_1f.3.analog-stereo.monitor/#0: Monitor of Built-in Audio Analog Stereo
	ports:
		analog-input-microphone-front: Front Microphone (priority 8500, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "audio-input-microphone"
		analog-input-microphone-rear: Rear Microphone (priority 8200, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "audio-input-microphone"
		analog-input-linein: Line In (priority 8100, latency offset 0 usec, available: no)
			properties:
				
		analog-output: Analog Output (priority 9900, latency offset 20000 usec, available: unknown)
			properties:
				
		analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "audio-headphones"
```


I also tried


```
sudo apt-get remove --purge alsa-base pulseaudio
   sudo apt-get install alsa-base pulseaudio

```

---

### Post by kazakore on 2018-05-13
Check pavucontrol (Pulse Audio controls and routing) and qasmixer, or alsamixer from the terminal if it's not installed on your system (for Alsa mixer levels etc.) Hopefully between then you'll find something muted or a level completely down.....

---

