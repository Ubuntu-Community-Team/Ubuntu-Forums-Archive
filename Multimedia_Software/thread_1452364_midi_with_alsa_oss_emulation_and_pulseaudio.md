---
title: "midi with alsa oss emulation and pulseaudio"
date: 2010-04-11
forum: Multimedia Software
---

### Post by odierick on 2010-04-11
Hi!

I'm under Ubuntu 8.04 LTS Hardy Heron using pulseaudio. I've got 2 soundcards : one internal AC97 7.1 without midi (card 0 in ALSA) and a PCI C-MEDIA 2.1 with OPL3 midi (card 3 in ALSA) I have sound in most ALSA or OSS applications with full 7.1 + 2.1 duplex. I have MIDI playback in any ALSA MIDI players (client 29:0 in ALSA).

I'm trying to run Final Doom for W95 on WINE with OSS driver.
I have sound effects but no MIDI music. I tryed with padsp and aoss wrappers.

I know I can use ALSA driver in wine or timidity, but I would rather use padsp + hardware MIDI if possible.

How do I configure ALSA OSS emulation for MIDI playback and check that it's working ? I tryed playmidi but whatever I told it, it couldn't find any midi device.

Anyone thoughts? :)

---

### Post by sirzeta on 2010-05-02
check first if you have the midi hardware enabled


aconnect -o


Greets.

---

### Post by odierick on 2012-09-12
Hi,

I have since upgraded to Lucid Lynx. I can't remember if I got it working in Hardy Heron or not.

Newer WINE works fine with ALSA and pulseaudio so I don't have to use OSS emulation anymore and hardware MIDI is working fine.

Thread marked as solved.

Olivier F. R. Dierick

---

