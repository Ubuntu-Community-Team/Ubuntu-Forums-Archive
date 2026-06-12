---
title: "Logitech 5.1 Not working on 11.10"
date: 2011-10-19
forum: Multimedia Software
---

### Post by subhanu.bhattacharya on 2011-10-19
My Intel original motherboard has a 6 channel (5.1) on-board Audio Subsystem [Realtek ALC883 audio codec on Intel 82801GB I/O Controller Hub (ICH7)]. I recently purchased a Logitech 5.1 which works perfectly on Windows xp. But, it fails to work on ubuntu 11.10 properly. Even after selecting 'Analog 5.1 Surround Output' under Settings > Sound > Hardware, only the F-R and F-L speakers are working. I tried installing GNOME ALSA Mixer, but it doesn't launch after installation.
Any help?

---

### Post by wolfen69 on 2011-10-19
See if [this]("https://help.ubuntu.com/community/SurroundSound") helps.

---

### Post by subhanu.bhattacharya on 2011-10-20
No, I tried modifying the file. But it doesn't help.

---

### Post by dazer26 on 2011-10-29
Go to your package manager (you might have to install synaptic, I dunno I use Kubuntu) and search pulse. Install paman, pavucontrol and pavumeter. After they are installed go to PulseAudio Volume Control under Multimedia. On the last tab (configuration) select you speaker setup (I use Analog Surround 7.1 output). It should work without having to restart, and now you can adjust the levels of the speakers under the Output Devices tab. 

The sound settings in Ubuntu (or Gnome/KDE?) are ****, I've had to install that pulse volume control in the last 3 releases to get surround working properly.

---

### Post by bigmaxic on 2012-04-10
Dazer26!!! Finally!!..Thank you man, that solution worked after all the *.conf files editing..rebooting and all other crap...thank you so much bro!

---

