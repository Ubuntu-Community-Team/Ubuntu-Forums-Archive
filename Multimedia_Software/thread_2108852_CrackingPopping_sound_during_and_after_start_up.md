---
title: "Cracking/Popping sound during and after start up"
date: 2013-01-25
forum: Multimedia Software
---

### Post by Pixtu on 2013-01-25
I have a working system with Ubuntu 10.04 with no problems.

When trying out an installation with 12.10 derivatives I frequently get an extremely annoying cracking/popping noise from the left speaker (which may actually be the system speaker rather than the onboard sound), which makes the system unusable.

Odd pops start during the boot process and once I login they become regular, perhaps a frequency of two per second. The 'pops' continue even if the sound is muted. Occasionally I can boot without the problem occurring after login, although there will usually be some popping during the boot process, and even more occasionally the popping will cease on it's own.

This problem also occurs with Linux Mint 14 (Nadia) and Xubuntu 12.10 but not with other distros such as Manjaro, so it would appear to be a problem with the base Ubuntu system.

My system is a Sony FS315S, Pentium Mobile, nVidia Graphics and Intel Audio.

I'm guessing that the problem is something to do with Alsa or Pulse and something that has obviously changed since 10.04.

I have seen numerous posts in a number of forums (including Ubuntu and Mint) which suggest various changes, mostly to do with the sound going into power saving mode. I have tried all of these things to no avail.

In case it may help identify a solution, I have three files created by the alsa-info script. alsa-manj.txt ([http://pastebin.com/K4n0fw5H](http://pastebin.com/K4n0fw5H)) was when running Manjaro (no problems), alsa-xubu.txt ([http://pastebin.com/g9VB3mfm](http://pastebin.com/g9VB3mfm)) running Xubuntu (with the sound problem) and alsa-1004.txt ([http://pastebin.com/DZXDqb8a](http://pastebin.com/DZXDqb8a)) running Ubuntu 10.04 (no sound problems).

Can anyone suggest what I can change or do to stop the noise please?

PS. I forgot to add that if a media file is played during the popping, then the media sound only appears to be affected by a rapid 'coming and going' of the sound/volume. In all other respects the sound seems to be working normally. Whilst the popping is at a fixed (quite loud) volume, the media playback volume can be muted , raised or lowered via the speaker sound controls.

---

### Post by AstroLlama on 2013-01-25
are the volume for the left and right speakers at equal levels?

the sound is otherwise working normally? if not it could be that the speaker is cracked  or popped...

---

### Post by Pixtu on 2013-01-26
> **AstroLlama said:**
> are the volume for the left and right speakers at equal levels?
Yes, the speaker volumes are equal.

> the sound is otherwise working normally?
Yes, otherwise working normally.

> if not it could be that the speaker is cracked  or popped...
No problem with the hardware. Existing 10.04 installation works properly without the popping. System also works with non Ubuntu distributions.

The problem appears to be caused by a change in how sound is managed in Ubuntu since 10.04 which is not used by other distros. I'm guessing it is something to do with Alsa and/or Pulse, but I don't yet know enough about these two systems or how they work together.

---

### Post by Pixtu on 2013-02-19
Having booted with a Live CD version of 12.04 without any problems it would appear to be something that has changed between 12.04 and 12.10.

I have also tried KDE versions with the same results.

So I need someone that understands how the sound operates and is configured in the underlying Ubuntu system in these two versions.

---

