---
title: "dmesg says vxpocket v2 fails"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by lusth on 2007-06-19
I have a Digigram vxpocket v2 CardBus audio card for my laptop. I'm trying to get it to work under Edgy. The output from dmesg reveals this error:

    ALSA ...alsa-kernel/pcmcia/vx/vxp_ops.c:101: cannot find xilinx magic word (41)

I'm running version 1.0.14rc4 of the drivers, 1.014a of the library, and 1.01.14
everything else. Also vxloader reports:

    vxloader: no VX-compatible cards found

The card operates fine under Windows XP.

Anybody seen this before?

Thanks,

john

---

### Post by ibanez88 on 2007-07-18
I got my Digigram V2 working using this older thread:

[http://ubuntuforums.org/showthread.php?t=112707&highlight=digigram](http://ubuntuforums.org/showthread.php?t=112707&highlight=digigram)

One note though I in my asound.conf I decided to give the digigram number 0 instead of 1 and I also blacklisted my onboard soundcard from modprobe.  Without this step I was able to get a test tone using the gnome sound manager but no application sound, or even gnome system sounds for that matter.

Did you download the firmware from alsa-projects.org seperately, in addition to the alsa packages?

I too got similar errors every time I tried to get the Digigram working.  I followed the above link on a freshly updated new feisty install and it just worked, seemingly out of the blue.

---

