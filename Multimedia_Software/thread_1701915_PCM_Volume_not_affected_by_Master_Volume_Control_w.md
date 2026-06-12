---
title: "PCM Volume not affected by Master Volume Control with Alsa"
date: 2011-03-07
forum: Multimedia Software
---

### Post by bartman2589 on 2011-03-07
Ok, I'm running Kubuntu 10.10 32 bit on an old DFI KT600AL motherboard based system using the onboard VIA 3058 AC97 audio (because it supports front panel audio connections and none of the add-in PCI soundcards I have do).  I have an old Gateway/STB TVPCI TV tuner card (mainly wanted the FM radio part to work) hooked up to the cd audio connector on the motherboard because the digital audio over the pci bus apparently isn't supported for this card (neither is the onboard analog mixer on the tv tuner card, I had to hack a CD-ROM audio cable and solder it to the audio outputs of the tv tuner module on the TV tuner card).  When I use the master channel as the master channel (selected in Kmix) then as one would expect it affects the output volume of all other audio playing on the system except that which is being handled by the PCM channel.  On Windows the PCM channel was also affected by the "Volume Control" slider such that ALL volume levels were reduced when moving the slider.  I'm hoping someone can help me figure out how to make it work like this on Kubuntu.

First off I should warn you that I (like many users of older hardware that is not properly supported under PulseAudio) have uninstalled PulseAudio (because it's garbage) and am using Alsa to manage my audio hardware.

I would think that there would be some way to do this using the 'amixer' application to add the PCM channel as a component of the 'Master' channel so that when the volume is turned down using the 'Master' channel control it  will affect the PCM channel too (at least the output to the speaker jack, not necessarily the capture or mix volume though), but I'm not really any good at doing things from a terminal window and the options for the amixer command kind of confused me.

Thanks to anyone who can help with this.

---

### Post by bartman2589 on 2011-03-08
Anyone?

---

