---
title: "Cannot load alsa-sink in pulseaudio"
date: 2009-01-17
forum: Multimedia Software
---

### Post by hofa on 2009-01-17
Pulseaudio won't load the module-alsa-sink module

```
14 module(s) loaded.
    index: 0
	name: <module-device-restore>
	argument: <>
	used: -1
	auto unload: no
    index: 1
	name: <module-stream-restore>
	argument: <>
	used: -1
	auto unload: no
    index: 2
	name: <module-hal-detect>
	argument: <>
	used: -1
	auto unload: no
    index: 3
	name: <module-esound-protocol-unix>
	argument: <socket=/tmp/.esd/socket>
	used: -1
	auto unload: no
    index: 4
	name: <module-native-protocol-unix>
	argument: <>
	used: -1
	auto unload: no
    index: 5
	name: <module-default-device-restore>
	argument: <>
	used: -1
	auto unload: no
    index: 6
	name: <module-rescue-streams>
	argument: <>
	used: -1
	auto unload: no
    index: 7
	name: <module-null-sink>
	argument: <sink_name=auto_null>
	used: -1
	auto unload: no
    index: 8
	name: <module-always-sink>
	argument: <>
	used: -1
	auto unload: no
    index: 9
	name: <module-suspend-on-idle>
	argument: <>
	used: -1
	auto unload: no
    index: 10
	name: <module-console-kit>
	argument: <>
	used: -1
	auto unload: no
    index: 11
	name: <module-position-event-sounds>
	argument: <>
	used: -1
	auto unload: no
    index: 12
	name: <module-gconf>
	argument: <>
	used: -1
	auto unload: no
    index: 13
	name: <module-cli-protocol-unix>
	argument: <>
	used: -1
	auto unload: no
```

These are the modules that are loaded, but I think module-alsa-sink shut be there too. The only output device I have right now is 'null'

So I tried loading the module-alsa-sink in pacmd, but after half a minute waiting, it says:

```
>>> load-module module-alsa-sink
Module load failed.
```


edit:
When I exit pacmd, I get this in my logs:
```
Jan 17 15:14:05 kasparov pulseaudio[30096]: alsa-util.c: Error opening PCM device hw:0: No such file or directory
Jan 17 15:14:05 kasparov pulseaudio[30096]: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_27d8_alsa_playback_0 tsched=1"): initialization failed.
Jan 17 15:14:05 kasparov pulseaudio[30096]: alsa-util.c: Error opening PCM device hw:0: No such file or directory
Jan 17 15:14:05 kasparov pulseaudio[30096]: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=0 source_name=alsa_input.pci_8086_27d8_alsa_capture_0 tsched=1"): initialization failed.
```

---

### Post by linuxishard on 2009-02-17
snap, this seems to be the exact issue im having, that module just doesnt wanna load. 
any ideas anybody?
i really want this to work sooo bad, i just want to output audio to my bluetooth headset and this module is all i need, but it just fails.

---

### Post by xc3RnbFO8P on 2009-02-18
Try to reinstall **Gstreamer Alsa** and **Pulse Audio**.
Remember to restart the computer.

---

### Post by LeFou on 2009-09-04
I just started encountering this error and removed/reinstall alsa and pulseaudio

but when I apt-get remove gstreamer stuff, it says it's going to yank a bunch of other things too. things I think I need, like gnome-media, gnome-applets... what's up?

---

