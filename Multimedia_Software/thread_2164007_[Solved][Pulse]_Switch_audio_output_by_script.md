---
title: "[Solved][Pulse] Switch audio output by script"
date: 2013-07-20
forum: Multimedia Software
---

### Post by LastStarDust on 2013-07-20
Hello,
I usually switch between two different audio outputs: an analog jack-audio output and a digital optical output.
I'd be glad to perform such a task by script instead of doing it every time from the gui:

[B]Audio Preferences->Hardware->Internal Audio->Stereo analogico output
Audio Preferences->Hardware->Internal Audio->Stereo digitale (IEC958) output[/B]

I got to know that I should use **pacmd** to change sink. But through *pacmd list-sinks* it is always listed only the current sink and nothing else.
If the current sink is *alsa_output.pci-0000_00_1b.0.analog-stereo* and I try to set *alsa_output.pci-0000_00_1b.0.iec958-stereo* I get an error
```
Welcome to PulseAudio! Use "help" for usage information.
>>> Sink alsa_output.pci-0000_00_1b.0.iec958-stereo does not exist.
```
and viceversa.

I also tried the script [http://marginalhacks.com/bin/pulse-switch-out](http://marginalhacks.com/bin/pulse-switch-out) but I always get:
```
$ ruby ./changesynk
ERROR: Only one sink found


Usage:  change [sink]
  Switch sound playback device for ALSA/pulseaudio


    [sink]   Specify sink number to use (see 'pacmd list-sinks')

```
Thanks

---

### Post by LastStarDust on 2013-07-31
Please help me. I can't figure out how to solve the issue.

---

### Post by Yellow Pasque on 2013-07-31
Can you give the output from:
```
pactl list
```

I'm thinking maybe you need to use set-sink-port

---

### Post by LastStarDust on 2013-08-02
Here the output. I'm sorry it is in Italian ...

```
Modulo #0
	Nome: module-device-restore
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the volume/mute state of devices"
		module.version = "1.1"


Modulo #1
	Nome: module-stream-restore
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the volume/mute/device state of streams"
		module.version = "1.1"


Modulo #2
	Nome: module-card-restore
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore profile of cards"
		module.version = "1.1"


Modulo #3
	Nome: module-augment-properties
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "Augment the property sets of streams with additional static information"
		module.version = "1.1"


Modulo #4
	Nome: module-alsa-card
	Argomento: device_id="1" name="pci-0000_01_00.1" card_name="alsa_card.pci-0000_01_00.1" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1"
	Contatore utilizzi: 0
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "ALSA Card"
		module.version = "1.1"


Modulo #5
	Nome: module-alsa-card
	Argomento: device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1"
	Contatore utilizzi: 1
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "ALSA Card"
		module.version = "1.1"


Modulo #6
	Nome: module-udev-detect
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "Detect available audio hardware and load matching drivers"
		module.version = "1.1"


Modulo #7
	Nome: module-bluetooth-discover
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Joao Paulo Rechi Vita"
		module.description = "Detect available bluetooth audio devices and load bluetooth audio drivers"
		module.version = "1.1"


Modulo #8
	Nome: module-native-protocol-unix
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "Native protocol (UNIX sockets)"
		module.version = "1.1"


Modulo #9
	Nome: module-gconf
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "GConf Adapter"
		module.version = "1.1"


Modulo #10
	Nome: module-default-device-restore
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the default sink and source"
		module.version = "1.1"


Modulo #11
	Nome: module-rescue-streams
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "When a sink/source is removed, try to move their streams to the default sink/source"
		module.version = "1.1"


Modulo #12
	Nome: module-always-sink
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Colin Guthrie"
		module.description = "Mantiene sempre almeno un sink caricato anche se è nullo"
		module.version = "1.1"


Modulo #13
	Nome: module-intended-roles
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "Automatically set device of streams based of intended roles of devices"
		module.version = "1.1"


Modulo #14
	Nome: module-suspend-on-idle
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "When a sink/source is idle for too long, suspend it"
		module.version = "1.1"


Modulo #15
	Nome: module-console-kit
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "Create a client for each ConsoleKit session of this user"
		module.version = "1.1"


Modulo #16
	Nome: module-position-event-sounds
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "Position event sounds between L and R depending on the position on screen of the widget triggering them."
		module.version = "1.1"


Modulo #17
	Nome: module-filter-heuristics
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Colin Guthrie"
		module.description = "Detect when various filters are desirable"
		module.version = "1.1"


Modulo #18
	Nome: module-filter-apply
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Colin Guthrie"
		module.description = "Load filter sinks automatically when needed"
		module.version = "1.1"


Modulo #19
	Nome: module-switch-on-port-available
	Argomento: 
	Contatore utilizzi: N/D
	Proprietà:
		


Modulo #20
	Nome: module-x11-publish
	Argomento: display=:0
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "X11 credential publisher"
		module.version = "1.1"


Modulo #21
	Nome: module-x11-bell
	Argomento: display=:0 sample=bell.ogg
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "X11 bell interceptor"
		module.version = "1.1"


Modulo #22
	Nome: module-x11-cork-request
	Argomento: display=:0
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "Synthesize X11 media key events when cork/uncork is requested"
		module.version = "1.1"


Modulo #23
	Nome: module-x11-xsmp
	Argomento: display=:0 session_manager=local/zion:@/tmp/.ICE-unix/2573,unix/zion:/tmp/.ICE-unix/2573
	Contatore utilizzi: N/D
	Proprietà:
		module.author = "Lennart Poettering"
		module.description = "X11 session management"
		module.version = "1.1"


Sink #2
	Stato: RUNNING
	Nome: alsa_output.pci-0000_00_1b.0.iec958-stereo
	Descrizione: Audio interno Stereo digitale (IEC958)
	Driver: module-alsa-card.c
	Specifica di campionamento: s32le ch 2 44100 Hz
	Mappa dei canali: front-left,front-right
	Modulo di appartenenza: 5
	Muto: no
	Volume: 0: 100% 1: 100%
	        0: 0,00 dB 1: 0,00 dB
	        bilanciamento 0,00
	Volume base: 100%
	             0,00 dB
	Monitor del sink: alsa_output.pci-0000_00_1b.0.iec958-stereo.monitor
	Latenza: 62345 microsec, configurata 90000 microsec
	Flag: HARDWARE HW_MUTE_CTRL DECIBEL_VOLUME LATENCY SET_FORMATS 
	Proprietà:
		alsa.resolution_bits = "32"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "ALC889 Digital"
		alsa.id = "ALC889 Digital"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "1"
		alsa.card = "0"
		alsa.card_name = "HDA Intel MID"
		alsa.long_card_name = "HDA Intel MID at 0xfbff8000 irq 52"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
		device.form_factor = "internal"
		device.string = "iec958:0"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "iec958-stereo"
		device.profile.description = "Stereo digitale (IEC958)"
		device.description = "Audio interno Stereo digitale (IEC958)"
		alsa.mixer_name = "Realtek ALC889"
		alsa.components = "HDA:10ec0889,1458a022,00100004"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Porte:
		iec958-stereo-output: Output digitale (S/PDIF) (priority: 0)
	Porta attiva: iec958-stereo-output
	Formati:
		pcm


Sorgente #2
	Stato: IDLE
	Nome: alsa_output.pci-0000_00_1b.0.iec958-stereo.monitor
	Descrizione: Monitor of Audio interno Stereo digitale (IEC958)
	Driver: module-alsa-card.c
	Specifica di campionamento: s32le ch 2 44100 Hz
	Mappa dei canali: front-left,front-right
	Modulo di appartenenza: 5
	Muto: no
	Volume: 0: 100% 1: 100%
	        0: 0,00 dB 1: 0,00 dB
	        bilanciamento 0,00
	Volume base: 100%
	             0,00 dB
	Monitor del sink: alsa_output.pci-0000_00_1b.0.iec958-stereo
	Latenza: 0 microsec, configurata 185759 microsec
	Flag: DECIBEL_VOLUME LATENCY 
	Proprietà:
		device.description = "Monitor of Audio interno Stereo digitale (IEC958)"
		device.class = "monitor"
		alsa.card = "0"
		alsa.card_name = "HDA Intel MID"
		alsa.long_card_name = "HDA Intel MID at 0xfbff8000 irq 52"
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
	Formati:
		pcm


Sink d'ingresso #2
	Driver: protocol-native.c
	Modulo di appartenenza: 8
	Client: 12
	Sink: 2
	Specifica di campionamento: s16le ch 2 44100 Hz
	Mappa dei canali: front-left,front-right
	Formato: pcm, format.sample_format = "\"s16le\""  format.channels = "2"  format.rate = "44100"  format.channel_map = "\"front-left,front-right\""
	Muto: no
	Volume: 0: 100% 1: 100%
	        0: 0,00 dB 1: 0,00 dB
	        bilanciamento 0,00
	Latenza buffer: 110000 microsec
	Latenza sink: 62172 microsec
	Metodo di ricampionamento: copy
	Proprietà:
		media.name = "«Bugle Call Rag» di «Benny Goodman & His Orchestra»"
		application.name = "Rhythmbox"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "26"
		media.role = "music"
		application.process.id = "3109"
		application.process.user = "neo"
		application.process.host = "zion"
		application.process.binary = "rhythmbox"
		application.icon_name = "rhythmbox"
		application.language = "it_IT.UTF-8"
		window.x11.display = ":0"
		application.process.machine_id = "6adc3d171648a4d2d585f94200000317"
		application.process.session_id = "6adc3d171648a4d2d585f94200000317-1375431346.501154-1999405435"
		module-stream-restore.id = "sink-input-by-media-role:music"
		media.title = "Bugle Call Rag "
		media.artist = "Benny Goodman & His Orchestra"


Client #0
	Driver: module-console-kit.c
	Modulo di appartenenza: 15
	Proprietà:
		application.name = "ConsoleKit Session /org/freedesktop/ConsoleKit/Session2"
		console-kit.session = "/org/freedesktop/ConsoleKit/Session2"


Client #1
	Driver: protocol-native.c
	Modulo di appartenenza: 8
	Proprietà:
		application.name = "GNOME Volume Control Media Keys"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "26"
		application.id = "org.gnome.VolumeControl"
		application.icon_name = "multimedia-volume-control"
		application.version = "3.4.2"
		application.process.id = "2633"
		application.process.user = "neo"
		application.process.host = "zion"
		application.process.binary = "gnome-settings-daemon"
		application.language = "it_IT.UTF-8"
		window.x11.display = ":0"
		application.process.machine_id = "6adc3d171648a4d2d585f94200000317"
		application.process.session_id = "6adc3d171648a4d2d585f94200000317-1375431346.501154-1999405435"


Client #2
	Driver: protocol-native.c
	Modulo di appartenenza: 8
	Proprietà:
		application.name = "GNOME Shell"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "26"
		application.id = "org.gnome.Shell"
		application.process.id = "2656"
		application.process.user = "neo"
		application.process.host = "zion"
		application.process.binary = "gnome-shell"
		application.language = "it_IT.UTF-8"
		window.x11.display = ":0"
		application.process.machine_id = "6adc3d171648a4d2d585f94200000317"
		application.process.session_id = "6adc3d171648a4d2d585f94200000317-1375431346.501154-1999405435"


Client #7
	Driver: module-x11-xsmp.c
	Modulo di appartenenza: 23
	Proprietà:
		application.name = "XSMP Session on gnome-session as 10d040b4a38f3226b6137543136110125400000025730057"
		xsmp.vendor = "gnome-session"
		xsmp.client.id = "10d040b4a38f3226b6137543136110125400000025730057"


Client #8
	Driver: protocol-native.c
	Modulo di appartenenza: 8
	Proprietà:
		application.name = "GNOME Shell Volume Control"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "26"
		application.id = "org.gnome.VolumeControl"
		application.icon_name = "multimedia-volume-control"
		application.version = "3.4.1"
		application.process.id = "2656"
		application.process.user = "neo"
		application.process.host = "zion"
		application.process.binary = "gnome-shell"
		application.language = "it_IT.UTF-8"
		window.x11.display = ":0"
		application.process.machine_id = "6adc3d171648a4d2d585f94200000317"
		application.process.session_id = "6adc3d171648a4d2d585f94200000317-1375431346.501154-1999405435"


Client #9
	Driver: protocol-native.c
	Modulo di appartenenza: 8
	Proprietà:
		application.name = "Chrome input"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "26"
		application.process.id = "2680"
		application.process.user = "neo"
		application.process.host = "zion"
		application.process.binary = "chrome"
		window.x11.display = ":0"
		application.language = "it_IT.UTF-8"
		application.process.machine_id = "6adc3d171648a4d2d585f94200000317"
		application.process.session_id = "6adc3d171648a4d2d585f94200000317-1375431346.501154-1999405435"


Client #10
	Driver: protocol-native.c
	Modulo di appartenenza: 8
	Proprietà:
		application.name = "GNOME Shell"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "26"
		window.x11.display = ":0"
		window.x11.screen = "0"
		application.process.id = "2656"
		application.process.user = "neo"
		application.process.host = "zion"
		application.process.binary = "gnome-shell"
		application.language = "it_IT.UTF-8"
		application.process.machine_id = "6adc3d171648a4d2d585f94200000317"
		application.process.session_id = "6adc3d171648a4d2d585f94200000317-1375431346.501154-1999405435"


Client #12
	Driver: protocol-native.c
	Modulo di appartenenza: 8
	Proprietà:
		application.name = "Rhythmbox"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "26"
		media.role = "music"
		application.process.id = "3109"
		application.process.user = "neo"
		application.process.host = "zion"
		application.process.binary = "rhythmbox"
		application.icon_name = "rhythmbox"
		application.language = "it_IT.UTF-8"
		window.x11.display = ":0"
		application.process.machine_id = "6adc3d171648a4d2d585f94200000317"
		application.process.session_id = "6adc3d171648a4d2d585f94200000317-1375431346.501154-1999405435"


Client #14
	Driver: protocol-native.c
	Modulo di appartenenza: 8
	Proprietà:
		application.name = "pactl"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "26"
		application.process.id = "3341"
		application.process.user = "neo"
		application.process.host = "zion"
		application.process.binary = "pactl"
		application.language = "it_IT.UTF-8"
		window.x11.display = ":0"
		application.process.machine_id = "6adc3d171648a4d2d585f94200000317"
		application.process.session_id = "6adc3d171648a4d2d585f94200000317-1375431346.501154-1999405435"


Scheda #0
	Nome: alsa_card.pci-0000_01_00.1
	Driver: module-alsa-card.c
	Modulo di appartenenza: 4
	Proprietà:
		alsa.card = "1"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xf9ffc000 irq 17"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:01:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "NVIDIA Corporation"
		device.product.name = "GF104 High Definition Audio Controller"
		device.string = "1"
		device.description = "GF104 High Definition Audio Controller"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Profili:
		output:hdmi-stereo: Digital Stereo (HDMI) output (sinks: 1, sources: 0, priority. 5400)
		output:hdmi-surround: Digital Surround 5.1 (HDMI) output (sinks: 1, sources: 0, priority. 300)
		output:hdmi-stereo-extra1: Digital Stereo (HDMI) output (sinks: 1, sources: 0, priority. 5200)
		output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI) output (sinks: 1, sources: 0, priority. 100)
		output:hdmi-stereo-extra2: Digital Stereo (HDMI) output (sinks: 1, sources: 0, priority. 5200)
		output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI) output (sinks: 1, sources: 0, priority. 100)
		output:hdmi-stereo-extra3: Digital Stereo (HDMI) output (sinks: 1, sources: 0, priority. 5200)
		output:hdmi-surround-extra3: Digital Surround 5.1 (HDMI) output (sinks: 1, sources: 0, priority. 100)
		off: Spento (sinks: 0, sources: 0, priority. 0)
	Profilo attivo: off
	Porte:
		hdmi-output-0: HDMI / DisplayPort (priorità 5900)
			Parte dei profili: output:hdmi-stereo, output:hdmi-surround
		hdmi-output-1: HDMI / DisplayPort 2 (priorità 5800)
			Parte dei profili: output:hdmi-stereo-extra1, output:hdmi-surround-extra1
		hdmi-output-2: HDMI / DisplayPort 3 (priorità 5700)
			Parte dei profili: output:hdmi-stereo-extra2, output:hdmi-surround-extra2
		hdmi-output-3: HDMI / DisplayPort 4 (priorità 5600)
			Parte dei profili: output:hdmi-stereo-extra3, output:hdmi-surround-extra3


Scheda #1
	Nome: alsa_card.pci-0000_00_1b.0
	Driver: module-alsa-card.c
	Modulo di appartenenza: 5
	Proprietà:
		alsa.card = "0"
		alsa.card_name = "HDA Intel MID"
		alsa.long_card_name = "HDA Intel MID at 0xfbff8000 irq 52"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
		device.form_factor = "internal"
		device.string = "0"
		device.description = "Audio interno"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Profili:
		output:analog-stereo: Stereo analogico output (sinks: 1, sources: 0, priority. 6000)
		output:analog-stereo+input:analog-stereo: Duplex stereo analogico (sinks: 1, sources: 1, priority. 6060)
		output:analog-stereo+input:iec958-stereo: Stereo analogico output + Stereo digitale (IEC958) input (sinks: 1, sources: 1, priority. 6055)
		output:analog-surround-40: Surround analogico 4.0 output (sinks: 1, sources: 0, priority. 700)
		output:analog-surround-40+input:analog-stereo: Surround analogico 4.0 output + Stereo analogico input (sinks: 1, sources: 1, priority. 760)
		output:analog-surround-40+input:iec958-stereo: Surround analogico 4.0 output + Stereo digitale (IEC958) input (sinks: 1, sources: 1, priority. 755)
		output:analog-surround-41: Surround analogico 4.1 output (sinks: 1, sources: 0, priority. 800)
		output:analog-surround-41+input:analog-stereo: Surround analogico 4.1 output + Stereo analogico input (sinks: 1, sources: 1, priority. 860)
		output:analog-surround-41+input:iec958-stereo: Surround analogico 4.1 output + Stereo digitale (IEC958) input (sinks: 1, sources: 1, priority. 855)
		output:analog-surround-50: Surround analogico 5.0 output (sinks: 1, sources: 0, priority. 700)
		output:analog-surround-50+input:analog-stereo: Surround analogico 5.0 output + Stereo analogico input (sinks: 1, sources: 1, priority. 760)
		output:analog-surround-50+input:iec958-stereo: Surround analogico 5.0 output + Stereo digitale (IEC958) input (sinks: 1, sources: 1, priority. 755)
		output:analog-surround-51: Surround analogico 5.1 output (sinks: 1, sources: 0, priority. 800)
		output:analog-surround-51+input:analog-stereo: Surround analogico 5.1 output + Stereo analogico input (sinks: 1, sources: 1, priority. 860)
		output:analog-surround-51+input:iec958-stereo: Surround analogico 5.1 output + Stereo digitale (IEC958) input (sinks: 1, sources: 1, priority. 855)
		output:analog-surround-71: Analog Surround 7.1 output (sinks: 1, sources: 0, priority. 700)
		output:analog-surround-71+input:analog-stereo: Analog Surround 7.1 output + Stereo analogico input (sinks: 1, sources: 1, priority. 760)
		output:analog-surround-71+input:iec958-stereo: Analog Surround 7.1 output + Stereo digitale (IEC958) input (sinks: 1, sources: 1, priority. 755)
		output:iec958-stereo: Stereo digitale (IEC958) output (sinks: 1, sources: 0, priority. 5500)
		output:iec958-stereo+input:analog-stereo: Stereo digitale (IEC958) output + Stereo analogico input (sinks: 1, sources: 1, priority. 5560)
		output:iec958-stereo+input:iec958-stereo: Duplex stereo digitale (IEC958) (sinks: 1, sources: 1, priority. 5555)
		input:analog-stereo: Stereo analogico input (sinks: 0, sources: 1, priority. 60)
		input:iec958-stereo: Stereo digitale (IEC958) input (sinks: 0, sources: 1, priority. 55)
		off: Spento (sinks: 0, sources: 0, priority. 0)
	Profilo attivo: output:iec958-stereo
	Porte:
		analog-output: Uscita analogica (priorità 9900)
			Parte dei profili: output:analog-stereo, output:analog-stereo+input:analog-stereo, output:analog-stereo+input:iec958-stereo, output:analog-surround-40, output:analog-surround-40+input:analog-stereo, output:analog-surround-40+input:iec958-stereo, output:analog-surround-41, output:analog-surround-41+input:analog-stereo, output:analog-surround-41+input:iec958-stereo, output:analog-surround-50, output:analog-surround-50+input:analog-stereo, output:analog-surround-50+input:iec958-stereo, output:analog-surround-51, output:analog-surround-51+input:analog-stereo, output:analog-surround-51+input:iec958-stereo, output:analog-surround-71, output:analog-surround-71+input:analog-stereo, output:analog-surround-71+input:iec958-stereo
		analog-output-headphones: Cuffie analogiche (priorità 9000)
			Parte dei profili: output:analog-stereo, output:analog-stereo+input:analog-stereo, output:analog-stereo+input:iec958-stereo
		analog-input-microphone-front: Microfono anteriore (priorità 8500)
			Parte dei profili: output:analog-stereo+input:analog-stereo, output:analog-surround-40+input:analog-stereo, output:analog-surround-41+input:analog-stereo, output:analog-surround-50+input:analog-stereo, output:analog-surround-51+input:analog-stereo, output:analog-surround-71+input:analog-stereo, output:iec958-stereo+input:analog-stereo, input:analog-stereo
		analog-input-microphone-rear: Microfono posteriore (priorità 8200)
			Parte dei profili: output:analog-stereo+input:analog-stereo, output:analog-surround-40+input:analog-stereo, output:analog-surround-41+input:analog-stereo, output:analog-surround-50+input:analog-stereo, output:analog-surround-51+input:analog-stereo, output:analog-surround-71+input:analog-stereo, output:iec958-stereo+input:analog-stereo, input:analog-stereo
		analog-input-linein: Line In (priorità 8100)
			Parte dei profili: output:analog-stereo+input:analog-stereo, output:analog-surround-40+input:analog-stereo, output:analog-surround-41+input:analog-stereo, output:analog-surround-50+input:analog-stereo, output:analog-surround-51+input:analog-stereo, output:analog-surround-71+input:analog-stereo, output:iec958-stereo+input:analog-stereo, input:analog-stereo
		iec958-stereo-input: iec958-stereo-input (priorità 0)
			Parte dei profili: output:analog-stereo+input:iec958-stereo, output:analog-surround-40+input:iec958-stereo, output:analog-surround-41+input:iec958-stereo, output:analog-surround-50+input:iec958-stereo, output:analog-surround-51+input:iec958-stereo, output:analog-surround-71+input:iec958-stereo, output:iec958-stereo+input:iec958-stereo, input:iec958-stereo
		iec958-stereo-output: Output digitale (S/PDIF) (priorità 0)
			Parte dei profili: output:iec958-stereo, output:iec958-stereo+input:analog-stereo, output:iec958-stereo+input:iec958-stereo



```

---

### Post by Yellow Pasque on 2013-08-02
Something like...
```
pactl set-card-profile 1 output:iec958-stereo
```

---

### Post by LastStarDust on 2013-08-02
> **Temüjin said:**
> Something like...
```
pactl set-card-profile 1 output:iec958-stereo
```

Thanks a lot. It did work like a charm.
Solved!

---

### Post by LastStarDust on 2013-08-02
I'd like to ask you yet another question.
When I switch to digital the analog exit shut up. But when I switch again to analog, digital out keeps playing in parallel.
To make a long story short, digital output is always on, no matter any other option. 
I have to switch off the amplifier (to witch digital output is plugged) in order to shut it up.
In windows 7 this don't happen.
Thanks in advance.

---

### Post by Yellow Pasque on 2013-08-02
Try using this script (remember to make the file executable with 'chmod +x script.sh'):

```
#!/bin/sh

analog="`pactl list cards | grep attivo | grep analog`"
pactl set-card-profile alsa_card.pci-0000_00_1b.0 off
if [ "$analog" ]
then
 pactl set-card-profile alsa_card.pci-0000_00_1b.0 output:iec958-stereo
else
 pactl set-card-profile alsa_card.pci-0000_00_1b.0 output:analog-stereo
fi
```

---

### Post by Yellow Pasque on 2013-08-02
Note: I edited the last post because the original script wasn't correct.

---

### Post by LastStarDust on 2013-08-02
The switch works ... but digital output doesn't turn off when analog is set.

---

### Post by Yellow Pasque on 2013-08-02
Hmm. Maybe there's something at the driver level controlling that. Can you give alsainfo? [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by LastStarDust on 2013-08-02
[http://www.alsa-project.org/db/?f=15b65c0275a0c03eafba4aaab788cfa069c100f9](http://www.alsa-project.org/db/?f=15b65c0275a0c03eafba4aaab788cfa069c100f9)

---

### Post by Yellow Pasque on 2013-08-03
Does this command turn off the Digital Output?
```
amixer set 'IEC958 Output',0 'Playback' 'off'
```

If so, you could incorporate it into the script
```
#!/bin/sh

analog="`pactl list cards | grep attivo | grep analog`"
if [ "$analog" ]
then
 pactl set-card-profile alsa_card.pci-0000_00_1b.0 output:iec958-stereo
 amixer set 'IEC958 Output',0 'Playback' 'on'
else
 pactl set-card-profile alsa_card.pci-0000_00_1b.0 output:analog-stereo
 amixer set 'IEC958 Output',0 'Playback' 'off'
fi
```

---

### Post by LastStarDust on 2013-08-04
Many thanks.
For the whole month of August I'll be outdoors so I'm going to check on September.
Good holidays

---

### Post by LastStarDust on 2013-09-13
It worked like a charm. Thanks for everything. I felt one more time Ubuntu community is still the best!

---

