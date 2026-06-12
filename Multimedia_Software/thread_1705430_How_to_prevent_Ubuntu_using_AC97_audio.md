---
title: "How to prevent Ubuntu using AC97 audio?"
date: 2011-03-12
forum: Multimedia Software
---

### Post by XEtedBear on 2011-03-12
I have an M-Audio Audiophile 2496 card installed in my PC. It is of far higher quality than the AC97 sound built into the VIA chipset. I want to use the M-Audio card so AC97 sound is disabled in BIOS.

When using Audacity I can record and play with the M-Audio card as I wish.

When using VLC (or any other media player), Ubuntu insists on playing through the AC97 ports - which I have disabled and which, I would have thought, was a pretty good indication that I don't want to use them.

Even when I configure VLC to use the M-Audio card  (using VLC's <tools> <preferences> <audio> <output Device> ) it still plays through the motherboard via-82xx hardware.

What nonsense is this? Surely Ubuntu cannot require me to replug my speakers when I want to switch between VLC/ Brasero etc and Audacity?


I looked at the Pulse Audio apps: good grief! Is there any human being which understand what all that is supposed to be about? I could find nothing which matched my understanding of my hardware or related in any way to what I, as an end-user, want to do with my system. Is there an interpretation of this PulseAudio function available anywhere?

---

### Post by eddier on 2011-03-12
If you have a separate sound card then disable your Motherboard sound system in the BIOS.

eddie

Sorry I see you have mentioned disabling sound via (!) the bios, allthough, you did hit f10 when leaving the bios to save the change i hope!

---

### Post by XEtedBear on 2011-03-13
> **eddier said:**
> If you have a separate sound card then disable your Motherboard sound system in the BIOS.

eddie

Sorry I see you have mentioned disabling sound via (!) the bios, allthough, you did hit f10 when leaving the bios to save the change i hope!

Yes, as you will have noticed from a careful reading of my post, disabling AC97 in BIOS is completely ignored by the Kernel. In fact when I browse the 'messages' log file (using the Log File Viewer) there is a log entry which specifically says: "VIA 82xx Audio .... enabling device (0000 -> 0001)".

On the other hand ASUS and AMI seem to think this hardware is disabled.

So it seems that this isn't my PC after all - it's owned by Linus Torvalds!

What nonsense is this?

---

