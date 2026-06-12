---
title: "No sound again"
date: 2010-03-05
forum: Multimedia Software
---

### Post by 4thfloorstudios on 2010-03-05
Hi,
I have Ubuntu 9.10 with GNOME and KDE and again no sound. I simply logged in to GNOME and then to KDE.

Is there any simple(!) way to fix sound problems under Ubuntu once and for all? Since more than one year I have sound issues. Tried all the solutions from the forums or wikis.

This is really annoying... ](*,)

So, my idea is to use only one way (PulseAudio? Alsa?) to have sound, is that possible somehow?

---

### Post by BiggoCharley on 2010-03-05
I sure hope you get an answer to this.  I had the same problem after upgrading to 9.1.  Like you, I tried all the fixes I could find on the forums to no avail.  Happily, prior to uprading from jaunty (where I had long since solved my sound problems) I had cloned my hard drive and set the clone (on a separate drive) aside--which turned out to be one of my smarter moments.  So now I'm back to jaunty.  I'll watch this thread for new info.

---

### Post by UnicornsRock420 on 2010-03-05
Currently running Karmic Koala, I tried all this [http://ubuntuforums.org/showpost.php?p=8892809](http://ubuntuforums.org/showpost.php?p=8892809) , building the driver/plugins/libs/etc.

```
Prompt: aplay -l
aplay: device_list:223: no soundcards found...
Prompt: sudo cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC1200
Prompt: sudo lshw -class sound
  *-multimedia
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:22 memory:fe024000-fe027fff
Prompt: uname -a
Linux Host 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
```There's the slightest faint with the volume cranked sound in amarok and VLC and everything else is dead. The Mixer appears to be working fine, tried installing/uninstalling pulseaudio package, running alsaconf, no change.

Yeah I agree there's many issues with sound devices. My professional opinion is atleast in my case the hardware may be a bit too new for all the kinks to be worked out. Even then though it's still annoying as ****. I've used Linux for years now and it seems like we should be past these archaic sound daemon configuration issues. If the driver installed can't talk to my device then the Mixer should reflect that. If a sound device is already in use, wtf do I do to figure that out? lsof? top? This shouldn't be this complicated.

---

### Post by 4thfloorstudios on 2010-03-08
Hi,
at least I found out that:

When switch from KDE TO GNOME, my sound is set to mute. If I do not unmute the sound and switch back to KDE, there is no sound, even if I turn all levels up.

So, could it be that both systems access different sound settings which are partially overwritten?

@UnicornsRock420:
Hopefully my problem is not hardware related. I agree to your opionion about audio drivers ;)

---

