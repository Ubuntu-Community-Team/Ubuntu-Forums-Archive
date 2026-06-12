---
title: "Acer 9800 fix for Hardy left-speaker-only regression"
date: 2008-04-28
forum: Multimedia Software
---

### Post by Zorael on 2008-04-28
I've been googling something fierce the last couple of days, doing my yearly quota of compiling and teeth-grinding, to fix the sound issues Hardy brought along. Everything worked fine in Gutsy, then Hardy regressed things. This is with the **generic** kernel, on my x64 installation.

This may apply to other Acer models that use the **snd_hda_intel** module for sound, as well. I'm not promising anything.
```
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```


Symptoms include:
[list][*]All sound routed through left speaker (both left and right channels)
[*]Not detecting headphone connection; "headphone" channel had to be muted and unmuted in alsamixer manually whenever you want to swap between headphones and speakers[/list]
Circumstances include:
[list][*]Following command says "front left, front right" in left speaker
```
$ speaker-test -twav -c2 -Ddefault
```
[*]No error messages in dmesg
```
zorael@sunspire:~$ dmesg | grep snd
zorael@sunspire:~$ dmesg | grep hda
zorael@sunspire:~$
```
[*]Channels aren't muted in alsamixer, nor set too low
[*]Installing **linux-backports-modules-hardy** doesn't help
[*]Compiling new modules from the **alsa-source** package in the repositories ends up with fresh modules with the same flaws[/list]


If those circumstances and symptoms don't correlate to the issues you're experiencing, this is likely not for you. Meaning, if you're getting spam of 'unknown symbols' in dmesg, this isn't it.

If they *do* correlate, the module isn't at fault. **All** you want to do is open up **/etc/modprobe.d/alsa-utils** in your text editor of choice, with superuser permissions...
```
$ gksu gedit /etc/modprobe.d/alsa-utils        # Gnome
$ kdesu "kate /etc/modprobe.d/alsa-utils"      # KDE
$ gksu mousepad /etc/modprobe.d/alsa-utils     # Xfce
$ sudo nano /etc/modprobe.d/alsa-utils         # terminal
```
...then add the following line to the bottom.
```
options snd-hda-intel **model=acer**
```
The **model=acer** bit is the important part, so if the line exists but has another model definition, change it accordingly. I've tried '**laptop**', '**3stacks**', '**auto**', and several others with varying degrees of *no-luck-at-all*. Besides, '**acer**' makes sense, hmm?

Should work. Sure did for me.

---

