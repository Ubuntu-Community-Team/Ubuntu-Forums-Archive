---
title: "Jackd2 + libffado + pulse-jack-plugin fail"
date: 2012-05-31
forum: Multimedia Software
---

### Post by QooQ on 2012-05-31
Hello,

This is my first post to a forum ever ):P!

First a short description of my system: I have a external Audio Interface (Terratec Phase X24 FW) connected to my Thinkpad T510. My OS is Ubuntu 12.04 LTS and Jackd ( 1.9.8 ) is running with libffado (2.999.0) via the firewire backend without any errors.

jackd -nPHASE -r -p1024 -t2000 -dfirewire -r48000 -p1024 -n3

My Audio System relies on Alsa and the Pulseaudio-Server therefore I need to use the Pulseaudio-Plugin for Jack - and this is where the trouble begins.

After the Jack startup the Pulseaudio Jack Sink wont appear in Qjackctl, running "pactl load-module module-jack-sink" just gives me "modul initialisation failed" (Rough German translation).

The Output of "pulseaudio --verbose" shows this error:

I: [pulseaudio] module.c: Loaded "module-alsa-card" (index: #5; argument: "device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1"").
I: [pulseaudio] module-udev-detect.c: Card /devices/pci0000:00/0000:00:1b.0/sound/card0 (alsa_card.pci-0000_00_1b.0) module loaded.
I: [pulseaudio] module-udev-detect.c: Found 2 cards.
I: [pulseaudio] module.c: Loaded "module-udev-detect" (index: #6; argument: "").
W: [pulseaudio] module-jack-sink.c: JACK error >Cannot connect to server socket err = Datei oder Verzeichnis nicht gefunden<
W: [pulseaudio] module-jack-sink.c: JACK error >Cannot connect to server socket<
jackdmp 1.9.8
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
`PHASE' server already active
Failed to open server
W: [pulseaudio] module-jack-sink.c: JACK error >Cannot connect to server socket err = Datei oder Verzeichnis nicht gefunden<
W: [pulseaudio] module-jack-sink.c: JACK error >Cannot connect to server socket<
W: [pulseaudio] module-jack-sink.c: JACK error >Cannot connect to server socket err = Datei oder Verzeichnis nicht gefunden<
W: [pulseaudio] module-jack-sink.c: JACK error >Cannot connect to server socket<
W: [pulseaudio] module-jack-sink.c: JACK error >Cannot connect to server socket err = Datei oder Verzeichnis nicht gefunden<
W: [pulseaudio] module-jack-sink.c: JACK error >Cannot connect to server socket<
W: [pulseaudio] module-jack-sink.c: JACK error >Cannot connect to server socket err = Datei oder Verzeichnis nicht gefunden<
W: [pulseaudio] module-jack-sink.c: JACK error >Cannot connect to server socket<
W: [pulseaudio] module-jack-sink.c: JACK error >Cannot connect to server socket err = Datei oder Verzeichnis nicht gefunden<
W: [pulseaudio] module-jack-sink.c: JACK error >Cannot connect to server socket<
W: [pulseaudio] module-jack-sink.c: JACK error >jack server is not running or cannot be started<
E: [pulseaudio] module-jack-sink.c: jack_client_open() failed.
E: [pulseaudio] module.c: Failed to load module "module-jack-sink" (argument: "connect=yes"): initialization failed.
I: [pulseaudio] module-jackdbus-detect.c: Failed to start module-jack-sink.
W: [pulseaudio] module-jack-source.c: JACK error >Cannot connect to server socket err = Datei oder Verzeichnis nicht gefunden<
W: [pulseaudio] module-jack-source.c: JACK error >Cannot connect to server socket<

Any Ideas?

Stefan

---

