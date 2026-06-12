---
title: "Alsa and compiling snd-usb-audio"
date: 2012-10-16
forum: Multimedia Software
---

### Post by Spazi on 2012-10-16
Hi guys, I'm really desperate on this one.
Using Ubuntu 12.04 on a Dell XPS 8000, I7 processor, 64 bit and just did a clean install.
I have an Axe FX 2 which works as a audio interface, and I would love to use it with the Ardour DAW.
the guide/thread I followed is [here]("http://forum.fractalaudio.com/axe-fx-ii-discussion/44765-anybody-tried-usb-interface-linux-yet.html"), but is meant for openSUSE 12.2
Through FXload it's possible for me to load the firmware into the interface and Ubuntu communicates with it, and with the lsusb command it even shows up and everything. I did a udev rule so that everytime I plug the interface in, it gets recognized and works.
As I've been told, the midi in and out work right away, but the audio needs some work.
I think what I need to do is recompile an ALSA driver called snd-usb-audio
This is the part where I'm lost, in the guide it talks about two files called "format.c" and "clock.c" that is suposed to be located in "/usr/share/linux-*kernelversion*/sound/usb"
Those files are not there, and my path is "/usr/src/linux-headers-3.2.0-29/sound/usb"
another file I need to find is "quirks-table.h" which I can't find either.
After all this I need to recompile the snd-usb-audio module, and I don't really know how to do that.

Am I missing some packages?

Any help or pointing me in the right direction would help me greatly!

---

