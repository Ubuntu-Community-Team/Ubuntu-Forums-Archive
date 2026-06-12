---
title: "Sound card numbers (seemingly) assigned randomly"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by sigdrifa on 2007-10-31
Hi all

I got a weird problem with my sound system.
Here's the output from cat /proc/asound/cards:
```

 0 [CA0106         ]: CA0106 - CA0106
                      Live! 7.1 24bit [SB0410] at 0xd880 irq 19
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe9f4000 irq 22

```

Since I want to use the Soundblaster as my default card, I created .asoundrc in my home folder like this:

```

pcm.!default {
type hw
card 0
}

ctl.!default {
type hw
card 0
}

```

I have my speakers connected to the SB, and one monitor to the NVidia.
So, here's what happens:
I boot my computer on one day, everythings fine. The next day I boot and wonder why knotify outputs sound to the monitor, and then I check /proc/asound/cards and the numbers are assigned vice versa, meaning card no. 0 is now NVidia. I reconfigure .asoundrc, log off and back on, and everything works - at least until the next reboot or the one after that.
I don't assume that the numbers really get assigned randomly, so if anyone has an idea, let me know.

Additional info on my system:
Kubuntu Gutsy Gibbon
uname -r 2.6.22-14-generic
alsa 1.0.14-1ubuntu2
lspci | grep audio 01:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
The NVidia is sound on board; the board is an MSI K9N Neo-F nF550
That's all I can think of right now, if anything else is missing, please let me know.

Thanks

---

### Post by deruberhanyok on 2007-10-31
I don't know what causes it - I have a similar problem, using an Audigy 2 ZS and leaving onboard audio enabled.

The instructions posted here were a permanent solution for me:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=multiple+sound+cards](http://ubuntuforums.org/showthread.php?t=205449&highlight=multiple+sound+cards)

I'ts under "Configuring default soundcards / stopping multiple soundcards from switching".

---

### Post by sigdrifa on 2007-11-01
Thanks, that sounds promising. I've just edited the alsa-base file. Now I'll have to wait and see. I'll post if it worked in a few days.

---

### Post by sigdrifa on 2007-11-07
Seems to have worked! Thanks a lot!

---

