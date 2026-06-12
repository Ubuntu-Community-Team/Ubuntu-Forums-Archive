---
title: "No sound in 18.04 fresh install"
date: 2019-04-03
forum: Multimedia Software
---

### Post by luftbahnfahrer on 2019-04-03
I recently installed 18.04 and I have no sound (my Dell xps-13 previously had 14.04 and the sound worked fine). 

Running lspci -v | grep -A7 -i "audio" yields:
```

mark@mark-XPS-13-9350:~$ lspci -v | grep -A7 -i "audio"00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21) (prog-if 80)
    Subsystem: Dell Sunrise Point-LP HD Audio
    Flags: bus master, fast devsel, latency 32, IRQ 16
    Memory at dc328000 (64-bit, non-prefetchable) [size=16K]
    Memory at dc300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl 
```

I've tried numerous things I've found online and nothing seems to work. Including:
[LIST]
[*]sudo alsa force-reload
[*]uninstalling and reinstalling alsa and pulseaudio
[*]going through the sound troubleshooting guide ([https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting))
[/LIST]

I'm not sure what to try next. Any help is appreciated.

---

### Post by huff2 on 2019-04-03
Open terminal, type alsamixer, then press enter. alsamixer is a program for the advanced Linux sound structure that is used to configure sound settings and adjust the sound volume. You should be able to see if a connection is muted. You will see "mm" if it is muted. Is anything muted? Also, be sure that you went to "settings" > "sound"  and have the correct output selected. Are you not getting sound from connected speakers or just your laptop speakers?

---

### Post by RedDirtDog on 2019-04-07
I had sound issues with 18.04 as well.  I ended up installing PulseAudio (after mucking around with alsa for ages).  This gave me the tools to get sound working, and the Volume Meter (for capture) shows me the 5.1 channels and if they're getting audio or not. Several times this simple little app has saved me time debugging.

---

