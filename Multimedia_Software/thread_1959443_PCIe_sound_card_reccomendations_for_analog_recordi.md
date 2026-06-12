---
title: "PCIe sound card reccomendations for analog recording"
date: 2012-04-15
forum: Multimedia Software
---

### Post by MakOwner on 2012-04-15
I am setting up a replacement for a system that records over the air FM radio.
  
The old system is a Dell PowerEdge 350, using a PCI Ensoniq 5880B sound card.  This worked like a charm with no issues.  I used a 10.04LTS minimal installation, and installed alsa-utils from the cli.
The arecord in the alsa-utils package records from the default sound device and just works.

The new system is a Dell PowerEdge 850.
The 850 has PCIe and PCIx I/O slots, so transferring the old sound card won't work. I went to Fry's and picked up the first PCIe sound card with a name I recognized - a Creative x-fi PCIe sound card.

It doesn't work of course...

So, I'm looking for a (hopefully) cheap card that the mic/line in works out of the box from a fresh install of minimal LTS install.  I don't need sound out, and there won't be any X windows installed, so no GUI tools.

Anyone have any suggestions/experience for this?

---

### Post by MakOwner on 2012-04-17
Nothing? wow.

I found an ASUS PCIe card that works out of the box with 10.04.4 LTS desktop.

Both ALSA and pulseadio get installed from the livecd.

How do I know which actually controls the sound card?


I'd prefer to load a minimal distribution and then load just what is needed to record from the mic/line-in jack...

---

### Post by bcschmerker on 2012-08-12
The [Advance LinUX Sound Architecture Project]("http://www.alsa-project.org/") supports the Asus® XONAR® Series PCI 2.2 and PCI-Express x1, except HDAV, with a [unique driver for the AV-100]("http://www.alsa-project.org/main/index.php/Matrix:Module-virtuoso") (modified from [snd-oxygen for the generic C-Media® CMI8000 series DSP's]("http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen")).  The latest Creative® DSP supported by the ALSA Project is the [CA0102]("http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1") (Sound Blaster® Audigy™ family); the CA0110 (Sound Blaster® X-Fi® MB2 and XtremeAudio) is only partially supported, and there are no drivers for either the CA20K1/CA20K2 or the bleeding-edge (as of August 2012) SoundCore3D® audio processors.

---

