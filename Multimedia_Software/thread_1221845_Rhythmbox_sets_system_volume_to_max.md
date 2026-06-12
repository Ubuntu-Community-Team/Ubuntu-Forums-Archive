---
title: "Rhythmbox sets system volume to max"
date: 2009-07-24
forum: Multimedia Software
---

### Post by smeck on 2009-07-24
Whenever I click play in Rhythmbox, the volume is set to maximum. I mean the alsa-mixer volume so all sound increases in volume. Pidgin also have this effect om the volume control.

After playing music with Rhythmbox a while the sound will die (in all program except VLC and line-in channel) and I must kill Rhythmbox in gnome system monitor, wait a couple of seconds and start Rhythmbox again.

```
 lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

---

