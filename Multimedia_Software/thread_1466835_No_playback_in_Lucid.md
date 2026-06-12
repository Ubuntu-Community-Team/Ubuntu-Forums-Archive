---
title: "No playback in Lucid"
date: 2010-04-30
forum: Multimedia Software
---

### Post by peppot on 2010-04-30
After upgrading to 10.4, audio no longer works.
It seems to be a PulseAudio problem. Rhythmbox and Quod Libet show the "red stop icon" when trying to play any audio (be it FLAC, MP3 etc), and playing audio in Totem gives: 

```
"** Message: Error: Failed to connect stream: No such unit
pulsesink.c(833): gst_pulseringbuffer_acquire (): /GstPlayBin2:play/GstPlaySink:playsink0/GstBin:abin/GstBin:audiosinkbin/GstGConfAudioSink:audio-sink/GstBin:bin2/GstPulseSink:pulsesink1" in console.
```

Any clues? I've been using various outputs such as HDMI, Intel and Bluetooth, may this have gotten screwed up in the upgrade?

Suggestions?

hda-intel, 2.6.32-21, pulseaudio 0.9.21-63-gd3efa-dirty

---

### Post by hugmenot on 2010-05-01
```
 cat /proc/asound/cards
```

and then 

```
pactl list
```

---

### Post by peppot on 2010-05-01
```

$ cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd5200000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xd0030000 irq 17

```

and

```


Module #0
	Name: module-device-restore
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the volume/mute state of devices"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #1
	Name: module-stream-restore
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the volume/mute/device state of streams"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #2
	Name: module-card-restore
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore profile of cards"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #3
	Name: module-augment-properties
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Augment the property sets of streams with additional static information"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #4
	Name: module-alsa-card
	Argument: device_id="1" name="pci-0000_01_00.1" card_name="alsa_card.pci-0000_01_00.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"
	Usage counter: 0
	Properties:
		module.author = "Lennart Poettering"
		module.description = "ALSA Card"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #5
	Name: module-alsa-card
	Argument: device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"
	Usage counter: 0
	Properties:
		module.author = "Lennart Poettering"
		module.description = "ALSA Card"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #6
	Name: module-udev-detect
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Detect available audio hardware and load matching drivers"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #7
	Name: module-bluetooth-discover
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Joao Paulo Rechi Vita"
		module.description = "Detect available bluetooth audio devices and load bluetooth audio drivers"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #8
	Name: module-esound-protocol-unix
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "ESOUND protocol (UNIX sockets)"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #9
	Name: module-native-protocol-unix
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Native protocol (UNIX sockets)"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #10
	Name: module-gconf
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "GConf Adapter"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #11
	Name: module-default-device-restore
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the default sink and source"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #12
	Name: module-rescue-streams
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "When a sink/source is removed, try to move their streams to the default sink/source"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #13
	Name: module-always-sink
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Colin Guthrie"
		module.description = "Always keeps at least one sink loaded even if it's a null one"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #14
	Name: module-intended-roles
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically set device of streams based of intended roles of devices"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #15
	Name: module-suspend-on-idle
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "When a sink/source is idle for too long, suspend it"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #16
	Name: module-console-kit
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Create a client for each ConsoleKit session of this user"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #17
	Name: module-position-event-sounds
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Position event sounds between L and R depending on the position on screen of the widget triggering them."
		module.version = "0.9.21-63-gd3efa-dirty"

Module #18
	Name: module-x11-xsmp
	Argument: 
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "X11 session management"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #19
	Name: module-x11-publish
	Argument: display=:0.0
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "X11 credential publisher"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #20
	Name: module-x11-bell
	Argument: display=:0.0 sample=bell.ogg
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "X11 bell interceptor"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #21
	Name: module-x11-cork-request
	Argument: display=:0.0
	Usage counter: inte tillgänglig
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Synthesize X11 media key events when cork/uncork is requested"
		module.version = "0.9.21-63-gd3efa-dirty"

Sink #0
	State: SUSPENDED
	Name: alsa_output.pci-0000_01_00.1.hdmi-stereo
	Description: RV620 Audio device [Radeon HD 34xx Series] Digital Stereo (HDMI)
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 4
	Mute: no
	Volume: 0: 100% 1: 100%
	        0: 0,00 dB 1: 0,00 dB
	        balance 0,00
	Base Volume: 100%
	             0,00 dB
	Monitor Source: alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor
	Latency: 0 usec, configured 0 usec
	Flags: HARDWARE DECIBEL_VOLUME LATENCY 
	Properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "ATI HDMI"
		alsa.id = "ATI HDMI"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "3"
		alsa.card = "1"
		alsa.card_name = "HDA ATI HDMI"
		alsa.long_card_name = "HDA ATI HDMI at 0xd0030000 irq 17"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:01:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "ATI Technologies Inc"
		device.product.id = "aa28"
		device.product.name = "RV620 Audio device [Radeon HD 34xx Series]"
		device.string = "hdmi:1"
		device.buffering.buffer_size = "352768"
		device.buffering.fragment_size = "176384"
		device.access_mode = "mmap+timer"
		device.profile.name = "hdmi-stereo"
		device.profile.description = "Digital Stereo (HDMI)"
		device.description = "RV620 Audio device [Radeon HD 34xx Series] Digital Stereo (HDMI)"
		alsa.mixer_name = "ATI R6xx HDMI"
		alsa.components = "HDA:1002aa01,104d2e00,00100000"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"

Sink #1
	State: SUSPENDED
	Name: alsa_output.pci-0000_00_1b.0.analog-stereo
	Description: Internt ljud Analog Stereo
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 5
	Mute: no
	Volume: 0:  57% 1:  57%
	        0: -14,85 dB 1: -14,85 dB
	        balance 0,00
	Base Volume: 100%
	             0,00 dB
	Monitor Source: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
	Latency: 0 usec, configured 0 usec
	Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
	Properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "ALC262 Analog"
		alsa.id = "ALC262 Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "293e"
		device.product.name = "82801I (ICH9 Family) HD Audio Controller"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "352768"
		device.buffering.fragment_size = "176384"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Internt ljud Analog Stereo"
		alsa.mixer_name = "Realtek ALC262"
		alsa.components = "HDA:10ec0262,104d2e00,00100302 HDA:14f12c06,104d1700,00100000"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Ports:
		analog-output: Analog Output (priority. 9900)
		analog-output-speaker: Analog Speakers (priority. 10000)
		analog-output-headphones: Analog Headphones (priority. 9000)
	Aktiv port: analog-output-speaker

Source #0
	State: SUSPENDED
	Name: alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor
	Description: Monitor of RV620 Audio device [Radeon HD 34xx Series] Digital Stereo (HDMI)
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 4
	Mute: no
	Volume: 0: 100% 1: 100%
	        0: 0,00 dB 1: 0,00 dB
	        balance 0,00
	Base Volume: 100%
	             0,00 dB
	Monitor of Sink: alsa_output.pci-0000_01_00.1.hdmi-stereo
	Latency: 0 usec, configured 0 usec
	Flags: DECIBEL_VOLUME LATENCY 
	Properties:
		device.description = "Monitor of RV620 Audio device [Radeon HD 34xx Series] Digital Stereo (HDMI)"
		device.class = "monitor"
		alsa.card = "1"
		alsa.card_name = "HDA ATI HDMI"
		alsa.long_card_name = "HDA ATI HDMI at 0xd0030000 irq 17"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:01:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "ATI Technologies Inc"
		device.product.id = "aa28"
		device.product.name = "RV620 Audio device [Radeon HD 34xx Series]"
		device.string = "1"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"

Source #1
	State: SUSPENDED
	Name: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
	Description: Monitor of Internt ljud Analog Stereo
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 5
	Mute: no
	Volume: 0: 100% 1: 100%
	        0: 0,00 dB 1: 0,00 dB
	        balance 0,00
	Base Volume: 100%
	             0,00 dB
	Monitor of Sink: alsa_output.pci-0000_00_1b.0.analog-stereo
	Latency: 0 usec, configured 0 usec
	Flags: DECIBEL_VOLUME LATENCY 
	Properties:
		device.description = "Monitor of Internt ljud Analog Stereo"
		device.class = "monitor"
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "293e"
		device.product.name = "82801I (ICH9 Family) HD Audio Controller"
		device.form_factor = "internal"
		device.string = "0"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"

Source #2
	State: SUSPENDED
	Name: alsa_input.pci-0000_00_1b.0.analog-stereo
	Description: Internt ljud Analog Stereo
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 5
	Mute: yes
	Volume: 0:  17% 1:  17%
	        0: -46,50 dB 1: -46,50 dB
	        balance 0,00
	Base Volume:  27%
	             -34,50 dB
	Monitor of Sink: inte tillgänglig
	Latency: 0 usec, configured 0 usec
	Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
	Properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "ALC262 Analog"
		alsa.id = "ALC262 Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "293e"
		device.product.name = "82801I (ICH9 Family) HD Audio Controller"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "352768"
		device.buffering.fragment_size = "176384"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Internt ljud Analog Stereo"
		alsa.mixer_name = "Realtek ALC262"
		alsa.components = "HDA:10ec0262,104d2e00,00100302 HDA:14f12c06,104d1700,00100000"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"

Client #0
	Driver: module-console-kit.c
	Owner Module: 16
	Properties:
		application.name = "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
		console-kit.session = "/org/freedesktop/ConsoleKit/Session1"

Client #2
	Driver: module-x11-xsmp.c
	Owner Module: 18
	Properties:
		application.name = "XSMP Session on gnome-session as 1014ae12547e6ffe73127271014845898400000015380045"
		xsmp.vendor = "gnome-session"
		xsmp.client.id = "1014ae12547e6ffe73127271014845898400000015380045"

Client #3
	Driver: protocol-native.c
	Owner Module: 9
	Properties:
		application.name = "GNOME Volume Control Media Keys"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "16"
		application.id = "org.gnome.VolumeControl"
		application.icon_name = "multimedia-volume-control"
		application.version = "2.30.0"
		application.process.id = "1614"
		application.process.user = "petter"
		application.process.host = "gunilla"
		application.process.binary = "gnome-settings-daemon"
		window.x11.display = ":0.0"
		application.language = "sv_SE.UTF-8"
		application.process.machine_id = "96ea5767ea6639ae0eaae94049cd171c"
		application.process.session_id = "96ea5767ea6639ae0eaae94049cd171c-1272710141.168959-909394282"

Client #9
	Driver: protocol-native.c
	Owner Module: 9
	Properties:
		application.name = "ayatana.indicator.sound"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "16"
		application.process.id = "2175"
		application.process.user = "petter"
		application.process.host = "gunilla"
		application.process.binary = "indicator-sound-service"
		application.language = "sv_SE.UTF-8"
		window.x11.display = ":0.0"
		application.process.machine_id = "96ea5767ea6639ae0eaae94049cd171c"
		application.process.session_id = "96ea5767ea6639ae0eaae94049cd171c-1272710141.168959-909394282"

Client #14
	Driver: protocol-native.c
	Owner Module: 9
	Properties:
		application.name = "pactl"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "16"
		application.process.id = "3774"
		application.process.user = "petter"
		application.process.host = "gunilla"
		application.process.binary = "pactl"
		application.language = "sv_SE.UTF-8"
		window.x11.display = ":0.0"
		application.process.machine_id = "96ea5767ea6639ae0eaae94049cd171c"
		application.process.session_id = "96ea5767ea6639ae0eaae94049cd171c-1272710141.168959-909394282"

Card #0
	Name: alsa_card.pci-0000_01_00.1
	Driver: module-alsa-card.c
	Owner Module: 4
	Properties:
		alsa.card = "1"
		alsa.card_name = "HDA ATI HDMI"
		alsa.long_card_name = "HDA ATI HDMI at 0xd0030000 irq 17"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:01:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "ATI Technologies Inc"
		device.product.id = "aa28"
		device.product.name = "RV620 Audio device [Radeon HD 34xx Series]"
		device.string = "1"
		device.description = "RV620 Audio device [Radeon HD 34xx Series]"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Profiles:
		output:hdmi-stereo: Digital Stereo (HDMI) Output (sinks: 1, sources: 0, priority. 5400)
		off: Off (sinks: 0, sources: 0, priority. 0)
	Aktiv profil: output:hdmi-stereo

Card #1
	Name: alsa_card.pci-0000_00_1b.0
	Driver: module-alsa-card.c
	Owner Module: 5
	Properties:
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "293e"
		device.product.name = "82801I (ICH9 Family) HD Audio Controller"
		device.form_factor = "internal"
		device.string = "0"
		device.description = "Internt ljud"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Profiles:
		output:analog-stereo: Analog Stereo Output (sinks: 1, sources: 0, priority. 6000)
		output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (sinks: 1, sources: 1, priority. 6060)
		input:analog-stereo: Analog Stereo Input (sinks: 0, sources: 1, priority. 60)
		off: Off (sinks: 0, sources: 0, priority. 0)
	Aktiv profil: output:analog-stereo+input:analog-stereo

```

