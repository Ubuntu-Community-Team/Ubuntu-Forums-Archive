---
title: "where's the sound control gone?"
date: 2011-05-31
forum: Mythbuntu
---

### Post by ceejay on 2011-05-31
Hello

I'm experimenting with Ubuntu/Mythbuntu to see if I can get a software build that does what I want (yet another HTPC requirement!) and have put an installation of Mythbuntu 11.04 on an old spare PC. On another partition on the same PC I've put Ubuntu 11.04 (+ MythTV).

Being an old PC, the sound cards are a bit odd - one is built in to the mobo, the other is effectively a USB sound card (actually a microsoft branded headset!).

When I boot into Ubuntu, I can go to the Control Center (gnome-control-center), select Sound, and get an option on the "Output" tab to pick one of the two audio devices for output.

But in Mythbuntu there is no such tool: I can open Applicstions/Multimedia/Mixer, which again sees both devices, but doesn't seem to have an option to enable one over the other - so it is sticking on the internal audio card, which isn't what I want right now.

I can install the package gnome-control-center and start it from the command line, but I'm sure I must be missing something! Where is the equivalent tool in Mythbuntu?

TIA
Ceejay

---

### Post by nickrout on 2011-05-31
you configure mythtv sound from within mythtv - settings|general, about the third page, scan for devices and then choose one.

---

### Post by ceejay on 2011-05-31
ah, thanks, I had found that page but missed the fact that "Scan for audio devices" is a button (it looked like a header!).

So I did that, and the item underneath no longer just says "ALSA:default". It has a long list of ALSA:... items: it wasn't immediately obvious which of the many I needed, but the comments at the bottom of the page after I selected each one gave me a workable clue.

Thank you!

---

