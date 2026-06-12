---
title: "sound for pno keyboard wanted"
date: 2011-01-06
forum: Multimedia Software
---

### Post by nnjond on 2011-01-06
Hi,

I have an Alesis q25 usb music keyboard. I want to plug it into my pc and get a piano sound out. Such sw as Rosegarden dose respond to the keyboard as far as the gui is concerned, -but no sound. And it's proving a nightmare to navigate!

Jack seems to be working ok and fluidsynth is installed

Can anyone ofer me a simple solution?

Thanks for your time.

---

### Post by BicyclerBoy on 2011-01-06
Have not used a USB keyboard but still had a lot of fun getting rosegarden to work..

Ubuntu does not have a midi "sound font" sfark file.
AFIAK Fluidsynth does not make any sound without the sound font file.

I found this somewhere & decompressed it with a windoze cmd-line tool in Wine.

So Rosegarden plays midi instruments via s/w synth with needs sound font library.

Works fine with normal *buntu, standard kernel & jack & pulse etc..

---

### Post by nnjond on 2011-01-06
Thanks for your interest, but I dont understand what your saying to me? Could you rephrase it please?

---

### Post by BicyclerBoy on 2011-01-06
A sound font file/library is required to synthesise any midi instrument.

Your USB keyboard just outputs midi commands.

Fluidsynth does not have a sound font library for midi. It makes a good simple tone generator without the sound font file.

The sound font file is non-free.

A windoze & OS-X licence includes a midi sound font file..

---

### Post by ajgreeny on 2011-01-06
Try installing **fluid-soundfont-gm** and **fluid-soundfont-gs**

---

### Post by nnjond on 2011-01-06
I have installed them; now I don't know what to do?

---

### Post by BicyclerBoy on 2011-01-06
I've not used the synaptic soundfonts package so thanks for that info.


Qsynth has to load the sound font (could be automatic).

Have you used Jack to connect the whole lot of stuff together ?

I think (from memory) there were 5 connections necessary.

---

