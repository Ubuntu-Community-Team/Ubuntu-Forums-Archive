---
title: "Midi with a soft synthisizer?"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by Unterseeboot_234 on 2006-12-29
Anybody know what software would let me author midi sounds using just a soft sythisizer? Everything I've found in Synaptic or Google is usually involved with connecting a card or external-usb/firewire device. My sound chip is on the PCIe nVidia card. My linux box *does* play .midi with a java program using JRE 1.3+. JACK and all its derivatives does not pipe to my sound chip. Otherwise, I'd be using Rosegarden. I'm hoping to find a program that converts .wav to .midi and/or a soft-mixer with the voice tracks shown as a gui.

Thanks, this is pretty close to the last thing I want done to finish my linux box as a graphic workstation.

---

### Post by eric71 on 2007-01-04
I don't do a lot with MIDI, but you can use the Fluidsynth DSSI or XSynth DSSI  in Rosegarden with a virtual keyboard,  VKeyBd.  That has been the easiest for me. You'll need jack running for using Synth plugins.  Select Synth plugin for the track, load the plugin (Xsynth, etc). Make sure you run VKeyBd.  You might need to connect this through Rosegarden's MIDI connections dialogue, but it usually happens automatically for me.  Then you can record MIDI through the virtual keyboard (which is also mapped to your computer keyboard).   Not the easiest to play that way, but it is the only way I know without an external MIDI device.

---

### Post by sgx on 2007-01-04
In qjackctl, the separate gui for jackd, you must select
both the instrument, and its output device, then press the connect button, in both the midi and audio panes. Also, for jackd and programs running with it, the same user must start all of them, be it root, su, or normal user...no mix and match. Also, matching numbers of 44100 (or your choice) should be set the same in all audio apps that offer the choice! For reference, I just ran commands
jackd -d alsa -r 44100
qjackctl
vkeybd
jack-dssi-host /usr/lib/dssi/fluidsynth-dssi.so

Next, in qjackctl, I select vkeybd and fluidsynth-dssi, in the midi tab of qjackctl, and press the connect button, then, clicking its audio tab, select fluidsynth-dssi and alsa_pcm (your soundchip) and press connect for them. The output should have been discovered by alsa, and placed there, ready for tunes. So then I press the Load Soundfont button on the fluidsynth interface, and choose one...Then, select an instrument from the soundfonts insrument list menu.
The Unison, and (the unrelated) Fluid soundfonts are 2 nice general midi fonts, from [www.hammersound.net](www.hammersound.net) , click
Sounds
Soundfont Library
Collections...Unison is smaller, Fluid larger, needs more memory, both have nice banks...

hmmmn...

Install dssi before any programs that use it, or apt-get
will pitch a hissyfit...jack-dssi-host, Hexter, and Whysynth are great additions, Hexter loading thousands of free yamaha DX7 patches, and Whysynth offering a couple hundred Kawai K4 type
of patches, with dozens of knobs to tweak the night away with...
If jack/qjackctl/alsa still won't see your soundchip, just
buy an Envy based soundcard, ($20-$100) and begin creating music! If you are on a laptop, a Mac compatible midi interface is best bet, because Macs demand standards compliant usb devices, so after verifying  with a thorough google search. make an informed choice.
Hope this helps!

---

### Post by Unterseeboot_234 on 2007-01-10
I thank you for your answers. I've been hacking in sound since my post on this. Awesome that it takes 3 terminal windows running to get sound. I still have fuzzy notes on my speakers and Rosegarden won't play any sound. I blame the latency issue that can be patched to load with the linux kernel. I don't want to do that. I've learned a lot. If I find anything else I will post in the Multimedia forums.

---