---

### Post by peppot on 2010-05-01
When I start gstreamer-properties I get an audible "test" beep, but that's it. No PA apps work...

mplayer -ao pulse gives silence (but in contrast with RB and QL, does count time at least)
mplayer -ao alsa gives sound.

Edit: So it's definitely pulse. I can play through ALSA in VLC, and even connect its stream to my bluetooth receiver via blueman/bluez, but as soon as I try a PA app (Rhythmbox, Quod Libet, Totem), total failure...

---

### Post by hugmenot on 2010-05-01
Why does it say STATE: SUSPENDED on the sinks in your pactl output?

You could try to restart PA in the foreground on the shell but that give you a lot of incomprehensible output to skim through (depending on how many -vvvv you slap behind it)


```
pulseaudio -k; pulseaudio --daemonize=no -v
```

Might take a few tries to get it to start in the foreground, because after the kill (-k) it immediately respawns, and this tries to get between the respawns.

---

### Post by hugmenot on 2010-05-01
Could it be that your pulseaudio package comes from some PPA?

My up-to-date Lucid install has version 

1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14


can you run 

```
apt-cache policy pulseaudio
```

---

### Post by peppot on 2010-05-01
Package is main repo.

pulse debug:

```

I: main.c: Detta är PulseAudio 0.9.21-63-gd3efa-dirty
I: main.c: Page size is 4096 bytes
I: main.c: Machine ID is 96ea5767ea6639ae0eaae94049cd171c.
I: main.c: Session ID is 96ea5767ea6639ae0eaae94049cd171c-1272710141.168959-909394282.
I: main.c: Using runtime directory /home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-runtime.
I: main.c: Using state directory /home/petter/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Kör i systemläge: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 SSE4_1 
I: svolume_mmx.c: Initialising MMX optimized functions.
I: remap_mmx.c: Initialising MMX optimized remappers.
I: svolume_sse.c: Initialising SSE2 optimized functions.
I: remap_sse.c: Initialising SSE2 optimized remappers.
I: sconv_sse.c: Initialising SSE2 optimized conversions.
I: module-device-restore.c: Sucessfully opened database file '/home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-device-volumes'.
I: module.c: Loaded "module-device-restore" (index: #0; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-stream-volumes'.
I: module.c: Loaded "module-stream-restore" (index: #1; argument: "").
I: module-card-restore.c: Sucessfully opened database file '/home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-card-database'.
I: module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #3; argument: "").
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround40:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround40:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround40:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround40:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround40:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround41:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround41:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround41:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround41:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround41:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround50:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround50:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround50:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround50:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround50:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround51:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround51:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround51:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround51:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround51:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround71:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround71:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround71:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround71:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround71:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1c failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1c failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1c failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1c failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: card.c: Created 0 "alsa_card.pci-0000_01_00.1"
I: alsa-sink.c: Successfully opened device hdmi:1.
I: alsa-sink.c: Selected mapping 'Digital Stereo (HDMI)' (hdmi-stereo).
I: alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL hdmi:1
I: alsa-mixer.c: Unable to attach to mixer hdmi:1: Filen eller katalogen finns inte
I: alsa-mixer.c: Successfully attached to mixer 'hw:1'
I: sink.c: Created sink 0 "alsa_output.pci-0000_01_00.1.hdmi-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     alsa.resolution_bits = "16"
I: sink.c:     device.api = "alsa"
I: sink.c:     device.class = "sound"
I: sink.c:     alsa.class = "generic"
I: sink.c:     alsa.subclass = "generic-mix"
I: sink.c:     alsa.name = "ATI HDMI"
I: sink.c:     alsa.id = "ATI HDMI"
I: sink.c:     alsa.subdevice = "0"
I: sink.c:     alsa.subdevice_name = "subdevice #0"
I: sink.c:     alsa.device = "3"
I: sink.c:     alsa.card = "1"
I: sink.c:     alsa.card_name = "HDA ATI HDMI"
I: sink.c:     alsa.long_card_name = "HDA ATI HDMI at 0xd0030000 irq 17"
I: sink.c:     alsa.driver_name = "snd_hda_intel"
I: sink.c:     device.bus_path = "pci-0000:01:00.1"
I: sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
I: sink.c:     device.bus = "pci"
I: sink.c:     device.vendor.id = "1002"
I: sink.c:     device.vendor.name = "ATI Technologies Inc"
I: sink.c:     device.product.id = "aa28"
I: sink.c:     device.product.name = "RV620 Audio device [Radeon HD 34xx Series]"
I: sink.c:     device.string = "hdmi:1"
I: sink.c:     device.buffering.buffer_size = "352768"
I: sink.c:     device.buffering.fragment_size = "176384"
I: sink.c:     device.access_mode = "mmap+timer"
I: sink.c:     device.profile.name = "hdmi-stereo"
I: sink.c:     device.profile.description = "Digital Stereo (HDMI)"
I: sink.c:     device.description = "RV620 Audio device [Radeon HD 34xx Series] Digital Stereo (HDMI)"
I: sink.c:     alsa.mixer_name = "ATI R6xx HDMI"
I: sink.c:     alsa.components = "HDA:1002aa01,104d2e00,00100000"
I: sink.c:     module-udev-detect.discovered = "1"
I: sink.c:     device.icon_name = "audio-card-pci"
I: source.c: Created source 0 "alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of RV620 Audio device [Radeon HD 34xx Series] Digital Stereo (HDMI)"
I: source.c:     device.class = "monitor"
I: source.c:     alsa.card = "1"
I: source.c:     alsa.card_name = "HDA ATI HDMI"
I: source.c:     alsa.long_card_name = "HDA ATI HDMI at 0xd0030000 irq 17"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:01:00.1"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "1002"
I: source.c:     device.vendor.name = "ATI Technologies Inc"
I: source.c:     device.product.id = "aa28"
I: source.c:     device.product.name = "RV620 Audio device [Radeon HD 34xx Series]"
I: source.c:     device.string = "1"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-sink.c: Using 2,0 fragments of size 176384 bytes (999,91ms), buffer size is 352768 bytes (1999,82ms)
I: alsa-sink.c: Time scheduling watermark is 20,00ms
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-card" (index: #4; argument: "device_id="1" name="pci-0000_01_00.1" card_name="alsa_card.pci-0000_01_00.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"").
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1 (alsa_card.pci-0000_01_00.1) module loaded.
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Ogiltigt argument
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: Filen eller katalogen finns inte
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: card.c: Created 1 "alsa_card.pci-0000_00_1b.0"
I: alsa-sink.c: Successfully opened device front:0.
I: alsa-sink.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-mixer.c: Unable to attach to mixer front:0: Filen eller katalogen finns inte
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
I: module-device-restore.c: Restoring port for sink sink:alsa_output.pci-0000_00_1b.0.analog-stereo.
I: module-device-restore.c: Restoring volume for sink alsa_output.pci-0000_00_1b.0.analog-stereo.
I: sink.c: Created sink 1 "alsa_output.pci-0000_00_1b.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     alsa.resolution_bits = "16"
I: sink.c:     device.api = "alsa"
I: sink.c:     device.class = "sound"
I: sink.c:     alsa.class = "generic"
I: sink.c:     alsa.subclass = "generic-mix"
I: sink.c:     alsa.name = "ALC262 Analog"
I: sink.c:     alsa.id = "ALC262 Analog"
I: sink.c:     alsa.subdevice = "0"
I: sink.c:     alsa.subdevice_name = "subdevice #0"
I: sink.c:     alsa.device = "0"
I: sink.c:     alsa.card = "0"
I: sink.c:     alsa.card_name = "HDA Intel"
I: sink.c:     alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
I: sink.c:     alsa.driver_name = "snd_hda_intel"
I: sink.c:     device.bus_path = "pci-0000:00:1b.0"
I: sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: sink.c:     device.bus = "pci"
I: sink.c:     device.vendor.id = "8086"
I: sink.c:     device.vendor.name = "Intel Corporation"
I: sink.c:     device.product.id = "293e"
I: sink.c:     device.product.name = "82801I (ICH9 Family) HD Audio Controller"
I: sink.c:     device.form_factor = "internal"
I: sink.c:     device.string = "front:0"
I: sink.c:     device.buffering.buffer_size = "352768"
I: sink.c:     device.buffering.fragment_size = "176384"
I: sink.c:     device.access_mode = "mmap+timer"
I: sink.c:     device.profile.name = "analog-stereo"
I: sink.c:     device.profile.description = "Analog Stereo"
I: sink.c:     device.description = "Internt ljud Analog Stereo"
I: sink.c:     alsa.mixer_name = "Realtek ALC262"
I: sink.c:     alsa.components = "HDA:10ec0262,104d2e00,00100302 HDA:14f12c06,104d1700,00100000"
I: sink.c:     module-udev-detect.discovered = "1"
I: sink.c:     device.icon_name = "audio-card-pci"
I: source.c: Created source 1 "alsa_output.pci-0000_00_1b.0.analog-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of Internt ljud Analog Stereo"
I: source.c:     device.class = "monitor"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA Intel"
I: source.c:     alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:00:1b.0"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "8086"
I: source.c:     device.vendor.name = "Intel Corporation"
I: source.c:     device.product.id = "293e"
I: source.c:     device.product.name = "82801I (ICH9 Family) HD Audio Controller"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "0"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-sink.c: Using 2,0 fragments of size 176384 bytes (999,91ms), buffer size is 352768 bytes (1999,82ms)
I: alsa-sink.c: Time scheduling watermark is 20,00ms
I: alsa-sink.c: Hardware volume ranges from -96,00 dB to 0,00 dB.
I: alsa-sink.c: No particular base volume set, fixing to 0 dB
I: alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-sink.c: Using hardware mute control.
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: alsa-sink.c: Starting playback.
I: alsa-source.c: Successfully opened device front:0.
I: alsa-source.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: alsa-source.c: Successfully enabled mmap() mode.
I: alsa-source.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-mixer.c: Unable to attach to mixer front:0: Filen eller katalogen finns inte
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
I: module-device-restore.c: Restoring mute state for source alsa_input.pci-0000_00_1b.0.analog-stereo.
I: source.c: Created source 2 "alsa_input.pci-0000_00_1b.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     alsa.resolution_bits = "16"
I: source.c:     device.api = "alsa"
I: source.c:     device.class = "sound"
I: source.c:     alsa.class = "generic"
I: source.c:     alsa.subclass = "generic-mix"
I: source.c:     alsa.name = "ALC262 Analog"
I: source.c:     alsa.id = "ALC262 Analog"
I: source.c:     alsa.subdevice = "0"
I: source.c:     alsa.subdevice_name = "subdevice #0"
I: source.c:     alsa.device = "0"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA Intel"
I: source.c:     alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:00:1b.0"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "8086"
I: source.c:     device.vendor.name = "Intel Corporation"
I: source.c:     device.product.id = "293e"
I: source.c:     device.product.name = "82801I (ICH9 Family) HD Audio Controller"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "front:0"
I: source.c:     device.buffering.buffer_size = "352768"
I: source.c:     device.buffering.fragment_size = "176384"
I: source.c:     device.access_mode = "mmap+timer"
I: source.c:     device.profile.name = "analog-stereo"
I: source.c:     device.profile.description = "Analog Stereo"
I: source.c:     device.description = "Internt ljud Analog Stereo"
I: source.c:     alsa.mixer_name = "Realtek ALC262"
I: source.c:     alsa.components = "HDA:10ec0262,104d2e00,00100302 HDA:14f12c06,104d1700,00100000"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-source.c: Using 2,0 fragments of size 176384 bytes (999,91ms), buffer size is 352768 bytes (1999,82ms)
I: alsa-source.c: Time scheduling watermark is 20,00ms
I: alsa-source.c: Hardware volume ranges from -12,00 dB to 34,50 dB.
I: alsa-source.c: Fixing base volume to -34,50 dB
I: alsa-source.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-source.c: Using hardware mute control.
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: module.c: Loaded "module-alsa-card" (index: #5; argument: "device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"").
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:1b.0/sound/card0 (alsa_card.pci-0000_00_1b.0) module loaded.
I: module-udev-detect.c: Found 2 cards.
I: module.c: Loaded "module-udev-detect" (index: #6; argument: "").
I: card.c: Created 2 "bluez_card.00_02_72_E6_C7_08"
I: module-bluetooth-device.c: SBC parameters:
I: module-bluetooth-device.c: 	allocation=0
I: module-bluetooth-device.c: 	subbands=1
I: module-bluetooth-device.c: 	blocks=3
I: module-bluetooth-device.c: 	bitpool=53
I: module-device-restore.c: Restoring volume for sink bluez_sink.00_02_72_E6_C7_08.
I: sink.c: Created sink 2 "bluez_sink.00_02_72_E6_C7_08" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     bluetooth.protocol = "a2dp"
I: sink.c:     device.description = "Belkin H95"
I: sink.c:     device.string = "00:02:72:E6:C7:08"
I: sink.c:     device.api = "bluez"
I: sink.c:     device.class = "sound"
I: sink.c:     device.bus = "bluetooth"
I: sink.c:     device.form_factor = "headset"
I: sink.c:     bluez.path = "/org/bluez/1265/hci0/dev_00_02_72_E6_C7_08"
I: sink.c:     bluez.class = "0x240404"
I: sink.c:     bluez.name = "Belkin H95"
I: sink.c:     device.icon_name = "audio-headset-bluetooth"
I: source.c: Created source 3 "bluez_sink.00_02_72_E6_C7_08.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of Belkin H95"
I: source.c:     device.class = "monitor"
I: source.c:     device.string = "00:02:72:E6:C7:08"
I: source.c:     device.api = "bluez"
I: source.c:     device.bus = "bluetooth"
I: source.c:     device.form_factor = "headset"
I: source.c:     bluez.path = "/org/bluez/1265/hci0/dev_00_02_72_E6_C7_08"
I: source.c:     bluez.class = "0x240404"
I: source.c:     bluez.name = "Belkin H95"
I: source.c:     device.icon_name = "audio-headset-bluetooth"
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: module.c: Loaded "module-bluetooth-device" (index: #7; argument: "address="00:02:72:E6:C7:08" path="/org/bluez/1265/hci0/dev_00_02_72_E6_C7_08"").
I: module.c: Loaded "module-bluetooth-discover" (index: #8; argument: "").
I: module.c: Loaded "module-esound-protocol-unix" (index: #9; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #10; argument: "").
I: module.c: Loaded "module-gconf" (index: #11; argument: "").
I: module-default-device-restore.c: No previous default sink setting, ignoring.
I: module-default-device-restore.c: No previous default source setting, ignoring.
I: module.c: Loaded "module-default-device-restore" (index: #12; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #13; argument: "").
I: module.c: Loaded "module-always-sink" (index: #14; argument: "").
I: module.c: Loaded "module-intended-roles" (index: #15; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #16; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
I: module.c: Loaded "module-console-kit" (index: #17; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #18; argument: "").
I: main.c: Daemon startup complete.
I: client.c: Created 1 "Native client (UNIX socket client)"
I: client.c: Created 2 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: client.c: Created 3 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: client.c: Created 4 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: module-suspend-on-idle.c: Source alsa_input.pci-0000_00_1b.0.analog-stereo idle for too long, suspending ...
I: alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Sink bluez_sink.00_02_72_E6_C7_08 idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo idle for too long, suspending ...
I: alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci-0000_01_00.1.hdmi-stereo idle for too long, suspending ...
I: alsa-sink.c: Device suspended...
I: client.c: Created 5 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: client.c: Freed 5 "Rhythmbox"
I: protocol-native.c: Connection died.
I: client.c: Created 6 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: client.c: Freed 6 "Rhythmbox"
I: protocol-native.c: Connection died.

```

