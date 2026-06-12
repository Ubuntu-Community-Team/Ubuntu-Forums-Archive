---
title: "[SOLVED] Stuttering or Slo-Mo Audio"
date: 2008-07-21
forum: Multimedia Software
---

### Post by dprestemon on 2008-07-21
I have a problem with stuttering sound.  The sound is not distorted or frequency shifted, just very ssssssllllllloooooowwwwww.  Here are the basic facts:

- I am running Hardy Heron with all updates through July 21.
- The sound always fails, but the timing varies.  It may work for one minute or two hours, but the average is probably around 10 minutes.
- The failure is application independent.  It does not matter which program is generating the sound.
- The failure is generalized.  If the sound fails with music playing in Rhythmbox, I can shut that and start Movie Player and will have the same problem.
- Only rebooting the system eliminates the problem.  (If there are commands I could try in a terminal window, I don't know what they are.)
- System overload is not a contributing factor.  The sound will fail even if only one application is running.
- The problem is OS related.  I have a dual-boot system and have no sound problem with Windows XP, but I really do not want to return to Windows.
- I have followed all of the recommendations in psyke83's PulseAudio fixes how-to post, and read through a dozen other related posts, all without success.
- The only log entry that appears potentially relevant is this one:

```
ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x00cb2001
```

This entry appears only after the sound has failed, but, strangely, it does not get posted at the time of the failure, but rather when the system is rebooted.

My system consists of:
- Micro-Star MS-7253 motherboard with VIA K8M890CE Northbridge and VT8237A Southbridge
- AMD Athlon 64 X2 4000+ CPU
- 2 GB RAM
- VIA High Definition Audio Controller with this configuration: driver=HDA, Intel latency=0, module=snd_hda_intel
- Realtek ALC883 audio codec

Any help will be greatly appreciated.  In my little apartment, my computer is my radio, stereo and DVD player.

---

### Post by dprestemon on 2008-07-25
Apparently the problem was related to the "Autodetect" option in gnome-sound-properties (accessible through System-Preferences-Sound). Switching the sound playback preference to "ALSA" eliminated it.

---

