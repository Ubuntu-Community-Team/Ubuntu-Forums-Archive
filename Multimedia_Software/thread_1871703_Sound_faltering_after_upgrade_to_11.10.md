---
title: "Sound faltering after upgrade to 11.10"
date: 2011-10-29
forum: Multimedia Software
---

### Post by ephialtis on 2011-10-29
I just upgraded to 11.10 and I face the following problem :

The sound is faltering all the time. By opening the sound manager I see the mute checkbox to be automatically toggled on and off all the time. 

The same happens both in Gnome and in KDE, and every time a sound is played. 

the lspci -v output is the following:
 
```
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
        Subsystem: ASUSTeK Computer Inc. Device 8326
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fbd7c000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

Any help would be appreciated.

PS. I have tried the [Sound Troubleshooting procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") but without success

---

### Post by ephialtis on 2011-10-29
I figured it out. For some reasons only one output channel was enabled and the other 3 (center, surround, side) were muted.  So if you face a similar problem run alsamixer and make sure that there are no muted channels

---

