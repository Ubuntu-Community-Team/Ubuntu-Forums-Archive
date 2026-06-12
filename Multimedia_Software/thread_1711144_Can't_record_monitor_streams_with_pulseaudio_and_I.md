---
title: "Can't record monitor streams with pulseaudio and Intel 82801H"
date: 2011-03-20
forum: Multimedia Software
---

### Post by dhasenan on 2011-03-20
Hi,

I'm getting silence when trying to record output from pulseaudio on my laptop. This wasn't happening the last time I tried, which, I admit, was almost certainly a previous ubuntu release (I'm on 10.10).

My sound card is an Intel ICH8-family device, supported by the snd_hda_intel module. PulseAudio calls it "Internal Audio Analog Stereo".

I'm doing various things that I find on the onlines, a few main ideas:

1. parec
I use:
```
parec -d alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
```

When I search for 'monitor' in $(pactl list), the only thing listed is alsa_output.pci-0000_00_1b.0.analog-stereo.monitor.

I use sox to convert the output to wav:
```
sox -t raw -r 44k -e signed-integer -L b 16 -c 2 $RAWFILE $WAVFILE
```

To make sure that the format was the same in both cases, I tried specifying everything in parec (as well as specifying nothing):
```
parec -d alsa_output.pci-0000_00_1b.0.analog-stereo.monitor --channels=2 --format=s16le --rate=44100 $RAWFILE
```

In all cases, the wav file is of the appropriate length, but silent.

2. Sound Recorder / Audacity; pavucontrol to change input source
I change the source 
The result file is of the appropriate length, but silent.

lspci reports the following about my sound card:
```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Dell Device 0275
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f8500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```

And snd_hda_intel is loaded:
```

$ lsmod|ack ^snd_hda_intel
snd_hda_intel          26115  6
```

When I open pavucontrol, I can see the level bar for my microphone moving when I talk, but I can't see the level bar for my sound output or the monitor channel.

It looks like pulseaudio can't see the monitor channel on this video card.

pactl list shows the following for my card's output:
```

Sink #0
        State: RUNNING
        Name: alsa_output.pci-0000_00_1b.0.analog-stereo
        Description: Internal Audio Analog Stereo
        Driver: module-alsa-card.c
        Sample Specification: s16le 2ch 44100Hz
        Channel Map: front-left,front-right
        Owner Module: 5
        Mute: no
        Volume: 0: 100% 1: 100%
                0: 0.00 dB 1: 0.00 dB
                balance 0.00
        Base Volume: 100%
                     0.00 dB
        Monitor Source: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
        Latency: 95910 usec, configured 96000 usec
        Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
        Properties:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = "ALC268 Analog"
                alsa.id = "ALC268 Analog"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "0"
                alsa.card = "0"
                alsa.card_name = "HDA Intel"
                alsa.long_card_name = "HDA Intel at 0xf8500000 irq 46"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1b.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "284b"
                device.product.name = "82801H (ICH8 Family) HD Audio Controller"
                device.form_factor = "internal"
                device.string = "front:0"
                device.buffering.buffer_size = "352768"
                device.buffering.fragment_size = "176384"
                device.access_mode = "mmap+timer"
                device.profile.name = "analog-stereo"
                device.profile.description = "Analog Stereo"
                device.description = "Internal Audio Analog Stereo"
                alsa.mixer_name = "Realtek ALC268"
                alsa.components = "HDA:10ec0268,10280275,00100003"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        Ports:
                analog-output: Analog Output (priority. 9900)
                analog-output-speaker: Analog Speakers (priority. 10000)
                analog-output-headphones: Analog Headphones (priority. 9000)
        Active Port: analog-output-speaker
```

And for its monitor:
```

Source #1
        State: IDLE
        Name: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
        Description: Monitor of Internal Audio Analog Stereo
        Driver: module-alsa-card.c
        Sample Specification: s16le 2ch 44100Hz
        Channel Map: front-left,front-right
        Owner Module: 5
        Mute: yes
        Volume: 0: 100% 1: 100%
                0: 0.00 dB 1: 0.00 dB
                balance 0.00
        Base Volume: 100%
                     0.00 dB
        Monitor of Sink: alsa_output.pci-0000_00_1b.0.analog-stereo
        Latency: 0 usec, configured 1999818 usec
        Flags: DECIBEL_VOLUME LATENCY 
        Properties:
                device.description = "Monitor of Internal Audio Analog Stereo"
                device.class = "monitor"
                alsa.card = "0"
                alsa.card_name = "HDA Intel"
                alsa.long_card_name = "HDA Intel at 0xf8500000 irq 46"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1b.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "284b"
                device.product.name = "82801H (ICH8 Family) HD Audio Controller"
                device.form_factor = "internal"
                device.string = "0"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
```

The full unabridged output of pactl list:
```

Module #0
	Name: module-device-restore
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the volume/mute state of devices"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #1
	Name: module-stream-restore
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the volume/mute/device state of streams"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #2
	Name: module-card-restore
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore profile of cards"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #3
	Name: module-augment-properties
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Augment the property sets of streams with additional static information"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #4
	Name: module-alsa-card
	Argument: device_id="1" name="usb-AKM_AK5370-00-default" card_name="alsa_card.usb-AKM_AK5370-00-default" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"
	Usage counter: 0
	Properties:
		module.author = "Lennart Poettering"
		module.description = "ALSA Card"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #5
	Name: module-alsa-card
	Argument: device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"
	Usage counter: 2
	Properties:
		module.author = "Lennart Poettering"
		module.description = "ALSA Card"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #6
	Name: module-udev-detect
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Detect available audio hardware and load matching drivers"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #7
	Name: module-bluetooth-discover
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Joao Paulo Rechi Vita"
		module.description = "Detect available bluetooth audio devices and load bluetooth audio drivers"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #8
	Name: module-esound-protocol-unix
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "ESOUND protocol (UNIX sockets)"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #9
	Name: module-native-protocol-unix
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Native protocol (UNIX sockets)"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #10
	Name: module-gconf
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "GConf Adapter"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #11
	Name: module-default-device-restore
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the default sink and source"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #12
	Name: module-rescue-streams
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "When a sink/source is removed, try to move their streams to the default sink/source"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #13
	Name: module-always-sink
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Colin Guthrie"
		module.description = "Always keeps at least one sink loaded even if it's a null one"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #14
	Name: module-intended-roles
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically set device of streams based of intended roles of devices"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #15
	Name: module-suspend-on-idle
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "When a sink/source is idle for too long, suspend it"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #16
	Name: module-console-kit
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Create a client for each ConsoleKit session of this user"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #17
	Name: module-position-event-sounds
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Position event sounds between L and R depending on the position on screen of the widget triggering them."
		module.version = "0.9.21-63-gd3efa-dirty"

Module #18
	Name: module-x11-publish
	Argument: display=:0.0
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "X11 credential publisher"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #19
	Name: module-x11-bell
	Argument: display=:0.0 sample=bell.ogg
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "X11 bell interceptor"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #20
	Name: module-x11-cork-request
	Argument: display=:0.0
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Synthesize X11 media key events when cork/uncork is requested"
		module.version = "0.9.21-63-gd3efa-dirty"

Module #21
	Name: module-x11-xsmp
	Argument: display=:0.0 session_manager=local/cerebus:@/tmp/.ICE-unix/2815,unix/cerebus:/tmp/.ICE-unix/2815
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "X11 session management"
		module.version = "0.9.21-63-gd3efa-dirty"

Sink #0
	State: RUNNING
	Name: alsa_output.pci-0000_00_1b.0.analog-stereo
	Description: Internal Audio Analog Stereo
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 5
	Mute: no
	Volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	Base Volume: 100%
	             0.00 dB
	Monitor Source: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
	Latency: 93543 usec, configured 96000 usec
	Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
	Properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "ALC268 Analog"
		alsa.id = "ALC268 Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xf8500000 irq 46"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "284b"
		device.product.name = "82801H (ICH8 Family) HD Audio Controller"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "352768"
		device.buffering.fragment_size = "176384"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Internal Audio Analog Stereo"
		alsa.mixer_name = "Realtek ALC268"
		alsa.components = "HDA:10ec0268,10280275,00100003"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Ports:
		analog-output: Analog Output (priority. 9900)
		analog-output-speaker: Analog Speakers (priority. 10000)
		analog-output-headphones: Analog Headphones (priority. 9000)
	Active Port: analog-output-speaker

Source #0
	State: SUSPENDED
	Name: alsa_input.usb-AKM_AK5370-00-default.analog-mono
	Description: AK5370 I/F A/D Converter Analog Mono
	Driver: module-alsa-card.c
	Sample Specification: s16le 1ch 44100Hz
	Channel Map: mono
	Owner Module: 4
	Mute: no
	Volume: 0: 100%
	        0: 0.00 dB
	        balance 0.00
	Base Volume:  46%
	             -20.00 dB
	Monitor of Sink: n/a
	Latency: 0 usec, configured 0 usec
	Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
	Properties:
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
		alsa.card_name = "AK5370"
		alsa.long_card_name = "AKM              AK5370           at usb-0000:00:1a.1-1, full speed"
		alsa.driver_name = "snd_usb_audio"
		device.bus_path = "pci-0000:00:1a.1-usb-0:1:1.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/sound/card1"
		udev.id = "usb-AKM_AK5370-00-default"
		device.bus = "usb"
		device.vendor.id = "0556"
		device.vendor.name = "Asahi Kasei Microsystems Co., Ltd"
		device.product.id = "0001"
		device.product.name = "AK5370 I/F A/D Converter"
		device.serial = "AKM_AK5370"
		device.string = "hw:1"
		device.buffering.buffer_size = "176400"
		device.buffering.fragment_size = "88200"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-mono"
		device.profile.description = "Analog Mono"
		device.description = "AK5370 I/F A/D Converter Analog Mono"
		alsa.mixer_name = "USB Mixer"
		alsa.components = "USB0556:0001"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-usb"

Source #1
	State: IDLE
	Name: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
	Description: Monitor of Internal Audio Analog Stereo
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 5
	Mute: yes
	Volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	Base Volume: 100%
	             0.00 dB
	Monitor of Sink: alsa_output.pci-0000_00_1b.0.analog-stereo
	Latency: 0 usec, configured 1999818 usec
	Flags: DECIBEL_VOLUME LATENCY 
	Properties:
		device.description = "Monitor of Internal Audio Analog Stereo"
		device.class = "monitor"
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xf8500000 irq 46"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "284b"
		device.product.name = "82801H (ICH8 Family) HD Audio Controller"
		device.form_factor = "internal"
		device.string = "0"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"

Source #2
	State: RUNNING
	Name: alsa_input.pci-0000_00_1b.0.analog-stereo
	Description: Internal Audio Analog Stereo
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 5
	Mute: yes
	Volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	Base Volume:  32%
	             -30.00 dB
	Monitor of Sink: n/a
	Latency: 9024 usec, configured 116000 usec
	Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
	Properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "ALC268 Analog"
		alsa.id = "ALC268 Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xf8500000 irq 46"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "284b"
		device.product.name = "82801H (ICH8 Family) HD Audio Controller"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "352768"
		device.buffering.fragment_size = "176384"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Internal Audio Analog Stereo"
		alsa.mixer_name = "Realtek ALC268"
		alsa.components = "HDA:10ec0268,10280275,00100003"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"

Sink Input #392
	Driver: protocol-native.c
	Owner Module: 9
	Client: 671
	Sink: 0
	Sample Specification: float32le 2ch 44100Hz
	Channel Map: front-left,front-right
	Mute: no
	Volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	Buffer Latency: 124648 usec
	Sink Latency: 93213 usec
	Resample method: copy
	Properties:
		media.name = "audio stream"
		application.name = "VLC media player"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "16"
		application.process.id = "31751"
		application.process.user = "dhasenan"
		application.process.host = "cerebus"
		application.process.binary = "vlc"
		application.language = "en_US.utf8"
		window.x11.display = ":0.0"
		application.process.machine_id = "f4776ed6cfc261cc02f14faf4b202468"
		application.process.session_id = "f4776ed6cfc261cc02f14faf4b202468-1300331146.777422-1336584929"
		application.icon_name = "vlc"
		module-stream-restore.id = "sink-input-by-application-name:VLC media player"

Source Output #303
	Driver: protocol-native.c
	Owner Module: 9
	Client: 668
	Source: 2
	Sample Specification: float32le 1ch 25Hz
	Channel Map: mono
	Buffer Latency: 0 usec
	Source Latency: 9200 usec
	Resample method: peaks
	Properties:
		application.id = "org.gnome.VolumeControl"
		media.name = "Peak detect"
		application.name = "GNOME Volume Control Dialog"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "16"
		application.icon_name = "multimedia-volume-control"
		application.version = "2.31.6"
		application.process.id = "32552"
		application.process.user = "dhasenan"
		application.process.host = "cerebus"
		application.process.binary = "gnome-volume-control"
		window.x11.display = ":0.0"
		application.language = "en_US.utf8"
		application.process.machine_id = "f4776ed6cfc261cc02f14faf4b202468"
		application.process.session_id = "f4776ed6cfc261cc02f14faf4b202468-1300331146.777422-1336584929"
		module-stream-restore.id = "source-output-by-application-id:org.gnome.VolumeControl"

Client #0
	Driver: module-console-kit.c
	Owner Module: 16
	Properties:
		application.name = "ConsoleKit Session /org/freedesktop/ConsoleKit/Session3"
		console-kit.session = "/org/freedesktop/ConsoleKit/Session3"

Client #1
	Driver: module-console-kit.c
	Owner Module: 16
	Properties:
		application.name = "ConsoleKit Session /org/freedesktop/ConsoleKit/Session5"
		console-kit.session = "/org/freedesktop/ConsoleKit/Session5"

Client #2
	Driver: protocol-native.c
	Owner Module: 9
	Properties:
		application.name = "GNOME Volume Control Media Keys"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "16"
		application.id = "org.gnome.VolumeControl"
		application.icon_name = "multimedia-volume-control"
		application.version = "2.32.0"
		application.process.id = "2863"
		application.process.user = "dhasenan"
		application.process.host = "cerebus"
		application.process.binary = "gnome-settings-daemon"
		window.x11.display = ":0.0"
		application.language = "en_US.utf8"
		application.process.machine_id = "f4776ed6cfc261cc02f14faf4b202468"
		application.process.session_id = "f4776ed6cfc261cc02f14faf4b202468-1300331146.777422-1336584929"

Client #7
	Driver: module-x11-xsmp.c
	Owner Module: 21
	Properties:
		application.name = "XSMP Session on gnome-session as 1069deadbfa3f7de2e13003311662511200000028150036"
		xsmp.vendor = "gnome-session"
		xsmp.client.id = "1069deadbfa3f7de2e13003311662511200000028150036"

Client #668
	Driver: protocol-native.c
	Owner Module: 9
	Properties:
		application.name = "GNOME Volume Control Dialog"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "16"
		application.id = "org.gnome.VolumeControl"
		application.icon_name = "multimedia-volume-control"
		application.version = "2.31.6"
		application.process.id = "32552"
		application.process.user = "dhasenan"
		application.process.host = "cerebus"
		application.process.binary = "gnome-volume-control"
		window.x11.display = ":0.0"
		application.language = "en_US.utf8"
		application.process.machine_id = "f4776ed6cfc261cc02f14faf4b202468"
		application.process.session_id = "f4776ed6cfc261cc02f14faf4b202468-1300331146.777422-1336584929"

Client #671
	Driver: protocol-native.c
	Owner Module: 9
	Properties:
		application.name = "VLC media player"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "16"
		application.process.id = "31751"
		application.process.user = "dhasenan"
		application.process.host = "cerebus"
		application.process.binary = "vlc"
		application.language = "en_US.utf8"
		window.x11.display = ":0.0"
		application.process.machine_id = "f4776ed6cfc261cc02f14faf4b202468"
		application.process.session_id = "f4776ed6cfc261cc02f14faf4b202468-1300331146.777422-1336584929"
		application.icon_name = "vlc"

Client #673
	Driver: protocol-native.c
	Owner Module: 9
	Properties:
		application.name = "pactl"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "16"
		application.process.id = "32594"
		application.process.user = "dhasenan"
		application.process.host = "cerebus"
		application.process.binary = "pactl"
		application.language = "en_US.utf8"
		window.x11.display = ":0.0"
		application.process.machine_id = "f4776ed6cfc261cc02f14faf4b202468"
		application.process.session_id = "f4776ed6cfc261cc02f14faf4b202468-1300331146.777422-1336584929"

Card #0
	Name: alsa_card.usb-AKM_AK5370-00-default
	Driver: module-alsa-card.c
	Owner Module: 4
	Properties:
		alsa.card = "1"
		alsa.card_name = "AK5370"
		alsa.long_card_name = "AKM              AK5370           at usb-0000:00:1a.1-1, full speed"
		alsa.driver_name = "snd_usb_audio"
		device.bus_path = "pci-0000:00:1a.1-usb-0:1:1.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/sound/card1"
		udev.id = "usb-AKM_AK5370-00-default"
		device.bus = "usb"
		device.vendor.id = "0556"
		device.vendor.name = "Asahi Kasei Microsystems Co., Ltd"
		device.product.id = "0001"
		device.product.name = "AK5370 I/F A/D Converter"
		device.serial = "AKM_AK5370"
		device.string = "1"
		device.description = "AK5370 I/F A/D Converter"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-usb"
	Profiles:
		input:analog-mono: Analog Mono Input (sinks: 0, sources: 1, priority. 1)
		off: Off (sinks: 0, sources: 0, priority. 0)
	Active Profile: input:analog-mono

Card #1
	Name: alsa_card.pci-0000_00_1b.0
	Driver: module-alsa-card.c
	Owner Module: 5
	Properties:
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xf8500000 irq 46"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "284b"
		device.product.name = "82801H (ICH8 Family) HD Audio Controller"
		device.form_factor = "internal"
		device.string = "0"
		device.description = "Internal Audio"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Profiles:
		output:analog-stereo: Analog Stereo Output (sinks: 1, sources: 0, priority. 6000)
		output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (sinks: 1, sources: 1, priority. 6060)
		input:analog-stereo: Analog Stereo Input (sinks: 0, sources: 1, priority. 60)
		off: Off (sinks: 0, sources: 0, priority. 0)
	Active Profile: output:analog-stereo+input:analog-stereo
```

---

### Post by dankegel on 2011-04-15
Same problem here.  lspci says
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)

