---
title: "No Sound over Displayport/HDMI, Only Option Analog Output"
date: 2012-07-01
forum: Multimedia Software
---

### Post by ozite on 2012-07-01
I've examined the [DebuggingSound problems Wiki]("https://wiki.ubuntu.com/DebuggingSoundProblems"), but still can't enable sound over Displayport/HDMI in Ubuntu on a Dell Latitude E6510 notebook. Audio is working over Displayport/HDMI in Windows 7 by default. 

I think this issue may be similar to bug [961286]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/961286").

Following [AlsaInfo]("https://wiki.ubuntu.com/Audio/AlsaInfo"), my information is located at [http://www.alsa-project.org/db/?f=6a2f2ceebd41031845175e0fe59b5d8f2477a510]("http://www.alsa-project.org/db/?f=6a2f2ceebd41031845175e0fe59b5d8f2477a510")

A "pacmd ls" gives the log file
```
Welcome to PulseAudio! Use "help" for usage information.
>>> Memory blocks currently allocated: 1, size: 63.9 KiB.
Memory blocks allocated during the whole lifetime: 6116, size: 13.4 MiB.
Memory blocks imported from other processes: 0, size: 0 B.
Memory blocks exported to other processes: 0, size: 0 B.
Total sample cache size: 0 B.
Default sample spec: s16le 2ch 44100Hz
Default channel map: front-left,front-right
Default sink name: alsa_output.pci-0000_00_1b.0.analog-stereo
Default source name: alsa_input.pci-0000_00_1b.0.analog-stereo
Memory blocks of type POOL: 1 allocated/3359 accumulated.
Memory blocks of type POOL_EXTERNAL: 0 allocated/0 accumulated.
Memory blocks of type APPENDED: 0 allocated/0 accumulated.
Memory blocks of type USER: 0 allocated/0 accumulated.
Memory blocks of type FIXED: 0 allocated/2757 accumulated.
Memory blocks of type IMPORTED: 0 allocated/0 accumulated.
19 module(s) loaded.
    index: 0
	name: <module-device-restore>
	argument: <>
	used: -1
	load once: yes
	properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the volume/mute state of devices"
		module.version = "1.1"
    index: 1
	name: <module-stream-restore>
	argument: <>
	used: -1
	load once: yes
	properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the volume/mute/device state of streams"
		module.version = "1.1"
    index: 2
	name: <module-card-restore>
	argument: <>
	used: -1
	load once: yes
	properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore profile of cards"
		module.version = "1.1"
    index: 3
	name: <module-augment-properties>
	argument: <>
	used: -1
	load once: yes
	properties:
		module.author = "Lennart Poettering"
		module.description = "Augment the property sets of streams with additional static information"
		module.version = "1.1"
    index: 4
	name: <module-alsa-card>
	argument: <device_id="1" name="pci-0000_01_00.1" card_name="alsa_card.pci-0000_01_00.1" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1">
	used: 0
	load once: no
	properties:
		module.author = "Lennart Poettering"
		module.description = "ALSA Card"
		module.version = "1.1"
    index: 5
	name: <module-alsa-card>
	argument: <device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1">
	used: 0
	load once: no
	properties:
		module.author = "Lennart Poettering"
		module.description = "ALSA Card"
		module.version = "1.1"
    index: 6
	name: <module-udev-detect>
	argument: <>
	used: -1
	load once: yes
	properties:
		module.author = "Lennart Poettering"
		module.description = "Detect available audio hardware and load matching drivers"
		module.version = "1.1"
    index: 7
	name: <module-native-protocol-unix>
	argument: <>
	used: -1
	load once: no
	properties:
		module.author = "Lennart Poettering"
		module.description = "Native protocol (UNIX sockets)"
		module.version = "1.1"
    index: 8
	name: <module-default-device-restore>
	argument: <>
	used: -1
	load once: yes
	properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the default sink and source"
		module.version = "1.1"
    index: 9
	name: <module-rescue-streams>
	argument: <>
	used: -1
	load once: yes
	properties:
		module.author = "Lennart Poettering"
		module.description = "When a sink/source is removed, try to move their streams to the default sink/source"
		module.version = "1.1"
    index: 10
	name: <module-always-sink>
	argument: <>
	used: -1
	load once: yes
	properties:
		module.author = "Colin Guthrie"
		module.description = "Always keeps at least one sink loaded even if it's a null one"
		module.version = "1.1"
    index: 11
	name: <module-intended-roles>
	argument: <>
	used: -1
	load once: yes
	properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically set device of streams based of intended roles of devices"
		module.version = "1.1"
    index: 12
	name: <module-suspend-on-idle>
	argument: <>
	used: -1
	load once: yes
	properties:
		module.author = "Lennart Poettering"
		module.description = "When a sink/source is idle for too long, suspend it"
		module.version = "1.1"
    index: 13
	name: <module-console-kit>
	argument: <>
	used: -1
	load once: yes
	properties:
		module.author = "Lennart Poettering"
		module.description = "Create a client for each ConsoleKit session of this user"
		module.version = "1.1"
    index: 14
	name: <module-position-event-sounds>
	argument: <>
	used: -1
	load once: yes
	properties:
		module.author = "Lennart Poettering"
		module.description = "Position event sounds between L and R depending on the position on screen of the widget triggering them."
		module.version = "1.1"
    index: 15
	name: <module-filter-heuristics>
	argument: <>
	used: -1
	load once: yes
	properties:
		module.author = "Colin Guthrie"
		module.description = "Detect when various filters are desirable"
		module.version = "1.1"
    index: 16
	name: <module-filter-apply>
	argument: <>
	used: -1
	load once: yes
	properties:
		module.author = "Colin Guthrie"
		module.description = "Load filter sinks automatically when needed"
		module.version = "1.1"
    index: 17
	name: <module-switch-on-port-available>
	argument: <>
	used: -1
	load once: no
	properties:
		
    index: 18
	name: <module-cli-protocol-unix>
	argument: <>
	used: -1
	load once: no
	properties:
		module.author = "Lennart Poettering"
		module.description = "Command line interface protocol (UNIX sockets)"
		module.version = "1.1"
2 sink(s) available.
    index: 0
	name: <alsa_output.pci-0000_01_00.1.hdmi-stereo-extra1>
	driver: <module-alsa-card.c>
	flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9050
	volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max request: 0 KiB
	max rewind: 0 KiB
	monitor source: 0
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
	card: 0 <alsa_card.pci-0000_01_00.1>
	module: 4
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "HDMI 0"
		alsa.id = "HDMI 0"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "7"
		alsa.card = "1"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xe3080000 irq 16"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:01:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "NVIDIA Corporation"
		device.product.name = "High Definition Audio Controller"
		device.string = "hdmi:1,1"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "hdmi-stereo-extra1"
		device.profile.description = "Digital Stereo (HDMI)"
		device.description = "High Definition Audio Controller Digital Stereo (HDMI)"
		alsa.mixer_name = "Nvidia GPU 0b HDMI/DP"
		alsa.components = "HDA:10de000b,10de0101,00100100"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	ports:
		hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, available: no)
			properties:
				
	active port: <hdmi-output-1>
  * index: 1
	name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9959
	volume: 0:  81% 1:  81%
	        0: -5.56 dB 1: -5.56 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max request: 0 KiB
	max rewind: 0 KiB
	monitor source: 1
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
	card: 1 <alsa_card.pci-0000_00_1b.0>
	module: 5
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "STAC92xx Analog"
		alsa.id = "STAC92xx Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xe9660000 irq 48"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Built-in Audio Analog Stereo"
		alsa.mixer_name = "IDT 92HD81B1C5"
		alsa.components = "HDA:111d76d5,1028040b,00100104"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	ports:
		analog-output: Analog Output (priority 9900, available: unknown)
			properties:
				
		analog-output-headphones: Headphones (priority 9000, available: no)
			properties:
				
	active port: <analog-output>
3 source(s) available.
    index: 0
	name: <alsa_output.pci-0000_01_00.1.hdmi-stereo-extra1.monitor>
	driver: <module-alsa-card.c>
	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 1050
	volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 0 KiB
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
	monitor_of: 0
	card: 0 <alsa_card.pci-0000_01_00.1>
	module: 4
	properties:
		device.description = "Monitor of High Definition Audio Controller Digital Stereo (HDMI)"
		device.class = "monitor"
		alsa.card = "1"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xe3080000 irq 16"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:01:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "NVIDIA Corporation"
		device.product.name = "High Definition Audio Controller"
		device.string = "1"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
    index: 1
	name: <alsa_output.pci-0000_00_1b.0.analog-stereo.monitor>
	driver: <module-alsa-card.c>
	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 1950
	volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 0 KiB
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
	monitor_of: 1
	card: 1 <alsa_card.pci-0000_00_1b.0>
	module: 5
	properties:
		device.description = "Monitor of Built-in Audio Analog Stereo"
		device.class = "monitor"
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xe9660000 irq 48"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
		device.form_factor = "internal"
		device.string = "0"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
  * index: 2
	name: <alsa_input.pci-0000_00_1b.0.analog-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9959
	volume: 0:  35% 1:  35%
	        0: -27.32 dB 1: -27.32 dB
	        balance 0.00
	base volume:  13%
	             -52.50 dB
	volume steps: 65537
	muted: yes
	current latency: 0.00 ms
	max rewind: 0 KiB
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 1.00 .. 371.52 ms
	card: 1 <alsa_card.pci-0000_00_1b.0>
	module: 5
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "STAC92xx Analog"
		alsa.id = "STAC92xx Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xe9660000 irq 48"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Built-in Audio Analog Stereo"
		alsa.mixer_name = "IDT 92HD81B1C5"
		alsa.components = "HDA:111d76d5,1028040b,00100104"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	ports:
		analog-input-microphone-internal: Internal Microphone (priority 8900, available: unknown)
			properties:
				
		analog-input-microphone-dock: Dock Microphone (priority 7800, available: no)
			properties:
				
		analog-input-microphone: Microphone (priority 8700, available: no)
			properties:
				
		analog-input-linein: Line In (priority 8100, available: unknown)
			properties:
				
	active port: <analog-input-microphone-internal>
4 client(s) logged in.
    index: 0
	driver: <module-console-kit.c>
	owner module: 13
	properties:
		application.name = "ConsoleKit Session /org/freedesktop/ConsoleKit/Session2"
		console-kit.session = "/org/freedesktop/ConsoleKit/Session2"
    index: 1
	driver: <protocol-native.c>
	owner module: 7
	properties:
		application.name = "GNOME Volume Control Media Keys"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "26"
		application.id = "org.gnome.VolumeControl"
		application.icon_name = "multimedia-volume-control"
		application.version = "3.4.2"
		application.process.id = "1963"
		application.process.user = "n00474500"
		application.process.host = "CHEM-55905-Ubuntu"
		application.process.binary = "gnome-settings-daemon"
		application.language = "en_US.UTF-8"
		window.x11.display = ":0"
		application.process.machine_id = "e50c478e61a737c828824cd500000002"
		application.process.session_id = "e50c478e61a737c828824cd500000002-1341151264.941604-259920289"
    index: 2
	driver: <protocol-native.c>
	owner module: 7
	properties:
		application.name = "Indicator Sound"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "26"
		application.id = "com.canonical.indicator.sound"
		application.icon_name = "multimedia-volume-control"
		application.version = "0.8.5.0"
		application.process.id = "2176"
		application.process.user = "n00474500"
		application.process.host = "CHEM-55905-Ubuntu"
		application.process.binary = "indicator-sound-service"
		application.language = "en_US.UTF-8"
		window.x11.display = ":0"
		application.process.machine_id = "e50c478e61a737c828824cd500000002"
		application.process.session_id = "e50c478e61a737c828824cd500000002-1341151264.941604-259920289"
    index: 10
	driver: <cli.c>
	owner module: 18
	properties:
		application.name = "UNIX socket client"
2 card(s) available.
    index: 0
	name: <alsa_card.pci-0000_01_00.1>
	driver: <module-alsa-card.c>
	owner module: 4
	properties:
		alsa.card = "1"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xe3080000 irq 16"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:01:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "NVIDIA Corporation"
		device.product.name = "High Definition Audio Controller"
		device.string = "1"
		device.description = "High Definition Audio Controller"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	profiles:
		output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400)
		output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 300)
		output:hdmi-stereo-extra1: Digital Stereo (HDMI) Output (priority 5200)
		output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI) Output (priority 100)
		output:hdmi-stereo-extra2: Digital Stereo (HDMI) Output (priority 5200)
		output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI) Output (priority 100)
		output:hdmi-stereo-extra3: Digital Stereo (HDMI) Output (priority 5200)
		output:hdmi-surround-extra3: Digital Surround 5.1 (HDMI) Output (priority 100)
		off: Off (priority 0)
	active profile: <output:hdmi-stereo-extra1>
	sinks:
		alsa_output.pci-0000_01_00.1.hdmi-stereo-extra1/#0: High Definition Audio Controller Digital Stereo (HDMI)
	sources:
		alsa_output.pci-0000_01_00.1.hdmi-stereo-extra1.monitor/#0: Monitor of High Definition Audio Controller Digital Stereo (HDMI)
	ports:
		hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, available: no)
			properties:
				
		hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, available: no)
			properties:
				
		hdmi-output-3: HDMI / DisplayPort 4 (priority 5600, available: no)
			properties:
				
    index: 1
	name: <alsa_card.pci-0000_00_1b.0>
	driver: <module-alsa-card.c>
	owner module: 5
	properties:
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xe9660000 irq 48"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
		device.form_factor = "internal"
		device.string = "0"
		device.description = "Built-in Audio"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	profiles:
		output:analog-stereo: Analog Stereo Output (priority 6000)
		output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060)
		input:analog-stereo: Analog Stereo Input (priority 60)
		off: Off (priority 0)
	active profile: <output:analog-stereo+input:analog-stereo>
	sinks:
		alsa_output.pci-0000_00_1b.0.analog-stereo/#1: Built-in Audio Analog Stereo
	sources:
		alsa_output.pci-0000_00_1b.0.analog-stereo.monitor/#1: Monitor of Built-in Audio Analog Stereo
		alsa_input.pci-0000_00_1b.0.analog-stereo/#2: Built-in Audio Analog Stereo
	ports:
		analog-output: Analog Output (priority 9900, available: unknown)
			properties:
				
		analog-output-headphones: Headphones (priority 9000, available: no)
			properties:
				
		analog-input-microphone-internal: Internal Microphone (priority 8900, available: unknown)
			properties:
				
		analog-input-microphone-dock: Dock Microphone (priority 7800, available: no)
			properties:
				
		analog-input-microphone: Microphone (priority 8700, available: no)
			properties:
				
		analog-input-linein: Line In (priority 8100, available: unknown)
			properties:
				
0 sink input(s) available.
0 source outputs(s) available.
0 cache entrie(s) available.
>>> 
```

The Analog Output is working in Ubuntu and it is the only option listed under Sound Settings.
[IMG]http://i75.photobucket.com/albums/i318/ozite/sound-analog_output_only-1.png[/IMG]

Ubuntu 12.04 Precise (64-bit) 3.2.0-26-generic.
cat /proc/asound/cards
0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xe9660000 irq 48
1 [NVidia ]: HDA-Intel - HDA NVidia
HDA NVidia at 0xe3080000 irq 16

If I click the Analog Output in the Sound settings, I get sound through the notebook speakers and "sudo speaker-test -c6 -l1 -twav" works through the notebook speakers.
There are slider bars for the IDT 92HD81B1C5, but no slider bars under the Gnome Alsa Mixer for the NVIDIA GPU HDMI/DP.

[IMG]http://i75.photobucket.com/albums/i318/ozite/gnome_alsa_mixer.png[/IMG]
[IMG]http://i75.photobucket.com/albums/i318/ozite/gnome_alsa_mixer2.png[/IMG]
Tried AlsaMixer and Nvidia GPU 0b HDMI/DP shows all 00 and can't be adjusted with the up arrow.
[IMG]http://i75.photobucket.com/albums/i318/ozite/alsa_mixer_00-1.png[/IMG]
pavucontrol, the built-in Audio Analog Stereo works fine.
Switch to HDMI
[IMG]http://i75.photobucket.com/albums/i318/ozite/pavucontrol_hdmi_bars-1.png[/IMG]
Play sound, see bars moving, but no sound.When playing sound (i.e. a Youtube video), the PulseAudio Volume Meter shows bar movement for the HDMI, but there is no sound. 
Under the configuration tab there are four Digital Stereo (HDMI) Output and four Digital Surround 5.1 (HDMI) Output options. I tried all 8 while a sound was playing, with no success.
[IMG]http://i75.photobucket.com/albums/i318/ozite/pavucontrol_checked.png[/IMG]
Tried "ubuntu-bug audio"
[IMG]http://i75.photobucket.com/albums/i318/ozite/ubuntu-bug_audio.png[/IMG]
I can't change it in sound output, since there is only one option.

The contents of /usr/share/pulseaudio/alsa-mixer/paths/hdmi-output-0.conf are:
```

[General]
description = HDMI / DisplayPort
priority = 59

[Jack HDMI/DP,pcm=3]
required = ignore
```

I tried the workaround and "pulseaudio -k" in thread [1944030]("http://ubuntuforums.org/showthread.php?t=1944030") without success.

I thought this might be a configuration issue. I am hopeful someone can point me in the right direction. Thanks in advance.

Nvidia NVS 3100m
[IMG]http://i75.photobucket.com/albums/i318/ozite/Nvidia_3100m.png[/IMG]

---

### Post by BicyclerBoy on 2012-07-01
Is this notebook an optimus graphics setup ??
Exactly how HDMI audio behaves with optimus is a good question.

If I read the alsa info correctly...
You appear to be using nouveau graphics driver.
I doubt that nouveau has full HDA audio support.

You might want to untick MPEG, EAC3, DTS AC3 in pavucontrol..your alsa info shows your nVidia codecs supports PCM & AC3 & lists IEC958.
This could be because of nouveau or alsa 1.0.24 

IEC958 device only supports PCM stereo & AC3/DTS.

Your alsa info shows (dmesg) no presence detect or eld (hot plug events)..did you have the HDMI receiver connected (& ON) during that reboot ?

---

### Post by ozite on 2012-07-01
> **BicyclerBoy said:**
> Is this notebook an optimus graphics setup ??
Exactly how HDMI audio behaves with optimus is a good question.

If I read the alsa info correctly...
You appear to be using nouveau graphics driver.
I doubt that nouveau has full HDA audio support.

You might want to untick MPEG, EAC3, DTS AC3 in pavucontrol..your alsa info shows your nVidia codecs supports PCM & AC3 & lists IEC958.
This could be because of nouveau or alsa 1.0.24 

IEC958 device only supports PCM stereo & AC3/DTS.

Your alsa info shows (dmesg) no presence detect or eld (hot plug events)..did you have the HDMI receiver connected (& ON) during that reboot ?

Thanks for the response. It's a Dell E6510 with a Nvidia NVS 3100m (verified with CPUz in Windows). 

I tried on two different devices in different rooms, one a Samsung HDTV and also a Pioneer receiver. I rebooted from Windows 7,where the sound is working over HDMI on both, to Ubuntu where it won't work on either.  I left the TV and the Receiver turned on in the separate trials.  

In Windows I could plug in the HDMI and it would detect it and have sound.  I also tried unplugging and pluggin in under Ubuntu. Video would be visible on the TV, but no sound. Still no option to select HDMI through the sound settings, only Analog Output.

I'm using nouveau driver and "Additional Drivers" shows that "No propietary drivers are in use on this system".  There is no option visible to install them.

I unticked all boxes except PCM, but still no sound.  

When there is no sound over HDMI, but bars moving indicating sound should be present from playing a video, I can click sound effects and it plays the alert sound over the notebook speakers.

---

### Post by neu5eeCh on 2012-07-02
I am noticing the same issues on my own Sony VAIO laptop. The volume keys control the volume for the HDMI Sound Card, but not the Built-in Analog Stereo. If I change playback to the HDMI card, I don't get any sound. 

I wonder if we should be filing a bug report?

---

