---
title: "Yet another sound problem thread..."
date: 2010-01-26
forum: Multimedia Software
---

### Post by truth is life on 2010-01-26
...this one with a bit of a twist. Today I changed over from Gnome to Xfce, and took the opportunity to clear out a lot of extra packages I had and didn't want or need. Before this, I had sound; now, I do not. Therefore, either installing essentially xubuntu or clearing out those packages must have disabled my sound. Unfortunately, I do not remember exactly which packages I uninstalled (it was over a hundred), so it would be very difficult to simply undo whichever ones were related to sound, and the Synaptic interface is not very useful wrt finding the sound-related packages (of course, apt-get is even less useful in this regard).

My lspci is as follows:
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Santa Cruz Operation Device 1043
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at fdef4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```which is not very helpful, since it just confirms I have a driver for my sound card (well, I didn't touch any of the kernel packages, so I would hope so). alsamixer reports maxed out volumes on all output channels, while my laptop's hardware also reports maxed out volumes and no muting. I also checked that I was part of the 'audio' group, added myself to it, and rebooted my computer just to be sure (it didn't help). This is obviously a bit of a tricky one.

---

### Post by Yellow Pasque on 2010-01-27
If you're getting rid of GNOME, make sure you purge all pulseaudio packages (except libpulse packages, you should keep those for dependency purposes). Also, remove any  hidden .pulse files/folders in your home directory. and remove gstreamer0.10-pulseaudio (install gstreamer0.10-alsa if it's not already installed).

You can also mark alsa-base and alsa-utils for reinstall if you're still having issues.

I love xfce and I hope you enjoy it as much as I do.

---

### Post by truth is life on 2010-01-27
> **Temüjin said:**
> If you're getting rid of GNOME, make sure you purge all pulseaudio packages (except libpulse packages, you should keep those for dependency purposes). Also, remove any  hidden .pulse files/folders in your home directory. and remove gstreamer0.10-pulseaudio (install gstreamer0.10-alsa if it's not already installed).

You can also mark alsa-base and alsa-utils for reinstall if you're still having issues.

I love xfce and I hope you enjoy it as much as I do.

Did that and it still doesn't work. What next?

And I am enjoying xfce. The default theme (& font, & text colors) is nice-looking, and the environment itself is noticeably snappier than GNOME, which is very nice considering the limited resources of this laptop.

---

### Post by Jose Catre-Vandis on 2010-01-29
Open up alsamixer from a terminal, and make sure you un-mute everything

Click on the volume icon to bring up the mixer and tick everything in sight from "Select Controls"

For good measure restart alsa:
```
sudo /etc/init.d/alsa-utils restart
```

Got sound?

---

