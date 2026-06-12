---
title: "Sound Not Working After Troubleshooting"
date: 2009-08-30
forum: Multimedia Software
---

### Post by gruurly on 2009-08-30
I've got a video file I can't get working with MPlayer; I keep on getting "Cannot find codec for audio format 0x56444152".

So before posting for assistance (Linux n00b here), I decided to work through the [Comprehensive Multimedia & Video How To]("http://ubuntuforums.org/showthread.php?t=766683"). I did, everything seemed fine - but now I have no sound whatsoever. I did before undertaking this.

So then I decided to work through the [Comprehensive Sound Problem]("http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound") guide. But I get to step 3 and I can't get any further because the ASLA list isn't up anymore.[INDENT][SIZE=1][I]"**(3)** Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver([COLOR=seagreen]green hyperlink text[/COLOR])."
[/I][/SIZE][/INDENT]cat /proc/asound/cards tells me:

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd0340000 irq 22

I'm running Ubuntu 9.04 on an Acer 3680 laptop.

Help?

---

### Post by gruurly on 2009-08-30
Ok got it working by the "Try This First" section of the how-to [here]("http://ubuntuforums.org/showthread.php?t=843012").

---

