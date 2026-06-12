---
title: "Tried everything I can for Sound output"
date: 2011-05-01
forum: Multimedia Software
---

### Post by vineetvb on 2011-05-01
Sound output is gone and I tried everything from the sticky post, from here [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") and several other similar posts in the forum. 

The problem seems to be the following-

1. ALSA detects the soundcard snd-hda-intel 
2. PulseAudio gives a "Dummy Output" 

Result: No output sound. 

My alsa-info.sh output is [here]("http://www.alsa-project.org/db/?f=9015bae5f446c96eb2db1e587169115e204dd410"). Judging from this seems ALSA is doing its job. 

Pulseaudio on the other hand - 

```
&#9492;&#9472;&#9508;10:42 AM|$&#9500;&#9472;> pactl stat
Currently in use: 1 blocks containing 63.9 KiB bytes total.
Allocated during whole lifetime: 403 blocks containing 3.2 MiB bytes total.
Sample cache size: 0 B
User name: vineet
Host Name: acer
Server Name: pulseaudio
Server Version: 0.9.22-24-g67d18
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: auto_null
Default Source: auto_null.monitor
Cookie: 831eb37e
```

and 

```
&#9492;&#9472;&#9508;10:55 AM|$&#9500;130&#9472;> pactl list
Module #0
	Name: module-device-restore
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the volume/mute state of devices"
		module.version = "0.9.22-24-g67d18"

Module #1
	Name: module-stream-restore
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the volume/mute/device state of streams"
		module.version = "0.9.22-24-g67d18"

Module #2
	Name: module-card-restore
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore profile of cards"
		module.version = "0.9.22-24-g67d18"

Module #3
	Name: module-augment-properties
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Augment the property sets of streams with additional static information"
		module.version = "0.9.22-24-g67d18"

Module #4
	Name: module-udev-detect
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Detect available audio hardware and load matching drivers"
		module.version = "0.9.22-24-g67d18"

Module #5
	Name: module-esound-protocol-unix
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "ESOUND protocol (UNIX sockets)"
		module.version = "0.9.22-24-g67d18"

Module #6
	Name: module-native-protocol-unix
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Native protocol (UNIX sockets)"
		module.version = "0.9.22-24-g67d18"

Module #7
	Name: module-default-device-restore
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the default sink and source"
		module.version = "0.9.22-24-g67d18"

Module #8
	Name: module-rescue-streams
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "When a sink/source is removed, try to move their streams to the default sink/source"
		module.version = "0.9.22-24-g67d18"

Module #9
	Name: module-null-sink
	Argument: sink_name=auto_null sink_properties='device.description="Dummy Output"'
	Usage counter: 0
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Clocked NULL sink"
		module.version = "0.9.22-24-g67d18"

Module #10
	Name: module-always-sink
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Colin Guthrie"
		module.description = "Always keeps at least one sink loaded even if it's a null one"
		module.version = "0.9.22-24-g67d18"

Module #11
	Name: module-intended-roles
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically set device of streams based of intended roles of devices"
		module.version = "0.9.22-24-g67d18"

Module #12
	Name: module-suspend-on-idle
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "When a sink/source is idle for too long, suspend it"
		module.version = "0.9.22-24-g67d18"

Module #13
	Name: module-console-kit
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Create a client for each ConsoleKit session of this user"
		module.version = "0.9.22-24-g67d18"

Module #14
	Name: module-position-event-sounds
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Position event sounds between L and R depending on the position on screen of the widget triggering them."
		module.version = "0.9.22-24-g67d18"

Module #15
	Name: module-x11-publish
	Argument: display=:0
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "X11 credential publisher"
		module.version = "0.9.22-24-g67d18"

Module #16
	Name: module-x11-bell
	Argument: display=:0 sample=bell.ogg
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "X11 bell interceptor"
		module.version = "0.9.22-24-g67d18"

Module #17
	Name: module-x11-cork-request
	Argument: display=:0
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Synthesize X11 media key events when cork/uncork is requested"
		module.version = "0.9.22-24-g67d18"

Module #18
	Name: module-x11-xsmp
	Argument: display=:0 session_manager=local/acer:@/tmp/.ICE-unix/1397,unix/acer:/tmp/.ICE-unix/1397
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "X11 session management"
		module.version = "0.9.22-24-g67d18"

Sink #0
	State: SUSPENDED
	Name: auto_null
	Description: Dummy Output
	Driver: module-null-sink.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 9
	Mute: no
	Volume: 0: 150% 1: 150%
	        0: 10.57 dB 1: 10.57 dB
	        balance 0.00
	Base Volume: 100%
	             0.00 dB
	Monitor Source: auto_null.monitor
	Latency: 0 usec, configured 0 usec
	Flags: DECIBEL_VOLUME LATENCY 
	Properties:
		device.description = "Dummy Output"
		device.class = "abstract"
		device.icon_name = "audio-card"

Source #0
	State: SUSPENDED
	Name: auto_null.monitor
	Description: Monitor of Dummy Output
	Driver: module-null-sink.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 9
	Mute: no
	Volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	Base Volume: 100%
	             0.00 dB
	Monitor of Sink: auto_null
	Latency: 0 usec, configured 0 usec
	Flags: DECIBEL_VOLUME LATENCY 
	Properties:
		device.description = "Monitor of Dummy Output"
		device.class = "monitor"
		device.icon_name = "audio-input-microphone"

Client #0
	Driver: module-console-kit.c
	Owner Module: 13
	Properties:
		application.name = "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
		console-kit.session = "/org/freedesktop/ConsoleKit/Session1"

Client #1
	Driver: protocol-native.c
	Owner Module: 6
	Properties:
		application.name = "GNOME Volume Control Media Keys"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "16"
		application.id = "org.gnome.VolumeControl"
		application.icon_name = "multimedia-volume-control"
		application.version = "2.32.1"
		application.process.id = "1454"
		application.process.user = "vineet"
		application.process.host = "acer"
		application.process.binary = "gnome-settings-daemon"
		window.x11.display = ":0"
		application.language = "en_US.UTF-8"
		application.process.machine_id = "0f7a9b147cb2388376a240d64cfecc2b"
		application.process.session_id = "0f7a9b147cb2388376a240d64cfecc2b-1304264423.191405-1057768068"

Client #6
	Driver: module-x11-xsmp.c
	Owner Module: 18
	Properties:
		application.name = "XSMP Session on gnome-session as 105c3f1af91685c03613042644434636000000013970049"
		xsmp.vendor = "gnome-session"
		xsmp.client.id = "105c3f1af91685c03613042644434636000000013970049"

Client #41
	Driver: protocol-native.c
	Owner Module: 6
	Properties:
		application.name = "pactl"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "16"
		application.process.id = "2359"
		application.process.user = "vineet"
		application.process.host = "acer"
		application.process.binary = "pactl"
		application.language = "en_US.UTF-8"
		window.x11.display = ":0.0"
		application.process.machine_id = "0f7a9b147cb2388376a240d64cfecc2b"
		application.process.session_id = "0f7a9b147cb2388376a240d64cfecc2b-1304264423.191405-1057768068"

```

So seems to me that pulseaudio doesn't know where my soundcard is. 

pactl load-module module-detect
pactl load-module module-udev-detect
pactl load-module module-hal-detect
all fail to initialize. 

Other relevant info: Ubuntu 11.04, Acer Aspire 4520 laptop, No prior history of sound problems. Problems started sometime after a kernel update while I was using 10.10. Upgraded to 11.04 a couple of days back. No change in the audio situation. I have tried everything possible to me for about 4 days now with no success. 

Any help is appreciated.

---

### Post by vineetvb on 2011-05-03
No avail yet. Re-installed OS. Went back to 10.04 (when it was working) still nothing. I have temporarily switched to Windows and running ubuntu on a virtual box. Sound works fine in Windows.

---

### Post by lidex on 2011-05-04
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by lkjoel on 2011-05-04
> **vineetvb said:**
> No avail yet. Re-installed OS. Went back to 10.04 (when it was working) still nothing. I have temporarily switched to Windows and running ubuntu on a virtual box. Sound works fine in Windows.
Try Fix your sound! in my signature.
Then use Post-Fix you sound! in my signature.

---

