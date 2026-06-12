---
title: "Simple MIDI setup"
date: 2011-01-22
forum: Multimedia Software
---

### Post by lcattell on 2011-01-22
Hi

Apologies if this is in the wrong part of the forum...

I realise that there are a lot of tutorials and posts about connecting midi devices, but I have been unable to get any of the solutions to work :(

I want to be able to connect my midi guitar and play synth/piano sounds through the PC speakers. The guitar is connected via a midi-usb cable.

From what I have read, I should be able to achieve this with qjackctl and zynaddsubfx. The first problem is that I cannot connect to the jack server in realtime mode unless I sudo qjackctl from a terminal.

When connected in realtime, zynaddsubfx fails to appear under the 'audio connections' tab. As a result, I can't connect it to the system output.

I also have concerns about the midi connection. The result of amidi -l is:

Dir Device    Name
IO  hw:1,0,0  USB Midi Cable MIDI 1

This suggests that something is connected, however, the result of amidi --dump is:

ALSA lib rawmidi_hw.c:233:(snd_rawmidi_hw_open) open /dev/snd/midiC0D0 failed: No such file or directory
cannot open port "default": No such file or directory


Does anyone have a simple solution for a n00b like myself?? I've been trying to fix this for several hours, and I'm at the point of just giving up.

Thanks

p.s. I'm running Ubuntu 9.10 if that helps

---

