---
title: "Sound not working on ALSA (cmipci module)"
date: 2008-08-25
forum: Multimedia Software
---

### Post by Zedpellin on 2008-08-25
I'm running xubuntu 7.04, and the other day installed a C-Media CMI8x38 PCI card in my system.

I followed the "Comprehensive Sound Problems Solutions Guide" thread using the following steps:

General Help

(1) aplay -l (no soundcards found)
(2) lspci -v (found my soundcard, moved onto step 3)
(3) C-Media CMI8x38 PCI type using cmipci module.
(4) sudo modprobe snd- (tab doesn't show a list of modules, i.e. it failed)

Getting the ALSA drivers from a *fresh* kernel

(1) uninstalled alsa drivers
(2) reinstalled alsa drivers
(2a) sudo apt-get install gdm xubuntu-desktop (reinstalled gdm&desktop)
(3) rebooted
(4) aplay -l (still no soundcard found)

ALSA driver Compilation
Using alsa-source
(1)
(2)
(3-5) unchecked []all, and checked []cmipci
(6) no errors found, process bar hit 100%

General Help

(4) sudo modprobe snd- (tab still doesn't show a list of modules, so i used sudo modprobe snd-cmipci and it didn't show anything, just went back to command line)

After this, I tried alsamixer (alsamixer: function snd_ctl_open failed for default: No such file or directory), aplay -l (aplay: device_list:205: no soundcards found...)

Any help would be much appreciated, as I am at my wits end about what to do.

---

### Post by botokely on 2008-08-28
I have an analogue problem too and I tried the commands below and I don't know how to fix the problem.

botokely@trano:~$ aplay -l

**** Liste des PLAYBACK pÃ©riphÃ©riques ****
carte  0: Intel [HDA Intel], pÃ©riphÃ©rique 0 : ALC662 Analog [ALC662 Analog]
  Sous-pÃ©riphÃ©riques: 1/1
  Sous-pÃ©riphÃ©rique: #0: subdevice #0

botokely@trano:~$ alsamixer

alsamixer: function snd_mixer_load failed: No such file or directory

Any help too would be appreciated.

---

### Post by Crafty Kisses on 2008-08-28
Post the results of > lspci

---

### Post by markbuntu on 2008-08-28
> **Zedpellin said:**
> I'm running xubuntu 7.04, and the other day installed a C-Media CMI8x38 PCI card in my system.

I followed the "Comprehensive Sound Problems Solutions Guide" thread using the following steps:

General Help

(1) aplay -l (no soundcards found)
(2) lspci -v (found my soundcard, moved onto step 3)
(3) C-Media CMI8x38 PCI type using cmipci module.
(4) sudo modprobe snd- (tab doesn't show a list of modules, i.e. it failed)

Getting the ALSA drivers from a *fresh* kernel

(1) uninstalled alsa drivers
(2) reinstalled alsa drivers
(2a) sudo apt-get install gdm xubuntu-desktop (reinstalled gdm&desktop)
(3) rebooted
(4) aplay -l (still no soundcard found)

ALSA driver Compilation
Using alsa-source
(1)
(2)
(3-5) unchecked []all, and checked []cmipci
(6) no errors found, process bar hit 100%

General Help

(4) sudo modprobe snd- (tab still doesn't show a list of modules, so i used sudo modprobe snd-cmipci and it didn't show anything, just went back to command line)

After this, I tried alsamixer (alsamixer: function snd_ctl_open failed for default: No such file or directory), aplay -l (aplay: device_list:205: no soundcards found...)

Any help would be much appreciated, as I am at my wits end about what to do.

Try the card in another slot if you have one free. I have that problem all the time. Anyway, all the CMI cards should work without any extensive fooling around, at least mine did. Make sure it is recognized by bios when you boot up.

---

