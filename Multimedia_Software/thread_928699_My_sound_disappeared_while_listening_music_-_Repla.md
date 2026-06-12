---
title: "My sound disappeared while listening music - Replaced by a beep"
date: 2008-09-24
forum: Multimedia Software
---

### Post by pnero on 2008-09-24
Hello,

I'm using Ubuntu Hardy on a HP Compaq pc, and I have a Sound Blaster Live PCI card.

About one week ago, while I was happily working and listening music (I was not upgrading anything), the audio suddenly disappeared; I tried a reboot, and since then I can only hear a painful beep coming out of my speakers, everytime a sound should play (system sounds, music, etc. ).

The strange thing is that my sound card is still recognized and seen as if it had no problems at all; I still have all the volume controls, and here's the output of lspci | grep -i audio
> 02:00.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)

I also tried booting from the ubuntu live cd, but the beep remains: this makes me think my audio card is gone, because hardy and gutsy were playing sound well up to one week ago :confused:

---

### Post by pnero on 2008-09-26
bump :cool:

---

### Post by pnero on 2008-10-04
Looks like the audio card was gone - I changed it and everything works well

---

