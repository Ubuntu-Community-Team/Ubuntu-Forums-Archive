---
title: "mythbuntu 16.04 no sound through hdmi"
date: 2016-07-11
forum: Multimedia Software
---

### Post by zapstrap on 2016-07-11
I have an asus p8h67-m pro motherboard with an i3 in it. I disabled on-board hd audio because I have an nvidia card installed with hdmi output. I know the card works because it was previously working on a mythbuntu 14.04 machine with a core2 processor. I still have that machine, and checked the card a second time in that machine.

I have tried youtube through a browser and vlc. I have not tried mythtv  yet, as there's no point in fighting that without working sound.

I ran alsamixer and got a screen with four S/PDIF channels all set to 00 for volume. If I press the M key, the number changes to MM. If I press +/- or up/down I get no change in value. Looking at the 

pulseaudio is installed, but doesn't seem to do anything, and it doesn't change anything if it's disabled.

From syslog I get this:
```
Jul 11 15:16:45 sigsauer systemd-udevd[367]: Process '/usr/sbin/alsactl -E HOME=/run/alsa restore 0' failed with exit code 99.
Jul 11 15:16:46 sigsauer alsactl[697]: /usr/sbin/alsactl: load_state:1683: Cannot open /var/lib/alsa/asound.state for reading: No such file or directory
Jul 11 15:16:46 sigsauer alsactl[697]: Found hardware: "HDA-Intel" "Nvidia GPU 0b HDMI/DP" "HDA:10de000b,10de0101,00100200" "0x1043" "0x8354"
Jul 11 15:16:46 sigsauer alsactl[697]: Hardware is initialized using a generic method

```

running alsa init, I get this:

```

Found hardware: "HDA-Intel" "Nvidia GPU 0b HDMI/DP" "HDA:10de000b,10de0101,00100200" "0x1043" "0x8354"
Hardware is initialized using a generic method

```

in syslog, I get this:
```
Jul 11 16:40:15 sigsauer systemd-udevd[7358]: Process '/usr/sbin/alsactl -E HOME=/run/alsa restore 0' failed with exit code 99.
```

running alsa reload, I get this:

```

Unloading ALSA sound driver modules: snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer).
Loading ALSA sound driver modules: snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.

```

If I do an aplay -l, I get:

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'm at the point of casting about, as I don't see a solution anywhere. I have in the mean time, gone back to my old hardware for mythtv.

This is a clean install on a blank disc, as of today.

---