And that's starting it and trying to play music twice in RB.

---

### Post by jacksonpollack on 2010-05-01
Not sure if this is related, but there seems to be a problem with HDA Intel in Lucid. Many people seem to have no sound.

See here:
[http://ubuntuforums.org/showthread.php?p=9212102#post9212102](http://ubuntuforums.org/showthread.php?p=9212102#post9212102)

Some solutions have been suggested, some have apparently worked (not for me though!).

---

### Post by peppot on 2010-05-01
Unfortunately none of those solutions apply

---

### Post by wintmulder on 2010-05-01
> **peppot said:**
> Unfortunately none of those solutions apply
and so the problem exists plz.... help us with the good working sollution :KS
grtsz.
just a beginner

---

### Post by hugmenot on 2010-05-01
Can you run again and use five -vvvvv?

---

### Post by wintmulder on 2010-05-01
> **wintmulder said:**
> and so the problem exists plz.... help us with the good working sollution :KS
grtsz.
just a beginner
(IR) issue solved :lolflag:
after reinstalll asla lib

---

### Post by peppot on 2010-05-02
Sure. Here goes:

```


I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) misslyckades: Operationen inte tillåten
I: core-util.c: Successfully gained nice level -11.
I: main.c: Detta är PulseAudio 0.9.21-63-gd3efa-dirty
I: main.c: Page size is 4096 bytes
I: main.c: Machine ID is 96ea5767ea6639ae0eaae94049cd171c.
I: main.c: Session ID is 96ea5767ea6639ae0eaae94049cd171c-1272710141.168959-909394282.
I: main.c: Using runtime directory /home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-runtime.
I: main.c: Using state directory /home/petter/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Kör i systemläge: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() misslyckades.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) misslyckades: Operationen inte tillåten
I: core-util.c: Successfully gained nice level -11.
I: main.c: Detta är PulseAudio 0.9.21-63-gd3efa-dirty
I: main.c: Page size is 4096 bytes
I: main.c: Machine ID is 96ea5767ea6639ae0eaae94049cd171c.
I: main.c: Session ID is 96ea5767ea6639ae0eaae94049cd171c-1272710141.168959-909394282.
I: main.c: Using runtime directory /home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-runtime.
I: main.c: Using state directory /home/petter/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Kör i systemläge: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() misslyckades.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) misslyckades: Operationen inte tillåten
I: core-util.c: Successfully gained nice level -11.
I: main.c: Detta är PulseAudio 0.9.21-63-gd3efa-dirty
I: main.c: Page size is 4096 bytes
I: main.c: Machine ID is 96ea5767ea6639ae0eaae94049cd171c.
I: main.c: Session ID is 96ea5767ea6639ae0eaae94049cd171c-1272710141.168959-909394282.
I: main.c: Using runtime directory /home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-runtime.
I: main.c: Using state directory /home/petter/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Kör i systemläge: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() misslyckades.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) misslyckades: Operationen inte tillåten
I: core-util.c: Successfully gained nice level -11.
I: main.c: Detta är PulseAudio 0.9.21-63-gd3efa-dirty
I: main.c: Page size is 4096 bytes
I: main.c: Machine ID is 96ea5767ea6639ae0eaae94049cd171c.
I: main.c: Session ID is 96ea5767ea6639ae0eaae94049cd171c-1272710141.168959-909394282.
I: main.c: Using runtime directory /home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-runtime.
I: main.c: Using state directory /home/petter/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Kör i systemläge: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() misslyckades.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) misslyckades: Operationen inte tillåten
I: core-util.c: Failed to acquire high-priority scheduling: Åtkomst nekas
I: main.c: Detta är PulseAudio 0.9.21-63-gd3efa-dirty
I: main.c: Page size is 4096 bytes
I: main.c: Machine ID is 96ea5767ea6639ae0eaae94049cd171c.
I: main.c: Session ID is 96ea5767ea6639ae0eaae94049cd171c-1272710141.168959-909394282.
I: main.c: Using runtime directory /home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-runtime.
I: main.c: Using state directory /home/petter/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Kör i systemläge: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 SSE4_1 
I: svolume_mmx.c: Initialising MMX optimized functions.
I: remap_mmx.c: Initialising MMX optimized remappers.
I: svolume_sse.c: Initialising SSE2 optimized functions.
I: remap_sse.c: Initialising SSE2 optimized remappers.
I: sconv_sse.c: Initialising SSE2 optimized conversions.
I: module-device-restore.c: Sucessfully opened database file '/home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-device-volumes'.
I: module.c: Loaded "module-device-restore" (index: #0; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-stream-volumes'.
I: module.c: Loaded "module-stream-restore" (index: #1; argument: "").
I: module-card-restore.c: Sucessfully opened database file '/home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-card-database'.
I: module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #3; argument: "").
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround40:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround40:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround40:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround40:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround40:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround41:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround41:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround41:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround41:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround41:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround50:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround50:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround50:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround50:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround50:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround51:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround51:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround51:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround51:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround51:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround71:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround71:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround71:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround71:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround71:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1c failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1c failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1c failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1c failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: card.c: Created 0 "alsa_card.pci-0000_01_00.1"
I: alsa-sink.c: Successfully opened device hdmi:1.
I: alsa-sink.c: Selected mapping 'Digital Stereo (HDMI)' (hdmi-stereo).
I: alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL hdmi:1
I: alsa-mixer.c: Unable to attach to mixer hdmi:1: Filen eller katalogen finns inte
I: alsa-mixer.c: Successfully attached to mixer 'hw:1'
I: sink.c: Created sink 0 "alsa_output.pci-0000_01_00.1.hdmi-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     alsa.resolution_bits = "16"
I: sink.c:     device.api = "alsa"
I: sink.c:     device.class = "sound"
I: sink.c:     alsa.class = "generic"
I: sink.c:     alsa.subclass = "generic-mix"
I: sink.c:     alsa.name = "ATI HDMI"
I: sink.c:     alsa.id = "ATI HDMI"
I: sink.c:     alsa.subdevice = "0"
I: sink.c:     alsa.subdevice_name = "subdevice #0"
I: sink.c:     alsa.device = "3"
I: sink.c:     alsa.card = "1"
I: sink.c:     alsa.card_name = "HDA ATI HDMI"
I: sink.c:     alsa.long_card_name = "HDA ATI HDMI at 0xd0030000 irq 17"
I: sink.c:     alsa.driver_name = "snd_hda_intel"
I: sink.c:     device.bus_path = "pci-0000:01:00.1"
I: sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
I: sink.c:     device.bus = "pci"
I: sink.c:     device.vendor.id = "1002"
I: sink.c:     device.vendor.name = "ATI Technologies Inc"
I: sink.c:     device.product.id = "aa28"
I: sink.c:     device.product.name = "RV620 Audio device [Radeon HD 34xx Series]"
I: sink.c:     device.string = "hdmi:1"
I: sink.c:     device.buffering.buffer_size = "352768"
I: sink.c:     device.buffering.fragment_size = "176384"
I: sink.c:     device.access_mode = "mmap+timer"
I: sink.c:     device.profile.name = "hdmi-stereo"
I: sink.c:     device.profile.description = "Digital Stereo (HDMI)"
I: sink.c:     device.description = "RV620 Audio device [Radeon HD 34xx Series] Digital Stereo (HDMI)"
I: sink.c:     alsa.mixer_name = "ATI R6xx HDMI"
I: sink.c:     alsa.components = "HDA:1002aa01,104d2e00,00100000"
I: sink.c:     module-udev-detect.discovered = "1"
I: sink.c:     device.icon_name = "audio-card-pci"
I: source.c: Created source 0 "alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of RV620 Audio device [Radeon HD 34xx Series] Digital Stereo (HDMI)"
I: source.c:     device.class = "monitor"
I: source.c:     alsa.card = "1"
I: source.c:     alsa.card_name = "HDA ATI HDMI"
I: source.c:     alsa.long_card_name = "HDA ATI HDMI at 0xd0030000 irq 17"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:01:00.1"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "1002"
I: source.c:     device.vendor.name = "ATI Technologies Inc"
I: source.c:     device.product.id = "aa28"
I: source.c:     device.product.name = "RV620 Audio device [Radeon HD 34xx Series]"
I: source.c:     device.string = "1"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-sink.c: Using 2,0 fragments of size 176384 bytes (999,91ms), buffer size is 352768 bytes (1999,82ms)
I: alsa-sink.c: Time scheduling watermark is 20,00ms
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-card" (index: #4; argument: "device_id="1" name="pci-0000_01_00.1" card_name="alsa_card.pci-0000_01_00.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"").
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1 (alsa_card.pci-0000_01_00.1) module loaded.
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Ogiltigt argument
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Ogiltigt argument
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: Filen eller katalogen finns inte
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: card.c: Created 1 "alsa_card.pci-0000_00_1b.0"
I: alsa-sink.c: Successfully opened device front:0.
I: alsa-sink.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-mixer.c: Unable to attach to mixer front:0: Filen eller katalogen finns inte
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
I: module-device-restore.c: Restoring port for sink sink:alsa_output.pci-0000_00_1b.0.analog-stereo.
I: module-device-restore.c: Restoring volume for sink alsa_output.pci-0000_00_1b.0.analog-stereo.
I: sink.c: Created sink 1 "alsa_output.pci-0000_00_1b.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     alsa.resolution_bits = "16"
I: sink.c:     device.api = "alsa"
I: sink.c:     device.class = "sound"
I: sink.c:     alsa.class = "generic"
I: sink.c:     alsa.subclass = "generic-mix"
I: sink.c:     alsa.name = "ALC262 Analog"
I: sink.c:     alsa.id = "ALC262 Analog"
I: sink.c:     alsa.subdevice = "0"
I: sink.c:     alsa.subdevice_name = "subdevice #0"
I: sink.c:     alsa.device = "0"
I: sink.c:     alsa.card = "0"
I: sink.c:     alsa.card_name = "HDA Intel"
I: sink.c:     alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
I: sink.c:     alsa.driver_name = "snd_hda_intel"
I: sink.c:     device.bus_path = "pci-0000:00:1b.0"
I: sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: sink.c:     device.bus = "pci"
I: sink.c:     device.vendor.id = "8086"
I: sink.c:     device.vendor.name = "Intel Corporation"
I: sink.c:     device.product.id = "293e"
I: sink.c:     device.product.name = "82801I (ICH9 Family) HD Audio Controller"
I: sink.c:     device.form_factor = "internal"
I: sink.c:     device.string = "front:0"
I: sink.c:     device.buffering.buffer_size = "352768"
I: sink.c:     device.buffering.fragment_size = "176384"
I: sink.c:     device.access_mode = "mmap+timer"
I: sink.c:     device.profile.name = "analog-stereo"
I: sink.c:     device.profile.description = "Analog Stereo"
I: sink.c:     device.description = "Internt ljud Analog Stereo"
I: sink.c:     alsa.mixer_name = "Realtek ALC262"
I: sink.c:     alsa.components = "HDA:10ec0262,104d2e00,00100302 HDA:14f12c06,104d1700,00100000"
I: sink.c:     module-udev-detect.discovered = "1"
I: sink.c:     device.icon_name = "audio-card-pci"
I: source.c: Created source 1 "alsa_output.pci-0000_00_1b.0.analog-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of Internt ljud Analog Stereo"
I: source.c:     device.class = "monitor"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA Intel"
I: source.c:     alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:00:1b.0"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "8086"
I: source.c:     device.vendor.name = "Intel Corporation"
I: source.c:     device.product.id = "293e"
I: source.c:     device.product.name = "82801I (ICH9 Family) HD Audio Controller"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "0"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-sink.c: Using 2,0 fragments of size 176384 bytes (999,91ms), buffer size is 352768 bytes (1999,82ms)
I: alsa-sink.c: Time scheduling watermark is 20,00ms
I: alsa-sink.c: Hardware volume ranges from -96,00 dB to 0,00 dB.
I: alsa-sink.c: No particular base volume set, fixing to 0 dB
I: alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-sink.c: Using hardware mute control.
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: alsa-sink.c: Starting playback.
I: alsa-source.c: Successfully opened device front:0.
I: alsa-source.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: alsa-source.c: Successfully enabled mmap() mode.
I: alsa-source.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-mixer.c: Unable to attach to mixer front:0: Filen eller katalogen finns inte
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
I: module-device-restore.c: Restoring mute state for source alsa_input.pci-0000_00_1b.0.analog-stereo.
I: source.c: Created source 2 "alsa_input.pci-0000_00_1b.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     alsa.resolution_bits = "16"
I: source.c:     device.api = "alsa"
I: source.c:     device.class = "sound"
I: source.c:     alsa.class = "generic"
I: source.c:     alsa.subclass = "generic-mix"
I: source.c:     alsa.name = "ALC262 Analog"
I: source.c:     alsa.id = "ALC262 Analog"
I: source.c:     alsa.subdevice = "0"
I: source.c:     alsa.subdevice_name = "subdevice #0"
I: source.c:     alsa.device = "0"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA Intel"
I: source.c:     alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:00:1b.0"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "8086"
I: source.c:     device.vendor.name = "Intel Corporation"
I: source.c:     device.product.id = "293e"
I: source.c:     device.product.name = "82801I (ICH9 Family) HD Audio Controller"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "front:0"
I: source.c:     device.buffering.buffer_size = "352768"
I: source.c:     device.buffering.fragment_size = "176384"
I: source.c:     device.access_mode = "mmap+timer"
I: source.c:     device.profile.name = "analog-stereo"
I: source.c:     device.profile.description = "Analog Stereo"
I: source.c:     device.description = "Internt ljud Analog Stereo"
I: source.c:     alsa.mixer_name = "Realtek ALC262"
I: source.c:     alsa.components = "HDA:10ec0262,104d2e00,00100302 HDA:14f12c06,104d1700,00100000"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-source.c: Using 2,0 fragments of size 176384 bytes (999,91ms), buffer size is 352768 bytes (1999,82ms)
I: alsa-source.c: Time scheduling watermark is 20,00ms
I: alsa-source.c: Hardware volume ranges from -12,00 dB to 34,50 dB.
I: alsa-source.c: Fixing base volume to -34,50 dB
I: alsa-source.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-source.c: Using hardware mute control.
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: module.c: Loaded "module-alsa-card" (index: #5; argument: "device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"").
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:1b.0/sound/card0 (alsa_card.pci-0000_00_1b.0) module loaded.
I: module-udev-detect.c: Found 2 cards.
I: module.c: Loaded "module-udev-detect" (index: #6; argument: "").
I: card.c: Created 2 "bluez_card.00_02_72_E6_C7_08"
I: module-bluetooth-device.c: SBC parameters:
I: module-bluetooth-device.c: 	allocation=0
I: module-bluetooth-device.c: 	subbands=1
I: module-bluetooth-device.c: 	blocks=3
I: module-bluetooth-device.c: 	bitpool=53
I: module-device-restore.c: Restoring volume for sink bluez_sink.00_02_72_E6_C7_08.
I: sink.c: Created sink 2 "bluez_sink.00_02_72_E6_C7_08" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     bluetooth.protocol = "a2dp"
I: sink.c:     device.description = "Belkin H95"
I: sink.c:     device.string = "00:02:72:E6:C7:08"
I: sink.c:     device.api = "bluez"
I: sink.c:     device.class = "sound"
I: sink.c:     device.bus = "bluetooth"
I: sink.c:     device.form_factor = "headset"
I: sink.c:     bluez.path = "/org/bluez/1265/hci0/dev_00_02_72_E6_C7_08"
I: sink.c:     bluez.class = "0x240404"
I: sink.c:     bluez.name = "Belkin H95"
I: sink.c:     device.icon_name = "audio-headset-bluetooth"
I: source.c: Created source 3 "bluez_sink.00_02_72_E6_C7_08.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of Belkin H95"
I: source.c:     device.class = "monitor"
I: source.c:     device.string = "00:02:72:E6:C7:08"
I: source.c:     device.api = "bluez"
I: source.c:     device.bus = "bluetooth"
I: source.c:     device.form_factor = "headset"
I: source.c:     bluez.path = "/org/bluez/1265/hci0/dev_00_02_72_E6_C7_08"
I: source.c:     bluez.class = "0x240404"
I: source.c:     bluez.name = "Belkin H95"
I: source.c:     device.icon_name = "audio-headset-bluetooth"
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: module.c: Loaded "module-bluetooth-device" (index: #7; argument: "address="00:02:72:E6:C7:08" path="/org/bluez/1265/hci0/dev_00_02_72_E6_C7_08"").
I: module.c: Loaded "module-bluetooth-discover" (index: #8; argument: "").
I: module.c: Loaded "module-esound-protocol-unix" (index: #9; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #10; argument: "").
I: module.c: Loaded "module-gconf" (index: #11; argument: "").
I: module-default-device-restore.c: No previous default sink setting, ignoring.
I: module-default-device-restore.c: No previous default source setting, ignoring.
I: module.c: Loaded "module-default-device-restore" (index: #12; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #13; argument: "").
I: module.c: Loaded "module-always-sink" (index: #14; argument: "").
I: module.c: Loaded "module-intended-roles" (index: #15; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #16; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
I: module.c: Loaded "module-console-kit" (index: #17; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #18; argument: "").
I: main.c: Daemon startup complete.
I: client.c: Created 1 "Native client (UNIX socket client)"
I: client.c: Created 2 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: client.c: Created 3 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: client.c: Created 4 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: module-suspend-on-idle.c: Source alsa_input.pci-0000_00_1b.0.analog-stereo idle for too long, suspending ...
I: alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Sink bluez_sink.00_02_72_E6_C7_08 idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo idle for too long, suspending ...
I: alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci-0000_01_00.1.hdmi-stereo idle for too long, suspending ...
I: alsa-sink.c: Device suspended...
I: client.c: Created 5 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: client.c: Freed 5 "Rhythmbox"
I: protocol-native.c: Connection died.
I: client.c: Created 6 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: client.c: Freed 6 "Rhythmbox"
I: protocol-native.c: Connection died.
I: main.c: Fick signal SIGHUP.
N: main.c: 3 sink(s) available.
N: main.c:     index: 0
N: main.c: 	name: <alsa_output.pci-0000_01_00.1.hdmi-stereo>
N: main.c: 	driver: <module-alsa-card.c>
N: main.c: 	flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
N: main.c: 	state: SUSPENDED
N: main.c: 	suspend cause: IDLE 
N: main.c: 	priority: 9050
N: main.c: 	volume: 0: 100% 1: 100%
N: main.c: 	        0: 0,00 dB 1: 0,00 dB
N: main.c: 	        balance 0,00
N: main.c: 	base volume: 100%
N: main.c: 	             0,00 dB
N: main.c: 	volume steps: 65537
N: main.c: 	muted: no
N: main.c: 	current latency: 0,00 ms
N: main.c: 	max request: 0 KiB
N: main.c: 	max rewind: 0 KiB
N: main.c: 	monitor source: 0
N: main.c: 	sample spec: s16le 2ch 44100Hz
N: main.c: 	channel map: front-left,front-right
N: main.c: 	             Stereo
N: main.c: 	used by: 0
N: main.c: 	linked by: 0
N: main.c: 	configured latency: 0,00 ms; range is 0,50 .. 1999,82 ms
N: main.c: 	card: 0 <alsa_card.pci-0000_01_00.1>
N: main.c: 	module: 4
N: main.c: 	properties:
N: main.c: 		alsa.resolution_bits = "16"
N: main.c: 		device.api = "alsa"
N: main.c: 		device.class = "sound"
N: main.c: 		alsa.class = "generic"
N: main.c: 		alsa.subclass = "generic-mix"
N: main.c: 		alsa.name = "ATI HDMI"
N: main.c: 		alsa.id = "ATI HDMI"
N: main.c: 		alsa.subdevice = "0"
N: main.c: 		alsa.subdevice_name = "subdevice #0"
N: main.c: 		alsa.device = "3"
N: main.c: 		alsa.card = "1"
N: main.c: 		alsa.card_name = "HDA ATI HDMI"
N: main.c: 		alsa.long_card_name = "HDA ATI HDMI at 0xd0030000 irq 17"
N: main.c: 		alsa.driver_name = "snd_hda_intel"
N: main.c: 		device.bus_path = "pci-0000:01:00.1"
N: main.c: 		sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
N: main.c: 		device.bus = "pci"
N: main.c: 		device.vendor.id = "1002"
N: main.c: 		device.vendor.name = "ATI Technologies Inc"
N: main.c: 		device.product.id = "aa28"
N: main.c: 		device.product.name = "RV620 Audio device [Radeon HD 34xx Series]"
N: main.c: 		device.string = "hdmi:1"
N: main.c: 		device.buffering.buffer_size = "352768"
N: main.c: 		device.buffering.fragment_size = "176384"
N: main.c: 		device.access_mode = "mmap+timer"
N: main.c: 		device.profile.name = "hdmi-stereo"
N: main.c: 		device.profile.description = "Digital Stereo (HDMI)"
N: main.c: 		device.description = "RV620 Audio device [Radeon HD 34xx Series] Digital Stereo (HDMI)"
N: main.c: 		alsa.mixer_name = "ATI R6xx HDMI"
N: main.c: 		alsa.components = "HDA:1002aa01,104d2e00,00100000"
N: main.c: 		module-udev-detect.discovered = "1"
N: main.c: 		device.icon_name = "audio-card-pci"
N: main.c:   * index: 1
N: main.c: 	name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
N: main.c: 	driver: <module-alsa-card.c>
N: main.c: 	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
N: main.c: 	state: SUSPENDED
N: main.c: 	suspend cause: IDLE 
N: main.c: 	priority: 9959
N: main.c: 	volume: 0:  45% 1:  45%
N: main.c: 	        0: -20,87 dB 1: -20,87 dB
N: main.c: 	        balance 0,00
N: main.c: 	base volume: 100%
N: main.c: 	             0,00 dB
N: main.c: 	volume steps: 65537
N: main.c: 	muted: no
N: main.c: 	current latency: 0,00 ms
N: main.c: 	max request: 0 KiB
N: main.c: 	max rewind: 0 KiB
N: main.c: 	monitor source: 1
N: main.c: 	sample spec: s16le 2ch 44100Hz
N: main.c: 	channel map: front-left,front-right
N: main.c: 	             Stereo
N: main.c: 	used by: 0
N: main.c: 	linked by: 0
N: main.c: 	configured latency: 0,00 ms; range is 0,50 .. 1999,82 ms
N: main.c: 	card: 1 <alsa_card.pci-0000_00_1b.0>
N: main.c: 	module: 5
N: main.c: 	properties:
N: main.c: 		alsa.resolution_bits = "16"
N: main.c: 		device.api = "alsa"
N: main.c: 		device.class = "sound"
N: main.c: 		alsa.class = "generic"
N: main.c: 		alsa.subclass = "generic-mix"
N: main.c: 		alsa.name = "ALC262 Analog"
N: main.c: 		alsa.id = "ALC262 Analog"
N: main.c: 		alsa.subdevice = "0"
N: main.c: 		alsa.subdevice_name = "subdevice #0"
N: main.c: 		alsa.device = "0"
N: main.c: 		alsa.card = "0"
N: main.c: 		alsa.card_name = "HDA Intel"
N: main.c: 		alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
N: main.c: 		alsa.driver_name = "snd_hda_intel"
N: main.c: 		device.bus_path = "pci-0000:00:1b.0"
N: main.c: 		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
N: main.c: 		device.bus = "pci"
N: main.c: 		device.vendor.id = "8086"
N: main.c: 		device.vendor.name = "Intel Corporation"
N: main.c: 		device.product.id = "293e"
N: main.c: 		device.product.name = "82801I (ICH9 Family) HD Audio Controller"
N: main.c: 		device.form_factor = "internal"
N: main.c: 		device.string = "front:0"
N: main.c: 		device.buffering.buffer_size = "352768"
N: main.c: 		device.buffering.fragment_size = "176384"
N: main.c: 		device.access_mode = "mmap+timer"
N: main.c: 		device.profile.name = "analog-stereo"
N: main.c: 		device.profile.description = "Analog Stereo"
N: main.c: 		device.description = "Internt ljud Analog Stereo"
N: main.c: 		alsa.mixer_name = "Realtek ALC262"
N: main.c: 		alsa.components = "HDA:10ec0262,104d2e00,00100302 HDA:14f12c06,104d1700,00100000"
N: main.c: 		module-udev-detect.discovered = "1"
N: main.c: 		device.icon_name = "audio-card-pci"
N: main.c: 	ports:
N: main.c: 		analog-output: Analog Output (priority 9900)
N: main.c: 		analog-output-speaker: Analog Speakers (priority 10000)
N: main.c: 		analog-output-headphones: Analog Headphones (priority 9000)
N: main.c: 	active port: <analog-output-speaker>
N: main.c:     index: 2
N: main.c: 	name: <bluez_sink.00_02_72_E6_C7_08>
N: main.c: 	driver: <module-bluetooth-device.c>
N: main.c: 	flags: HARDWARE DECIBEL_VOLUME LATENCY 
N: main.c: 	state: SUSPENDED
N: main.c: 	suspend cause: IDLE 
N: main.c: 	priority: 9030
N: main.c: 	volume: 0:  70% 1:  70%
N: main.c: 	        0: -9,29 dB 1: -9,29 dB
N: main.c: 	        balance 0,00
N: main.c: 	base volume: 100%
N: main.c: 	             0,00 dB
N: main.c: 	volume steps: 65537
N: main.c: 	muted: no
N: main.c: 	current latency: 0,00 ms
N: main.c: 	max request: 3 KiB
N: main.c: 	max rewind: 0 KiB
N: main.c: 	monitor source: 3
N: main.c: 	sample spec: s16le 2ch 44100Hz
N: main.c: 	channel map: front-left,front-right
N: main.c: 	             Stereo
N: main.c: 	used by: 0
N: main.c: 	linked by: 0
N: main.c: 	fixed latency: 45,32 ms
N: main.c: 	card: 2 <bluez_card.00_02_72_E6_C7_08>
N: main.c: 	module: 7
N: main.c: 	properties:
N: main.c: 		bluetooth.protocol = "a2dp"
N: main.c: 		device.description = "Belkin H95"
N: main.c: 		device.string = "00:02:72:E6:C7:08"
N: main.c: 		device.api = "bluez"
N: main.c: 		device.class = "sound"
N: main.c: 		device.bus = "bluetooth"
N: main.c: 		device.form_factor = "headset"
N: main.c: 		bluez.path = "/org/bluez/1265/hci0/dev_00_02_72_E6_C7_08"
N: main.c: 		bluez.class = "0x240404"
N: main.c: 		bluez.name = "Belkin H95"
N: main.c: 		device.icon_name = "audio-headset-bluetooth"
N: main.c: 4 source(s) available.
N: main.c:     index: 0
N: main.c: 	name: <alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor>
N: main.c: 	driver: <module-alsa-card.c>
N: main.c: 	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
N: main.c: 	state: SUSPENDED
N: main.c: 	suspend cause: IDLE 
N: main.c: 	priority: 1050
N: main.c: 	volume: 0: 100% 1: 100%
N: main.c: 	        0: 0,00 dB 1: 0,00 dB
N: main.c: 	        balance 0,00
N: main.c: 	base volume: 100%
N: main.c: 	             0,00 dB
N: main.c: 	volume steps: 65537
N: main.c: 	muted: no
N: main.c: 	current latency: 0,00 ms
N: main.c: 	max rewind: 0 KiB
N: main.c: 	sample spec: s16le 2ch 44100Hz
N: main.c: 	channel map: front-left,front-right
N: main.c: 	             Stereo
N: main.c: 	used by: 0
N: main.c: 	linked by: 0
N: main.c: 	configured latency: 0,00 ms; range is 0,50 .. 1999,82 ms
N: main.c: 	monitor_of: 0
N: main.c: 	card: 0 <alsa_card.pci-0000_01_00.1>
N: main.c: 	module: 4
N: main.c: 	properties:
N: main.c: 		device.description = "Monitor of RV620 Audio device [Radeon HD 34xx Series] Digital Stereo (HDMI)"
N: main.c: 		device.class = "monitor"
N: main.c: 		alsa.card = "1"
N: main.c: 		alsa.card_name = "HDA ATI HDMI"
N: main.c: 		alsa.long_card_name = "HDA ATI HDMI at 0xd0030000 irq 17"
N: main.c: 		alsa.driver_name = "snd_hda_intel"
N: main.c: 		device.bus_path = "pci-0000:01:00.1"
N: main.c: 		sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
N: main.c: 		device.bus = "pci"
N: main.c: 		device.vendor.id = "1002"
N: main.c: 		device.vendor.name = "ATI Technologies Inc"
N: main.c: 		device.product.id = "aa28"
N: main.c: 		device.product.name = "RV620 Audio device [Radeon HD 34xx Series]"
N: main.c: 		device.string = "1"
N: main.c: 		module-udev-detect.discovered = "1"
N: main.c: 		device.icon_name = "audio-card-pci"
N: main.c:     index: 1
N: main.c: 	name: <alsa_output.pci-0000_00_1b.0.analog-stereo.monitor>
N: main.c: 	driver: <module-alsa-card.c>
N: main.c: 	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
N: main.c: 	state: SUSPENDED
N: main.c: 	suspend cause: IDLE 
N: main.c: 	priority: 1950
N: main.c: 	volume: 0: 100% 1: 100%
N: main.c: 	        0: 0,00 dB 1: 0,00 dB
N: main.c: 	        balance 0,00
N: main.c: 	base volume: 100%
N: main.c: 	             0,00 dB
N: main.c: 	volume steps: 65537
N: main.c: 	muted: no
N: main.c: 	current latency: 0,00 ms
N: main.c: 	max rewind: 0 KiB
N: main.c: 	sample spec: s16le 2ch 44100Hz
N: main.c: 	channel map: front-left,front-right
N: main.c: 	             Stereo
N: main.c: 	used by: 0
N: main.c: 	linked by: 0
N: main.c: 	configured latency: 0,00 ms; range is 0,50 .. 1999,82 ms
N: main.c: 	monitor_of: 1
N: main.c: 	card: 1 <alsa_card.pci-0000_00_1b.0>
N: main.c: 	module: 5
N: main.c: 	properties:
N: main.c: 		device.description = "Monitor of Internt ljud Analog Stereo"
N: main.c: 		device.class = "monitor"
N: main.c: 		alsa.card = "0"
N: main.c: 		alsa.card_name = "HDA Intel"
N: main.c: 		alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
N: main.c: 		alsa.driver_name = "snd_hda_intel"
N: main.c: 		device.bus_path = "pci-0000:00:1b.0"
N: main.c: 		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
N: main.c: 		device.bus = "pci"
N: main.c: 		device.vendor.id = "8086"
N: main.c: 		device.vendor.name = "Intel Corporation"
N: main.c: 		device.product.id = "293e"
N: main.c: 		device.product.name = "82801I (ICH9 Family) HD Audio Controller"
N: main.c: 		device.form_factor = "internal"
N: main.c: 		device.string = "0"
N: main.c: 		module-udev-detect.discovered = "1"
N: main.c: 		device.icon_name = "audio-card-pci"
N: main.c:   * index: 2
N: main.c: 	name: <alsa_input.pci-0000_00_1b.0.analog-stereo>
N: main.c: 	driver: <module-alsa-card.c>
N: main.c: 	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
N: main.c: 	state: SUSPENDED
N: main.c: 	suspend cause: IDLE 
N: main.c: 	priority: 9959
N: main.c: 	volume: 0:  17% 1:  17%
N: main.c: 	        0: -46,50 dB 1: -46,50 dB
N: main.c: 	        balance 0,00
N: main.c: 	base volume:  27%
N: main.c: 	             -34,50 dB
N: main.c: 	volume steps: 65537
N: main.c: 	muted: yes
N: main.c: 	current latency: 0,00 ms
N: main.c: 	max rewind: 0 KiB
N: main.c: 	sample spec: s16le 2ch 44100Hz
N: main.c: 	channel map: front-left,front-right
N: main.c: 	             Stereo
N: main.c: 	used by: 0
N: main.c: 	linked by: 0
N: main.c: 	configured latency: 0,00 ms; range is 0,50 .. 1999,82 ms
N: main.c: 	card: 1 <alsa_card.pci-0000_00_1b.0>
N: main.c: 	module: 5
N: main.c: 	properties:
N: main.c: 		alsa.resolution_bits = "16"
N: main.c: 		device.api = "alsa"
N: main.c: 		device.class = "sound"
N: main.c: 		alsa.class = "generic"
N: main.c: 		alsa.subclass = "generic-mix"
N: main.c: 		alsa.name = "ALC262 Analog"
N: main.c: 		alsa.id = "ALC262 Analog"
N: main.c: 		alsa.subdevice = "0"
N: main.c: 		alsa.subdevice_name = "subdevice #0"
N: main.c: 		alsa.device = "0"
N: main.c: 		alsa.card = "0"
N: main.c: 		alsa.card_name = "HDA Intel"
N: main.c: 		alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
N: main.c: 		alsa.driver_name = "snd_hda_intel"
N: main.c: 		device.bus_path = "pci-0000:00:1b.0"
N: main.c: 		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
N: main.c: 		device.bus = "pci"
N: main.c: 		device.vendor.id = "8086"
N: main.c: 		device.vendor.name = "Intel Corporation"
N: main.c: 		device.product.id = "293e"
N: main.c: 		device.product.name = "82801I (ICH9 Family) HD Audio Controller"
N: main.c: 		device.form_factor = "internal"
N: main.c: 		device.string = "front:0"
N: main.c: 		device.buffering.buffer_size = "352768"
N: main.c: 		device.buffering.fragment_size = "176384"
N: main.c: 		device.access_mode = "mmap+timer"
N: main.c: 		device.profile.name = "analog-stereo"
N: main.c: 		device.profile.description = "Analog Stereo"
N: main.c: 		device.description = "Internt ljud Analog Stereo"
N: main.c: 		alsa.mixer_name = "Realtek ALC262"
N: main.c: 		alsa.components = "HDA:10ec0262,104d2e00,00100302 HDA:14f12c06,104d1700,00100000"
N: main.c: 		module-udev-detect.discovered = "1"
N: main.c: 		device.icon_name = "audio-card-pci"
N: main.c:     index: 3
N: main.c: 	name: <bluez_sink.00_02_72_E6_C7_08.monitor>
N: main.c: 	driver: <module-bluetooth-device.c>
N: main.c: 	flags: DECIBEL_VOLUME LATENCY 
N: main.c: 	state: SUSPENDED
N: main.c: 	suspend cause: IDLE 
N: main.c: 	priority: 1030
N: main.c: 	volume: 0: 100% 1: 100%
N: main.c: 	        0: 0,00 dB 1: 0,00 dB
N: main.c: 	        balance 0,00
N: main.c: 	base volume: 100%
N: main.c: 	             0,00 dB
N: main.c: 	volume steps: 65537
N: main.c: 	muted: no
N: main.c: 	current latency: 0,00 ms
N: main.c: 	max rewind: 0 KiB
N: main.c: 	sample spec: s16le 2ch 44100Hz
N: main.c: 	channel map: front-left,front-right
N: main.c: 	             Stereo
N: main.c: 	used by: 0
N: main.c: 	linked by: 0
N: main.c: 	fixed latency: 45,32 ms
N: main.c: 	monitor_of: 2
N: main.c: 	card: 2 <bluez_card.00_02_72_E6_C7_08>
N: main.c: 	module: 7
N: main.c: 	properties:
N: main.c: 		device.description = "Monitor of Belkin H95"
N: main.c: 		device.class = "monitor"
N: main.c: 		device.string = "00:02:72:E6:C7:08"
N: main.c: 		device.api = "bluez"
N: main.c: 		device.bus = "bluetooth"
N: main.c: 		device.form_factor = "headset"
N: main.c: 		bluez.path = "/org/bluez/1265/hci0/dev_00_02_72_E6_C7_08"
N: main.c: 		bluez.class = "0x240404"
N: main.c: 		bluez.name = "Belkin H95"
N: main.c: 		device.icon_name = "audio-headset-bluetooth"
N: main.c: 0 sink input(s) available.
N: main.c: 0 source outputs(s) available.
N: main.c: 5 client(s) logged in.
N: main.c:     index: 0
N: main.c: 	driver: <module-console-kit.c>
N: main.c: 	owner module: 17
N: main.c: 	properties:
N: main.c: 		application.name = "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
N: main.c: 		console-kit.session = "/org/freedesktop/ConsoleKit/Session1"
N: main.c:     index: 1
N: main.c: 	driver: <protocol-native.c>
N: main.c: 	owner module: 10
N: main.c: 	properties:
N: main.c: 		application.name = "libcanberra"
N: main.c: 		native-protocol.peer = "UNIX socket client"
N: main.c: 		native-protocol.version = "16"
N: main.c: 		window.x11.display = ":0.0"
N: main.c: 		window.x11.screen = "0"
N: main.c: 		application.process.id = "1614"
N: main.c: 		application.process.user = "petter"
N: main.c: 		application.process.host = "gunilla"
N: main.c: 		application.process.binary = "gnome-settings-daemon"
N: main.c: 		application.language = "sv_SE.UTF-8"
N: main.c: 		application.process.machine_id = "96ea5767ea6639ae0eaae94049cd171c"
N: main.c: 		application.process.session_id = "96ea5767ea6639ae0eaae94049cd171c-1272710141.168959-909394282"
N: main.c:     index: 2
N: main.c: 	driver: <protocol-native.c>
N: main.c: 	owner module: 10
N: main.c: 	properties:
N: main.c: 		application.name = "ayatana.indicator.sound"
N: main.c: 		native-protocol.peer = "UNIX socket client"
N: main.c: 		native-protocol.version = "16"
N: main.c: 		application.process.id = "2175"
N: main.c: 		application.process.user = "petter"
N: main.c: 		application.process.host = "gunilla"
N: main.c: 		application.process.binary = "indicator-sound-service"
N: main.c: 		application.language = "sv_SE.UTF-8"
N: main.c: 		window.x11.display = ":0.0"
N: main.c: 		application.process.machine_id = "96ea5767ea6639ae0eaae94049cd171c"
N: main.c: 		application.process.session_id = "96ea5767ea6639ae0eaae94049cd171c-1272710141.168959-909394282"
N: main.c:     index: 3
N: main.c: 	driver: <protocol-native.c>
N: main.c: 	owner module: 10
N: main.c: 	properties:
N: main.c: 		application.name = "libcanberra"
N: main.c: 		native-protocol.peer = "UNIX socket client"
N: main.c: 		native-protocol.version = "16"
N: main.c: 		window.x11.display = ":0.0"
N: main.c: 		window.x11.screen = "0"
N: main.c: 		application.process.id = "1652"
N: main.c: 		application.process.user = "petter"
N: main.c: 		application.process.host = "gunilla"
N: main.c: 		application.process.binary = "gnome-power-manager"
N: main.c: 		application.language = "sv_SE.UTF-8"
N: main.c: 		application.process.machine_id = "96ea5767ea6639ae0eaae94049cd171c"
N: main.c: 		application.process.session_id = "96ea5767ea6639ae0eaae94049cd171c-1272710141.168959-909394282"
N: main.c:     index: 4
N: main.c: 	driver: <protocol-native.c>
N: main.c: 	owner module: 10
N: main.c: 	properties:
N: main.c: 		application.name = "GNOME Volume Control Media Keys"
N: main.c: 		native-protocol.peer = "UNIX socket client"
N: main.c: 		native-protocol.version = "16"
N: main.c: 		application.id = "org.gnome.VolumeControl"
N: main.c: 		application.icon_name = "multimedia-volume-control"
N: main.c: 		application.version = "2.30.0"
N: main.c: 		application.process.id = "1614"
N: main.c: 		application.process.user = "petter"
N: main.c: 		application.process.host = "gunilla"
N: main.c: 		application.process.binary = "gnome-settings-daemon"
N: main.c: 		window.x11.display = ":0.0"
N: main.c: 		application.language = "sv_SE.UTF-8"
N: main.c: 		application.process.machine_id = "96ea5767ea6639ae0eaae94049cd171c"
N: main.c: 		application.process.session_id = "96ea5767ea6639ae0eaae94049cd171c-1272710141.168959-909394282"
N: main.c: 3 card(s) available.
N: main.c:     index: 0
N: main.c: 	name: <alsa_card.pci-0000_01_00.1>
N: main.c: 	driver: <module-alsa-card.c>
N: main.c: 	owner module: 4
N: main.c: 	properties:
N: main.c: 		alsa.card = "1"
N: main.c: 		alsa.card_name = "HDA ATI HDMI"
N: main.c: 		alsa.long_card_name = "HDA ATI HDMI at 0xd0030000 irq 17"
N: main.c: 		alsa.driver_name = "snd_hda_intel"
N: main.c: 		device.bus_path = "pci-0000:01:00.1"
N: main.c: 		sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
N: main.c: 		device.bus = "pci"
N: main.c: 		device.vendor.id = "1002"
N: main.c: 		device.vendor.name = "ATI Technologies Inc"
N: main.c: 		device.product.id = "aa28"
N: main.c: 		device.product.name = "RV620 Audio device [Radeon HD 34xx Series]"
N: main.c: 		device.string = "1"
N: main.c: 		device.description = "RV620 Audio device [Radeon HD 34xx Series]"
N: main.c: 		module-udev-detect.discovered = "1"
N: main.c: 		device.icon_name = "audio-card-pci"
N: main.c: 	profiles:
N: main.c: 		output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400)
N: main.c: 		off: Off (priority 0)
N: main.c: 	active profile: <output:hdmi-stereo>
N: main.c: 	sinks:
N: main.c: 		alsa_output.pci-0000_01_00.1.hdmi-stereo/#0: RV620 Audio device [Radeon HD 34xx Series] Digital Stereo (HDMI)
N: main.c: 	sources:
N: main.c: 		alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor/#0: Monitor of RV620 Audio device [Radeon HD 34xx Series] Digital Stereo (HDMI)
N: main.c:     index: 1
N: main.c: 	name: <alsa_card.pci-0000_00_1b.0>
N: main.c: 	driver: <module-alsa-card.c>
N: main.c: 	owner module: 5
N: main.c: 	properties:
N: main.c: 		alsa.card = "0"
N: main.c: 		alsa.card_name = "HDA Intel"
N: main.c: 		alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
N: main.c: 		alsa.driver_name = "snd_hda_intel"
N: main.c: 		device.bus_path = "pci-0000:00:1b.0"
N: main.c: 		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
N: main.c: 		device.bus = "pci"
N: main.c: 		device.vendor.id = "8086"
N: main.c: 		device.vendor.name = "Intel Corporation"
N: main.c: 		device.product.id = "293e"
N: main.c: 		device.product.name = "82801I (ICH9 Family) HD Audio Controller"
N: main.c: 		device.form_factor = "internal"
N: main.c: 		device.string = "0"
N: main.c: 		device.description = "Internt ljud"
N: main.c: 		module-udev-detect.discovered = "1"
N: main.c: 		device.icon_name = "audio-card-pci"
N: main.c: 	profiles:
N: main.c: 		output:analog-stereo: Analog Stereo Output (priority 6000)
N: main.c: 		output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060)
N: main.c: 		input:analog-stereo: Analog Stereo Input (priority 60)
N: main.c: 		off: Off (priority 0)
N: main.c: 	active profile: <output:analog-stereo+input:analog-stereo>
N: main.c: 	sinks:
N: main.c: 		alsa_output.pci-0000_00_1b.0.analog-stereo/#1: Internt ljud Analog Stereo
N: main.c: 	sources:
N: main.c: 		alsa_output.pci-0000_00_1b.0.analog-stereo.monitor/#1: Monitor of Internt ljud Analog Stereo
N: main.c: 		alsa_input.pci-0000_00_1b.0.analog-stereo/#2: Internt ljud Analog Stereo
N: main.c:     index: 2
N: main.c: 	name: <bluez_card.00_02_72_E6_C7_08>
N: main.c: 	driver: <module-bluetooth-device.c>
N: main.c: 	owner module: 7
N: main.c: 	properties:
N: main.c: 		device.description = "Belkin H95"
N: main.c: 		device.string = "00:02:72:E6:C7:08"
N: main.c: 		device.api = "bluez"
N: main.c: 		device.class = "sound"
N: main.c: 		device.bus = "bluetooth"
N: main.c: 		device.form_factor = "headset"
N: main.c: 		bluez.path = "/org/bluez/1265/hci0/dev_00_02_72_E6_C7_08"
N: main.c: 		bluez.class = "0x240404"
N: main.c: 		bluez.name = "Belkin H95"
N: main.c: 		device.icon_name = "audio-headset-bluetooth"
N: main.c: 	profiles:
N: main.c: 		a2dp: High Fidelity Playback
I: main.c: Fick signal SIGINT.
I: main.c: Avslutar.
I: main.c: Daemon shutdown initiated.
I: module.c: Unloading "module-device-restore" (index: #0).
I: module.c: Unloaded "module-device-restore" (index: #0).
I: module.c: Unloading "module-stream-restore" (index: #1).
I: module.c: Unloaded "module-stream-restore" (index: #1).
I: module.c: Unloading "module-card-restore" (index: #2).
I: module.c: Unloaded "module-card-restore" (index: #2).
I: module.c: Unloading "module-augment-properties" (index: #3).
I: module.c: Unloaded "module-augment-properties" (index: #3).
I: module.c: Unloading "module-alsa-card" (index: #4).
I: sink.c: Freeing sink 0 "alsa_output.pci-0000_01_00.1.hdmi-stereo"
I: source.c: Freeing source 0 "alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor"
I: card.c: Freed 0 "alsa_card.pci-0000_01_00.1"
I: module.c: Unloaded "module-alsa-card" (index: #4).
I: module.c: Unloading "module-alsa-card" (index: #5).
I: sink.c: Freeing sink 1 "alsa_output.pci-0000_00_1b.0.analog-stereo"
I: source.c: Freeing source 1 "alsa_output.pci-0000_00_1b.0.analog-stereo.monitor"
I: source.c: Freeing source 2 "alsa_input.pci-0000_00_1b.0.analog-stereo"
I: card.c: Freed 1 "alsa_card.pci-0000_00_1b.0"
I: module.c: Unloaded "module-alsa-card" (index: #5).
I: module.c: Unloading "module-udev-detect" (index: #6).
I: module.c: Unloaded "module-udev-detect" (index: #6).
I: module.c: Unloading "module-bluetooth-device" (index: #7).
I: sink.c: Freeing sink 2 "bluez_sink.00_02_72_E6_C7_08"
I: source.c: Freeing source 3 "bluez_sink.00_02_72_E6_C7_08.monitor"
I: card.c: Freed 2 "bluez_card.00_02_72_E6_C7_08"
I: module.c: Unloaded "module-bluetooth-device" (index: #7).
I: module.c: Unloading "module-bluetooth-discover" (index: #8).
I: module.c: Unloaded "module-bluetooth-discover" (index: #8).
I: module.c: Unloading "module-esound-protocol-unix" (index: #9).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #9).
I: module.c: Unloading "module-native-protocol-unix" (index: #10).
I: client.c: Freed 1 "libcanberra"
I: client.c: Freed 2 "ayatana.indicator.sound"
I: client.c: Freed 3 "libcanberra"
I: client.c: Freed 4 "GNOME Volume Control Media Keys"
I: module.c: Unloaded "module-native-protocol-unix" (index: #10).
I: module.c: Unloading "module-gconf" (index: #11).
I: module.c: Unloaded "module-gconf" (index: #11).
I: module.c: Unloading "module-default-device-restore" (index: #12).
I: module.c: Unloaded "module-default-device-restore" (index: #12).
I: module.c: Unloading "module-rescue-streams" (index: #13).
I: module.c: Unloaded "module-rescue-streams" (index: #13).
I: module.c: Unloading "module-always-sink" (index: #14).
I: module.c: Unloaded "module-always-sink" (index: #14).
I: module.c: Unloading "module-intended-roles" (index: #15).
I: module.c: Unloaded "module-intended-roles" (index: #15).
I: module.c: Unloading "module-suspend-on-idle" (index: #16).
I: module.c: Unloaded "module-suspend-on-idle" (index: #16).
I: module.c: Unloading "module-console-kit" (index: #17).
I: client.c: Freed 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
I: module.c: Unloaded "module-console-kit" (index: #17).
I: module.c: Unloading "module-position-event-sounds" (index: #18).
I: module.c: Unloaded "module-position-event-sounds" (index: #18).
I: main.c: Daemon terminated.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) misslyckades: Operationen inte tillåten
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: Detta är PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Kompilerad med Valgrind-stöd: nej
D: main.c: Kör i valgrind-läge: no
D: main.c: Running in VM: no
D: main.c: Optimerat bygge: ja
D: main.c: All asserts enabled.
I: main.c: Machine ID is 96ea5767ea6639ae0eaae94049cd171c.
I: main.c: Session ID is 96ea5767ea6639ae0eaae94049cd171c-1272749634.947472-1093471698.
I: main.c: Using runtime directory /home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-runtime.
I: main.c: Using state directory /home/petter/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Kör i systemläge: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 SSE4_1 
I: svolume_mmx.c: Initialising MMX optimized functions.
I: remap_mmx.c: Initialising MMX optimized remappers.
I: svolume_sse.c: Initialising SSE2 optimized functions.
I: remap_sse.c: Initialising SSE2 optimized remappers.
I: sconv_sse.c: Initialising SSE2 optimized conversions.
D: memblock.c: Using shared memory pool with 1024 slots of size 64,0 KiB each, total size is 64,0 MiB, maximum usable slot size is 65496
D: database-tdb.c: Opened TDB database '/home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-device-volumes.tdb'
I: module-device-restore.c: Sucessfully opened database file '/home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-device-volumes'.
I: module.c: Loaded "module-device-restore" (index: #0; argument: "").
D: database-tdb.c: Opened TDB database '/home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-stream-volumes.tdb'
I: module-stream-restore.c: Sucessfully opened database file '/home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-stream-volumes'.
I: module.c: Loaded "module-stream-restore" (index: #1; argument: "").
D: database-tdb.c: Opened TDB database '/home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-card-database.tdb'
I: module-card-restore.c: Sucessfully opened database file '/home/petter/.pulse/96ea5767ea6639ae0eaae94049cd171c-card-database'.
I: module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-udev-detect.so': success
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1 is busy: no
D: module-udev-detect.c: Loading module-alsa-card with arguments 'device_id="1" name="pci-0000_01_00.1" card_name="alsa_card.pci-0000_01_00.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"'
D: dbus-util.c: Successfully connected to D-Bus session bus e7babc16cee3b98ec0b2bac84bdc9e43 as :1.198
D: reserve-wrap.c: Successfully acquired reservation lock on device 'Audio1'
D: alsa-mixer.c: Looking at profile output:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-mono+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-mono+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-mono+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-mono+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround40:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround40:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround40:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround40:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround40:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-41
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround41:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround41:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround41:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround41:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround41:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-50
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround50:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround50:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround50:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround50:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround50:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-51
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround51:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround51:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround51:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround51:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround51:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-71
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround71:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround71:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround71:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround71:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0p failed
I: alsa-util.c: Error opening PCM device surround71:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1p failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:hdmi-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hdmi:1
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:hdmi-stereo supported.
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1c failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1c failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device front:1: Filen eller katalogen finns inte
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D0c failed
I: alsa-util.c: Error opening PCM device hw:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1c failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC1D1c failed
I: alsa-util.c: Error opening PCM device iec958:1: Filen eller katalogen finns inte
I: card.c: Created 0 "alsa_card.pci-0000_01_00.1"
D: reserve-wrap.c: Successfully create reservation lock monitor for device 'Audio1'
D: alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hdmi:1
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
I: alsa-sink.c: Successfully opened device hdmi:1.
I: alsa-sink.c: Selected mapping 'Digital Stereo (HDMI)' (hdmi-stereo).
I: alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL hdmi:1
I: alsa-mixer.c: Unable to attach to mixer hdmi:1: Filen eller katalogen finns inte
I: alsa-mixer.c: Successfully attached to mixer 'hw:1'
I: module-device-restore.c: Restoring volume for sink alsa_output.pci-0000_01_00.1.hdmi-stereo.
I: sink.c: Created sink 0 "alsa_output.pci-0000_01_00.1.hdmi-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     alsa.resolution_bits = "16"
I: sink.c:     device.api = "alsa"
I: sink.c:     device.class = "sound"
I: sink.c:     alsa.class = "generic"
I: sink.c:     alsa.subclass = "generic-mix"
I: sink.c:     alsa.name = "ATI HDMI"
I: sink.c:     alsa.id = "ATI HDMI"
I: sink.c:     alsa.subdevice = "0"
I: sink.c:     alsa.subdevice_name = "subdevice #0"
I: sink.c:     alsa.device = "3"
I: sink.c:     alsa.card = "1"
I: sink.c:     alsa.card_name = "HDA ATI HDMI"
I: sink.c:     alsa.long_card_name = "HDA ATI HDMI at 0xd0030000 irq 17"
I: sink.c:     alsa.driver_name = "snd_hda_intel"
I: sink.c:     device.bus_path = "pci-0000:01:00.1"
I: sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
I: sink.c:     device.bus = "pci"
I: sink.c:     device.vendor.id = "1002"
I: sink.c:     device.vendor.name = "ATI Technologies Inc"
I: sink.c:     device.product.id = "aa28"
I: sink.c:     device.product.name = "RV620 Audio device [Radeon HD 34xx Series]"
I: sink.c:     device.string = "hdmi:1"
I: sink.c:     device.buffering.buffer_size = "352768"
I: sink.c:     device.buffering.fragment_size = "176384"
I: sink.c:     device.access_mode = "mmap+timer"
I: sink.c:     device.profile.name = "hdmi-stereo"
I: sink.c:     device.profile.description = "Digital Stereo (HDMI)"
I: sink.c:     device.description = "RV620 Audio device [Radeon HD 34xx Series] Digital Stereo (HDMI)"
I: sink.c:     alsa.mixer_name = "ATI R6xx HDMI"
I: sink.c:     alsa.components = "HDA:1002aa01,104d2e00,00100000"
I: sink.c:     module-udev-detect.discovered = "1"
I: sink.c:     device.icon_name = "audio-card-pci"
D: core-subscribe.c: Dropped redundant event due to change event.
I: source.c: Created source 0 "alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of RV620 Audio device [Radeon HD 34xx Series] Digital Stereo (HDMI)"
I: source.c:     device.class = "monitor"
I: source.c:     alsa.card = "1"
I: source.c:     alsa.card_name = "HDA ATI HDMI"
I: source.c:     alsa.long_card_name = "HDA ATI HDMI at 0xd0030000 irq 17"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:01:00.1"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "1002"
I: source.c:     device.vendor.name = "ATI Technologies Inc"
I: source.c:     device.product.id = "aa28"
I: source.c:     device.product.name = "RV620 Audio device [Radeon HD 34xx Series]"
I: source.c:     device.string = "1"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-sink.c: Using 2,0 fragments of size 176384 bytes (999,91ms), buffer size is 352768 bytes (1999,82ms)
I: alsa-sink.c: Time scheduling watermark is 20,00ms
D: alsa-sink.c: hwbuf_unused=0
D: alsa-sink.c: setting avail_min=87310
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Hooks PCM
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1444937728
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1444937728
D: alsa-util.c: Slave: Hardware PCM card 1 'HDA ATI HDMI' device 3 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1444937728
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1444937728
D: alsa-util.c:   appl_ptr     : 0
D: alsa-util.c:   hw_ptr       : 0
D: alsa-sink.c: Thread starting up
D: core-util.c: SCHED_RR|SCHED_RESET_ON_FORK worked.
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: alsa-sink.c: Starting playback.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
I: module.c: Loaded "module-alsa-card" (index: #4; argument: "device_id="1" name="pci-0000_01_00.1" card_name="alsa_card.pci-0000_01_00.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"").
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1 (alsa_card.pci-0000_01_00.1) module loaded.
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
D: module-udev-detect.c: /devices/pci0000:00/0000:00:1b.0/sound/card0 is busy: no
D: module-udev-detect.c: Loading module-alsa-card with arguments 'device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"'
D: reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
D: alsa-mixer.c: Looking at profile output:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-stereo supported.
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-stereo+input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:analog-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:iec958-stereo supported.
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:iec958-stereo+input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:hdmi-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Ogiltigt argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Ogiltigt argument
D: alsa-mixer.c: Looking at profile input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
D: alsa-mixer.c: Looking at profile input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: Filen eller katalogen finns inte
I: module-card-restore.c: Restoring profile for card alsa_card.pci-0000_00_1b.0.
I: card.c: Created 1 "alsa_card.pci-0000_00_1b.0"
D: reserve-wrap.c: Successfully create reservation lock monitor for device 'Audio0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
I: alsa-sink.c: Successfully opened device front:0.
I: alsa-sink.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-mixer.c: Unable to attach to mixer front:0: Filen eller katalogen finns inte
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
D: alsa-mixer.c: Probing path 'analog-output'
D: alsa-mixer.c: Probing path 'analog-output-speaker'
D: alsa-mixer.c: Probing path 'analog-output-speaker'
D: alsa-mixer.c: Probe of element 'Desktop Speaker' failed.
D: alsa-mixer.c: Probing path 'analog-output-headphones'
D: alsa-mixer.c: Probing path 'analog-output-headphones'
D: alsa-mixer.c: Probe of element 'Headphone2' failed.
D: alsa-mixer.c: Probing path 'analog-output-mono'
D: alsa-mixer.c: Probe of element 'Master Mono' failed.
D: alsa-mixer.c: Probing path 'analog-output-lfe-on-mono'
D: alsa-mixer.c: Probe of element 'Master Mono' failed.
D: alsa-sink.c: Probed mixer paths:
D: alsa-mixer.c: Path Set 0x8568ed8, direction=1, probed=yes
D: alsa-mixer.c: Path analog-output (Analog Output), direction=1, priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=30, min_dB=-96, max_dB=0
D: alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=0, enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
D: alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=2, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Path analog-output-speaker (Analog Speakers), direction=1, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=30, min_dB=-141, max_dB=0
D: alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=0, enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
D: alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=1, enumeration=0, required=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Path analog-output-headphones (Analog Headphones), direction=1, priority=90, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=30, min_dB=-96, max_dB=0
D: alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=0, enumeration=0, required=4, required_absent=0, mask=0x0, n_channels=0, override_map=yes
D: alsa-mixer.c: Element Speaker, direction=1, switch=2, volume=2, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Added 3 ports
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-device-restore.c: Restoring port for sink sink:alsa_output.pci-0000_00_1b.0.analog-stereo.
I: module-device-restore.c: Restoring volume for sink alsa_output.pci-0000_00_1b.0.analog-stereo.
I: sink.c: Created sink 1 "alsa_output.pci-0000_00_1b.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     alsa.resolution_bits = "16"
I: sink.c:     device.api = "alsa"
I: sink.c:     device.class = "sound"
I: sink.c:     alsa.class = "generic"
I: sink.c:     alsa.subclass = "generic-mix"
I: sink.c:     alsa.name = "ALC262 Analog"
I: sink.c:     alsa.id = "ALC262 Analog"
I: sink.c:     alsa.subdevice = "0"
I: sink.c:     alsa.subdevice_name = "subdevice #0"
I: sink.c:     alsa.device = "0"
I: sink.c:     alsa.card = "0"
I: sink.c:     alsa.card_name = "HDA Intel"
I: sink.c:     alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
I: sink.c:     alsa.driver_name = "snd_hda_intel"
I: sink.c:     device.bus_path = "pci-0000:00:1b.0"
I: sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: sink.c:     device.bus = "pci"
I: sink.c:     device.vendor.id = "8086"
I: sink.c:     device.vendor.name = "Intel Corporation"
I: sink.c:     device.product.id = "293e"
I: sink.c:     device.product.name = "82801I (ICH9 Family) HD Audio Controller"
I: sink.c:     device.form_factor = "internal"
I: sink.c:     device.string = "front:0"
I: sink.c:     device.buffering.buffer_size = "352768"
I: sink.c:     device.buffering.fragment_size = "176384"
I: sink.c:     device.access_mode = "mmap+timer"
I: sink.c:     device.profile.name = "analog-stereo"
I: sink.c:     device.profile.description = "Analog Stereo"
I: sink.c:     device.description = "Internt ljud Analog Stereo"
I: sink.c:     alsa.mixer_name = "Realtek ALC262"
I: sink.c:     alsa.components = "HDA:10ec0262,104d2e00,00100302 HDA:14f12c06,104d1700,00100000"
I: sink.c:     module-udev-detect.discovered = "1"
I: sink.c:     device.icon_name = "audio-card-pci"
D: core-subscribe.c: Dropped redundant event due to change event.
I: source.c: Created source 1 "alsa_output.pci-0000_00_1b.0.analog-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of Internt ljud Analog Stereo"
I: source.c:     device.class = "monitor"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA Intel"
I: source.c:     alsa.long_card_name = "HDA Intel at 0xd5200000 irq 22"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:00:1b.0"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "8086"
I: source.c:     device.vendor.name = "Intel Corporation"
I: source.c:     device.product.id = "293e"
I: source.c:     device.product.name = "82801I (ICH9 Family) HD Audio Controller"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "0"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-sink.c: Using 2,0 fragments of size 176384 bytes (999,91ms), buffer size is 352768 bytes (1999,82ms)
I: alsa-sink.c: Time scheduling watermark is 20,00ms
D: alsa-sink.c: hwbuf_unused=0
D: alsa-sink.c: setting avail_min=87310
D: alsa-mixer.c: Activating path analog-output-speaker
D: alsa-mixer.c: Path analog-output-speaker (Analog Speakers), direction=1, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=30, min_dB=-141, max_dB=0
D: alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=0, enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
D: alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=1, enumeration=0, required=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
I: alsa-sink.c: Hardware volume ranges from -141,00 dB to 0,00 dB.
I: alsa-sink.c: No particular base volume set, fixing to 0 dB
I: alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-sink.c: Using hardware mute control.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1444937728
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1444937728
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1444937728
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1444937728
D: alsa-util.c:   appl_ptr     : 0
D: alsa-util.c:   hw_ptr       : 0
D: alsa-sink.c: Thread starting up
D: alsa-sink.c: Requested volume: 0:  45% 1:  45%
D: core-util.c: SCHED_RR|SCHED_RESET_ON_FORK worked.
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
D: alsa-sink.c: Got hardware volume: 0:  45% 1:  45%
D: alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
I: alsa-sink.c: Starting playback.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
I: module.c: Loaded "module-alsa-card" (index: #5; argument: "device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"").
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:1b.0/sound/card0 (alsa_card.pci-0000_00_1b.0) module loaded.
I: module-udev-detect.c: Found 2 cards.
I: module.c: Loaded "module-udev-detect" (index: #6; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-bluetooth-discover.so': success
D: dbus-util.c: Successfully connected to D-Bus system bus 745ae090dc53606fd2a99d524bdc9e32 as :1.73
D: bluetooth-util.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module.c: Loaded "module-bluetooth-discover" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #8; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #10; argument: "").
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci-0000_00_1b.0.analog-stereo'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_output.pci-0000_00_1b.0.analog-stereo.monitor'.
I: module.c: Loaded "module-default-device-restore" (index: #11; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #12; argument: "").
I: module.c: Loaded "module-always-sink" (index: #13; argument: "").
I: module.c: Loaded "module-intended-roles" (index: #14; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci-0000_01_00.1.hdmi-stereo becomes idle, timeout in 5 seconds.
D: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo becomes idle, timeout in 5 seconds.
I: module.c: Loaded "module-suspend-on-idle" (index: #15; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: module.c: Loaded "module-console-kit" (index: #16; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #17; argument: "").
D: main.c: Got org.pulseaudio.Server!
I: main.c: Daemon startup complete.
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
I: client.c: Created 1 "Native client (UNIX socket client)"
I: client.c: Created 2 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 16, local 16
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
D: protocol-native.c: Protocol version: remote 16, local 16
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
D: module-augment-properties.c: Looking for .desktop file for indicator-sound-service
D: module-augment-properties.c: Looking for .desktop file for thunderbird-bin
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: protocol-native.c: Client indicator-sound-service changes volume of sink alsa_output.pci-0000_00_1b.0.analog-stereo.
D: alsa-sink.c: Requested volume: 0:  45% 1:  45%
D: alsa-sink.c: Got hardware volume: 0:  45% 1:  45%
D: alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
I: client.c: Created 3 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 16, local 16
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
D: module-augment-properties.c: Looking for .desktop file for gnome-settings-daemon
I: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo idle for too long, suspending ...
D: sink.c: Suspend cause of sink alsa_output.pci-0000_00_1b.0.analog-stereo is 0x0004, suspending
I: alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci-0000_01_00.1.hdmi-stereo idle for too long, suspending ...
D: sink.c: Suspend cause of sink alsa_output.pci-0000_01_00.1.hdmi-stereo is 0x0004, suspending
I: alsa-sink.c: Device suspended...
D: reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio0 changed: not busy
D: reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio1 changed: not busy
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
I: client.c: Created 4 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 16, local 16
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
D: module-augment-properties.c: Looking for .desktop file for rhythmbox
I: client.c: Freed 4 "Rhythmbox"
I: protocol-native.c: Connection died.

```

I also tried the reinstall of alsa and pulse as suggested in [http://ubuntuforums.org/showthread.php?t=1466615&page=2](http://ubuntuforums.org/showthread.php?t=1466615&page=2) but this had no effect...

---

### Post by peppot on 2010-05-02
More weirdness. MPlayer and VLC can both output through Pulse, but Rhythmbox, Totem or Quod Libet can't. Does this seem to point to it being a gstreamer issue? Any ideas how to debug gstreamer?

---

### Post by hugmenot on 2010-05-02
Since the pulseaudio log just says "connection died" it probably /is/ gstreamer.

How did you set up your gstreamer output pipelines?

There is the tool gstreamer-properties, where you can set the global pipeline.

In gconf you can also set pipelines for musicaudio and chataudio separately under /system/gstreamer/0.10/default

---

### Post by peppot on 2010-05-02
Thank you hugmenot! The musicaudiosink was set to "Intel", which isn't availible anymore. I copied the audiosink setting and all now works! Awesome. Big thanks!

---

### Post by hugmenot on 2010-05-02
You’re welcome.

I doubt "Intel" was ever a valid Gstreamer pipeline, though.

---

