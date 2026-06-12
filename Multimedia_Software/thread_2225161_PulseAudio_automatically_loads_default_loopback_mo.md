---
title: "PulseAudio automatically loads default loopback module after I load one."
date: 2014-05-20
forum: Multimedia Software
---

### Post by (O) on 2014-05-20
I am trying to stream audio from a Bluetooth source to a Bluetooth sink.  I connect the devices, get confirmation that their modules are loaded in PulseAudio, then I load the loopback module.  The loopback module is loaded, but PA loads another after that overrides mine:

26      module-loopback source="bluez_source.70_72_3C_62_49_7F" source_dont_move="true" sink_input_properties="media.role=music"

I tried commenting out the ```
load-module module-default-device-restore
``` line in etc/pulse/default.pa and restarting the daemon, but no dice.  Is there another setting I'm missing?  Or, even better, can I load my loopback module with some argument that gives it priority?

---

