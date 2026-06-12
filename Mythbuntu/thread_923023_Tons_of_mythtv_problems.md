---
title: "Tons of mythtv problems"
date: 2008-09-17
forum: Mythbuntu
---

### Post by SneakerElph on 2008-09-17
I've been searching google, tirelessly for a few days. I cannot for the life of me get my TV working. I'm running:

Mythbuntu 8.04
AMD 4800+
GeForce 8800GTS
Hauppauge HVR-950q USB adapter plugged into standard analog cable at Washington State University.

I've plugged it in, and compiled/installed the drivers. MythTV picks it up, but when i go to use Watch TV, the screen just blinks. Back to the main menu.

So i went to load my channels into MythTV from the Input Connections pane on mythbackend setup. I have a schedules direct account, and mythfilldatabase seems to grab the channels, and then do nothing with them because everything tells me i have no channels. I went into the input connections pane and scanned for channels, but it only scanned ATSC channels, and, as i have no antenna hooked up, just my analog cable, it found no channels. How can i make it scan my analog channels? also, the "Fetch listings from source" button does nothing. at all.

I'm really sorry if this is too much to ask or whatever, but i've been without tv for a couple months and i'm not getting anywhere close to where i want to be... mplayer dvb:// won't load up the card because I don't have a channels.conf, so i can't even see if the card works... help me please!

---

### Post by Disparu on 2008-09-18
had similar issue if you don't set the global cable type properly... IE us-cable? instead of bcast.

---

### Post by agamotto on 2008-09-18
> **Disparu said:**
> had similar issue if you don't set the global cable type properly... IE us-cable? instead of bcast.

See if this works for you:  Freq table high cable, and scan for qam-256.

---

