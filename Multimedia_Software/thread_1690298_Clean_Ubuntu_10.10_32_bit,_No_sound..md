---
title: "Clean Ubuntu 10.10 32 bit, No sound."
date: 2011-02-18
forum: Multimedia Software
---

### Post by billdotson on 2011-02-18
Output of sudo lshw -c sound: 
```
*-multimedia            
       description: Audio device
       product: GF104 High Definition Audio Controller
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:17 memory:f7dfc000-f7dfffff
  *-multimedia
       description: Multimedia audio controller
       product: SB0400 Audigy2 Value
       vendor: Creative Labs
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2
       resources: irq:23 ioport:ec00(size=64)

```
I had 9.04 just a few weeks ago, upgraded to 9.10 and the sound was gone. It was fixed easily by installing GNOMEmixer. I tried upgrading to 10.04, didn't work, so I did a complete reinstall of 10.10. No sound at all, through either device (HDMI audio or 5.1 speakers).

I love Ubuntu and all, so I hate to complain, but I thought this sort of thing was over as far back as 9.04, which I can't remember having any driver issues, sound issues, etc. Anyway, what is the next step?

---

### Post by billdotson on 2011-02-18
Nothing at all eh?

---

### Post by billdotson on 2011-02-19
Seriously, nobody has any idea? This is getting really annoying having no sound.

---

### Post by jsprz8382 on 2011-02-19
I have this issue too!
Same/Similar hardware also help us!

---

### Post by gruffyddd on 2011-02-20
My soundcard stopped working about 2 weeks ago - the sound has gone very quiet and fuzzy.

It may be because of this bug [here]("https://bugs.launchpad.net/ubuntu/+bug/708586"). Try rebooting into kernel 2.6.32-27-generic instead of 2.6.32-28-generic - I will be trying the same thing once I figure out how to do it.

---

### Post by trey31357 on 2011-02-20
I had the same problem - here's how I fixed it.

Install alsamixer:

sudo apt-get install gnome-alsamixer

Then open GNOME ALSA Mixer from Applications -> Sound & Video -> GNOME ALSA Mixer

Choose the tab: “SigmaTel…”

Turn on “Audigy Analog/Digital Output Jack”

That should do the trick.

---

### Post by billdotson on 2011-02-21
Hey Trey, that worked, thank you. I remember doing that to fix the sound after U upgraded from 9.04 to 9.10, but the thing I forgot to do was to check the Output Jack box. The sound works now for my Soundblaster Audigy 4. However, it would still be nice if the sound would work for the GF104 HDMI audio (nVidia GTX 460). If I can't figure that out though, at least I have sound from something.

---

