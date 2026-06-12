---
title: "using creative xmod usb"
date: 2008-12-15
forum: Multimedia Software
---

### Post by TMachado on 2008-12-15
I want to use my Creative Xmod in Ubuntu 8.10

[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

So I've downloaded and installed alsa-driver-1.0.18a, and when connected to the computer, I can use "buttons" from my xmod, but the sound goes to the laptop system sound...

What can I do?

---

### Post by andreasis on 2008-12-16
Hi,

I have the same card.  It is perfect except for one thing: linux support.  Every time I configure it on a new system, a different problem needs to be resolved.

As per your issue, a first step that I take is to check under System > Preferences > Sound, and play around with the settings until (if even) you find one that works.


It sounds like you're using both the notebook and the xmod sound cards, at the same time.  Three options that I could think of is to

[easiest] disable your integrated sound card from the notebook's BIOS

or
a) identify your notebook's soundcard using the command lspci
b) look up the driver for your card and compare it to your lsmod output
c) blacklist your sound card under /etc/modprobe.d/blacklist

or
try just setting the xmod sound card to be the default sound card
[http://ubuntuforums.org/showthread.php?t=487729](http://ubuntuforums.org/showthread.php?t=487729)
Do look through this and the guide referenced in post #2.

---

