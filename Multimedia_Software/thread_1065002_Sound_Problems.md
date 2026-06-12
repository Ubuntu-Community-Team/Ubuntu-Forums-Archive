---
title: "Sound Problems"
date: 2009-02-09
forum: Multimedia Software
---

### Post by Lex-Man on 2009-02-09
I've downloaded and installed the latest Linux ATI driver 9.1 for my graphics card but it seems to have stopped my sound card working at all.  The card has a HDMI port which takes audio (its a Radeon[sp?] 3850).

I have tried checking the permissions for my account and make sure that I have the rights to use audio play back, which I do.

I have added the driver information to the end of the file  /etc/modules
the driver information was snd-emu10k2 for a Sound Blaster Audigy2 ZS Platinum Pro.

I got the information from.

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

I checked that the sound in alsamixer to make sure it wasn't muted.

I also tried removing and replacing the ALSA drivers.

Finally I tried setting my card as the default by modifying the /etc/modprobe.d/alsa-base

to force the creative card as my default none of this has given me any sound. Is there anything else people can suggest?

---

### Post by Lex-Man on 2009-02-10
Does anyone have any idea how I can sort this problem or is it unfixible?

---

### Post by GARoss on 2009-02-10
I see that you checked the alsamixer but did you also uncheck the Audigy Analog/Digital Output Jack?
I have an older Audigy 2 SB & got nothing until that was unchecked.
HTH
George

---

### Post by Neural oD on 2009-02-10
have a look at this thread - it's pretty comprehensive :) [http://ubuntuforums.org/showthread.php?t=205449&page=137](http://ubuntuforums.org/showthread.php?t=205449&page=137)

---

### Post by Lex-Man on 2009-02-10
> **GARoss said:**
> I see that you checked the alsamixer but did you also uncheck the Audigy Analog/Digital Output Jack?
I have an older Audigy 2 SB & got nothing until that was unchecked.
HTH
George

Ah, yeah that got it.  Thanks.

---

