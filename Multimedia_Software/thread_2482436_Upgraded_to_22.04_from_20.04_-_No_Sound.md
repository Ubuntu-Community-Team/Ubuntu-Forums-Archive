---
title: "Upgraded to 22.04 from 20.04 - No Sound"
date: 2022-12-30
forum: Multimedia Software
---

### Post by LVDave on 2022-12-30
I just upgraded a Dell Latitude laptop from 20.04 to 22.04. Only post-install issue appears to be no sound. I tried all the google links and nothing worked until I disabled pipewire AND
did an "alsa force-reload". This restores sound, however, everytime I restart or coldboot the system, I have to do an "sudo alsa force-reload". Not really interested in doing this everytime I restart/coldboot. Anybody have a PERMANENT fix?

Edit: Set up a script to run at startup to do the "alsa force-reload" as root. Solves the problem, but isn't a permanent fix.

---

### Post by LVDave on 2023-01-11
Anybody? {{crickets}}

---

### Post by #&amp;thj^% on 2023-01-11
Let's try to hush them crickets then, show us this please:>>(please use code tags for the return)
```
journalctl -b 0 --user-unit=pipewire --user-unit=pipewire-pulse --user-unit=pipewire-media-session --user-unit=init.scope
```
This no sound seems to very common as of late, with upgrades.

---

### Post by LVDave on 2023-02-03
OP here.. Not only do I get this behavior (no-sound) on a 20.04->22.04 upgrade, but on two Dell systems, one Latitude laptop and one Precision workstation, I get the SAME no-sound on clean-installs. I see countless reports of this problem all over the net and none of them seems to fix the problem permanently. I found, on the laptop clean-install a "sudo alsa force-reload" recovers the intel audio device after each reboot. On the precision clean-install, that didn't work, so I ripped out pipewire and audio now works. Ubuntu has a serious problem with this alleged LTS. Never had ANY problems with 20.04... Been with Ubuntu since 7.04, but IF LTS releases are going to be so buggy, it may be time to look elsewhere for a distro.

---

### Post by LVDave on 2023-05-30
Much later, it seems whatEVER was causing this "no audio" issue, has been fixed. No longer need to do the "sudo alsa force-reload".. Thanks, Canonical...

---

