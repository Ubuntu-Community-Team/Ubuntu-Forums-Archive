---
title: "Could anyone help me with MIDI?"
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by Philiptheorganist on 2008-01-22
I am running Ubuntu 7.04 Feisty on an HP Pavilion 7915. I have a Yamaha P60 digital piano that I want to connect via MIDI so that I can use Horgand and possibly Rosegarden. I have a cable that goes from MIDI I/O to a joystick connector. It used to work great on Win98 SE, but when I plugged it into my Linux computer via the motherboard, I didn't know where to find its input.  Also, when I attempt to use Rosegarden for playback, I get this message: <System timer resolution is too low. Rosegarden was unable to find a high-resolution timing source for MIDI performance.
This may mean you are using a Linux system with the kernel timer resolution set too low. Please contact your Linux distributor for more information.> Is there code I need to put in the terminal to fix this and do I need to get any software or drivers? Thanks everyone for your help, as I am still a noob.

---

### Post by eric71 on 2008-01-23
The normal kernel was not intended for high quality midi work. If you install the realtime kernel via Synaptic, you won't see this error anymore. It will be the one that ends with -rt. It will appear as another choice in GRUB when you are booting.

---

### Post by rosegarden78 on 2008-01-23
I have ignored this error without compromising my music composition.  But that depends on the definition of professional.  You'll need to download these programs:

1) FluidSynth - a 3rd party MIDI synthesizer that uses sound fonts
2) Hammer Sound - a website that has free professional sound fonts
3) Audacity - multi track audio recording and effects
4) Rosegarden

To use fluidsynth read online documentation or type man fluidsynth.  You might need to find out which channel your on to load fluidsynth.  But the docs should handle all the details.

---

### Post by rosegarden78 on 2008-01-23
The MidiPort 1x1 works with Linux out of the box.  I've interfaced with easily with Rosegarden.  It accepts input from my Roland PMA-5 sequencer as well as keyboard with MIDI interface.  I think here is where the system timing gets in the way.  I think you need to score each MIDI track separately instead of all together when trying to download multi-track recording from sequencer device.  Been a while since I wrote a song though.  Timing no problem for real-time sound recording in Audacity only affects multi-track MIDI recording in rosegarden.  Fluidsynth should not be affected either.  KMid might also work.

---

### Post by Philiptheorganist on 2008-01-23
I only have 256 MB of RAM. Will an rt kernel cause trouble?
Thanks

---

### Post by Philiptheorganist on 2008-01-23
Is fluidsynth free and where can I get it? I don't have much experience with softsynths but I used to mess around with Jim Henry's Miditzer (_virtualorgan.com_) on Windows and it said it was a fluidsynth. I just plugged in the Yamaha and played.

---

