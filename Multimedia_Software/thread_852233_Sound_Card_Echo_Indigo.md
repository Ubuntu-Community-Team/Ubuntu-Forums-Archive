---
title: "Sound Card Echo Indigo"
date: 2008-07-07
forum: Multimedia Software
---

### Post by BRRFOC on 2008-07-07
Greetings - new Echo Indigo IO card installed but firmware not loaded (dmesg shows:  *Firmware not available (-2)*.

The card is detected using *lspci -v* and the snd_indigoio module is loaded, but the card does not appear using *aplay -l*.

There doesn't appear to be anything for Echo card in /lib/firmware/kernel/2.6.20-15-generic/ however there is Makefile in /usr/src/linux-headers-2.6.20-15/sound/pci with script for Echo Indigo.

I've read various posts on Ubuntu forum for the Echo Indigo card, I have alsa-utils and alsa-firmware-loaders installed.  Any suggestions would be appreciated, thanks.

ok - if firmware is not found, add hardy to medibuntu sources.list.d and install alsa-firmware 1.0.16.  Follow instructions in thread 826724 for Echo Indigo.

---

