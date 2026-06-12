---
title: "Ubuntu boot locks up with Audigy2 card"
date: 2006-02-22
forum: Multimedia &amp; Video
---

### Post by Mnemonicman on 2006-02-22
It only happens when I have that card installed. It stops at [4294697.670000] Installing spdif_bug patch : Audigy 2 [SB0240]. Is it an ALSA problem?

---

### Post by Mnemonicman on 2006-06-06
Anyone? I'm now running Ubuntu 6.06 AMD64 and the problem still persists. Any help on the matter would be appreciated. How can it just lock up when it gets to installing this spdif patch?

---

### Post by Mnemonicman on 2006-06-06
Not to press the matter too much but if I can't install it to work then how do I prevent Ubuntu from trying to load the drivers for it? I followed the how-to on the ALSA site for compiling ALSA for the audigy2 but that didn't work either.

---

### Post by pjeeanah on 2006-06-08
Press Ctrl-C when Ubuntu is booting. This will prevent it from loading the sound card module. Find the correct module name of your card and place it in the hotplug blacklist. From then on you can download the latest ALSA drivers and compile them for your card.

Hope this helps.

---

### Post by Mnemonicman on 2006-06-08
Thanks for the advice but I have tried Ctrl-C to stop the sound card module from loading but now that I'm using 6.06 it's not very clear when that part comes up. Still where would I find the hotplug blacklist? That may still work.

---