The commands I was trying are

#!/bin/sh
set -x
MONITOR=$(pactl list | grep -A2 '^Source #' | \
    grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)
speaker-test &
pid1=$!
parec --device="$MONITOR" --verbose foo.pcm &
pid2=$!
sleep 3
kill $pid1
kill $pid2
sox -t raw -r 48000 -sLb 16 -c 2 - foo.wav < foo.pcm
# Expect to hear something here, but foo.wav is silent...
play foo.wav

---

### Post by dankegel on 2011-04-15
I should mention the bad system is an asus laptop
running ubuntu natty beta, updated.

The same test script works fine on my desktop running
ubuntu 10.10, where lspci reports
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

---

### Post by dhasenan on 2011-04-15
> **dankegel said:**
> Same problem here.  lspci says
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)

I reinstalled Ubuntu to no effect. This twigged me that it was a hardware issue. I turned off the computer, unplugged the battery, waited an hour, and then turned it on. Now it works.

Rather than waiting an hour, you can repeatedly attempt to turn your computer on. Two or three times should drain the capacitors and reset the hardware.

---

### Post by locketine on 2011-04-17
I had this exact problem and it took me a couple hours to figure out but when I did I felt like an idiot.

Your pactl output for the monitor includes this handy little bit of information.

> Mute: yes

**How I Unmuted:**
Installed pavucontrol (just try launching from terminal), launched it, went to the "Input Devices" tab, selected "Show all input devices" from the Show dropdown, found the monitor of internal analog stereo and clicked the speaker button.

You can check to see which device an application is recording on the Recording tab so make sure you have the same device set there that has your audio playing on it. This setting appears to persist through multiple application sessions :).

---

### Post by ryanov on 2012-03-15
Thanks locketine! This was exactly my problem as well. I also spent a lot of time on this!

---

### Post by IanSWilliams on 2012-03-20
Thanks everyone, mine was Muted Too!

Wasn't yesterday!

The only thing I've done different since then was leave my PC on standby overnight, and, there was a power failure while I was asleep.

Boy oh boy was I scratching my head over this!!!

---

### Post by fi2 on 2012-08-08
Same here. Spent days with struggling, and it was muted. Thanks locketine.

---

