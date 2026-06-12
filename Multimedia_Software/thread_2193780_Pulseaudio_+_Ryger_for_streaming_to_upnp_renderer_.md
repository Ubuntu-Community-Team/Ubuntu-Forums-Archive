---
title: "Pulseaudio + Ryger for streaming to upnp renderer - working with latest versions"
date: 2013-12-14
forum: Multimedia Software
---

### Post by kamelie1706 on 2013-12-14
Hi,

I have now trying to get ryder & pulseaudio to work together without luck.

1-Ryger installation looks fine and I can use it as independant upnp server.
 
2-pulseaudio works and I get the sound from onboard sound

The issue is when I launch pavucontrol, I do not see the "Upnp/Dlna" option as output in the playback tab when playing a music nor in the "output device".

System:
- Lubuntu 13.10 64 Bits
- Rygel 0.18.4 
- pulseaudio 4.0

Setting in rygel.conf:
[GstLaunch]
enabled=true
launch-items=mypulseaudiosink
mypulseaudiosink-title=Audio on @HOSTNAME@
mypulseaudiosink-mime=audio/x-wav
mypulseaudiosink-launch=pulsesrc device=alsa_output.pci-0000_00_14.2.analog-stereo.monitor ! wavpackenc

Message when launching rygel 
Rygel-Message: New plugin 'GstLaunch' available
MPRIS-Message: rygel-mpris-plugin-factory.vala:33: Module 'MPRIS' disabled by user. Ignoring&#8230;
Rygel-Message: New plugin 'MediaExport' available
External-Message: rygel-external-plugin-factory.vala:33: Module 'External' disabled by user. Ignoring&#8230;


Any idea where I should be looking?

---

### Post by kamelie1706 on 2013-12-14
Erratum:
It seems I had to enable the upnp settings in "Configure Local Sound server".

Now I have the option in playback panel.
- My receiver can see "Gst Launch"/Audio on pc/Audio on pc
- I select Upnp in pulseaudio setting as output
.... nothing comes out the av receiver

I use pc's media streaming, this is playing fine though the av receiver

---

### Post by kamelie1706 on 2013-12-14
Error message from rygel
(rygel:5331): MediaEngine-GStreamer-CRITICAL **: Error from pipeline RygelGstDataSource: pulsesrc.c(1605): gst_pulsesrc_prepare (): /GstPipeline:RygelGstDataSource/GstBin:bin0/GstPulseSrc:pulsesrc0

---

### Post by kamelie1706 on 2013-12-14
This is what I have on "pacmd list-sources" 
Welcome to PulseAudio! Use "help" for usage information.
>>> 4 source(s) available.
    index: 0
	name: <alsa_output.pci-0000_01_05.1.hdmi-stereo.monitor>
	driver: <module-alsa-card.c>
	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: RUNNING
	suspend cause: 
	priority: 1050
	volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 64 KiB
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 1
	linked by: 1
	configured latency: 46.00 ms; range is 46.00 .. 371.52 ms
	monitor_of: 0
	card: 0 <alsa_card.pci-0000_01_05.1>
	module: 5
	properties:
		device.description = "Monitor of M5A88-V EVO Digital Stereo (HDMI)"
		device.class = "monitor"
		alsa.card = "1"
		alsa.card_name = "HDA ATI HDMI"
		alsa.long_card_name = "HDA ATI HDMI at 0xfe8e8000 irq 19"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:01:05.1"
		sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:05.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
		device.product.id = "970f"
		device.product.name = "M5A88-V EVO"
		device.string = "1"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
    index: 1
	name: <alsa_output.pci-0000_00_14.2.analog-stereo.monitor>
	driver: <module-alsa-card.c>
	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: RUNNING
	suspend cause: 
	priority: 1950
	volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 64 KiB
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 1
	linked by: 1
	configured latency: 20.00 ms; range is 2.00 .. 371.52 ms
	monitor_of: 1
	card: 1 <alsa_card.pci-0000_00_14.2>
	module: 6
	properties:
		device.description = "Monitor of Built-in Audio Analog Stereo"
		device.class = "monitor"
		alsa.card = "0"
		alsa.card_name = "HDA ATI SB"
		alsa.long_card_name = "HDA ATI SB at 0xfe6f8000 irq 16"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:14.2"
		sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
		device.product.id = "4383"
		device.product.name = "M5A88-V EVO"
		device.form_factor = "internal"
		device.string = "0"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
  * index: 2
	name: <alsa_input.pci-0000_00_14.2.analog-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: RUNNING
	suspend cause: 
	priority: 9959
	volume: 0:  11% 1:  11%
	        0: -57.00 dB 1: -57.00 dB
	        balance 0.00
	base volume:  10%
	             -60.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.09 ms
	max rewind: 0 KiB
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 1
	linked by: 1
	configured latency: 20.00 ms; range is 2.00 .. 371.52 ms
	card: 1 <alsa_card.pci-0000_00_14.2>
	module: 6
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "ALC892 Analog"
		alsa.id = "ALC892 Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA ATI SB"
		alsa.long_card_name = "HDA ATI SB at 0xfe6f8000 irq 16"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:14.2"
		sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
		device.product.id = "4383"
		device.product.name = "M5A88-V EVO"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Built-in Audio Analog Stereo"
		alsa.mixer_name = "Realtek ALC892"
		alsa.components = "HDA:10ec0892,1043841b,00100302"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	ports:
		analog-input-microphone-front: Front Microphone (priority 8500, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "audio-input-microphone"
		analog-input-microphone-rear: Rear Microphone (priority 8200, latency offset 0 usec, available: yes)
			properties:
				device.icon_name = "audio-input-microphone"
		analog-input-linein: Line In (priority 8100, latency offset 0 usec, available: no)
			properties:
				
	active port: <analog-input-microphone-rear>
    index: 3
	name: <upnp.monitor>
	driver: <module-null-sink.c>
	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: RUNNING
	suspend cause: 
	priority: 1000
	volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 3 KiB
	sample spec: s16be 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 2
	linked by: 2
	configured latency: 20.00 ms; range is 0.50 .. 2000.00 ms
	monitor_of: 2
	module: 23
	properties:
		device.description = "Monitor of DLNA/UPnP Streaming"
		device.class = "monitor"
		device.icon_name = "audio-input-microphone"

---

### Post by kamelie1706 on 2013-12-14
Input 3 seems very strange!!! microphone => upnp.monitor?

---

