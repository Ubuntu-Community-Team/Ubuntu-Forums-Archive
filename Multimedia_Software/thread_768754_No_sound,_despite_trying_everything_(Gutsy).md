---
title: "No sound, despite trying everything (Gutsy)"
date: 2008-04-26
forum: Multimedia Software
---

### Post by ricmitch on 2008-04-26
Hi all.

I installed Gutsy a few weeks and was very happy that the sound at least worked straight away.

After toying around with VLC and ALSA trying to get SPDIF passthrough to work, I seem to have ended up with no sound at all (either through SPDIF or analog outputs). My initial reaction was to undo the things I had tried in order to get things going again, but this didn't work.

I've followed all the steps on the [Ubuntu wiki](https://help.ubuntu.com/community/SoundTroubleshooting) and [Comprehensive Sound Problems thread](http://ubuntuforums.org/showthread.php?t=205449) but to no avail. This included getting the ALSA drivers from a fresh kernel and purging the old ones as well as trying [this method](http://ubuntuforums.org/showthread.php?t=575653&page=2) of rebuilding ALSA from source.

# aplay -l
# aplay -L
# lsmod | grep snd-
all work as expected.

I've also tried muting, unmuting and messing around with the volumes on alsamixer. I've attached output from [aadebug](http://alsa.opensrc.org/index.php/Aadebug).

My hardware setup is Asus A8N-SLI motherboard (nForce 4) using the on-board sound with no other soundcards. I do have a TV card installed which includes some sound devices, but these never affected sound before.

---

### Post by ricmitch on 2008-04-29
*bump* :(

---

