---
title: "Volume changes on OSD but nothing from speakers"
date: 2008-09-03
forum: Mythbuntu
---

### Post by zagor on 2008-09-03
Hi all,

I have just upgraded from Mythbuntu 7.10 to 8.04.1 (64bit version).
Everything was working fine in 7.10 with Mythtv 0.20.
Now it seems I can't change the volume from within MythTV.
When changing the volume either with a keyboardo or with the remote, I see the OSD showing a volume change (in mythtv or xine or VLC, pick yours) but no changes are heard from the TV speakers.
Only way to change the volume is using the TV remote.
Btw, in the setup screens I've set both initial volumes at 95, but the OSD in the internal player is always starting form 100%.
Don't know if it matters....

Thanks

---

### Post by xykevinr on 2008-09-03
Could be wrong but try this.

Open a terminal, run alsamixer, play a tv program, see which channel affects the volume. When you know, go to frontend setup, general, audo, select ALSAdefault, and type in the name of the channel you found in the 'Mixer controls' box.

Kev

---

### Post by zagor on 2008-09-04
It seems probably the issue is more general and related to the upgrade procedure: alsamixer won't start and I receive this message
```
alsamixer: function snd_mixer_load failed: No such file or director
```

If I try to change the device, actually notyhing is shown and no controls either.
The integrated audio on my barebone Asus P1-AH2 is a ALC861-DTS (DTS supported)Azalia 6 Channel.

Any hint on what to do?
Thanks

---

### Post by zagor on 2008-09-05
Solved, following [this]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382/comments/86") workaround.

```
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
sudo alsa force-unload
sudo depmod -ae
sudo modprobe snd-hda-intel
```

Hope I don't have to recompile for each kernel update.
In my opinion, this bug is unforgivable for an upgrade from 7.10 to 8.04, a LTS version! Not for the bug itself, but because is present on launchpad since Feb 2008 and still no official solution/patch!

---

