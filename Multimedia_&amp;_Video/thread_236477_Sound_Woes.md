---
title: "Sound Woes"
date: 2006-08-14
forum: Multimedia &amp; Video
---

### Post by starorbs on 2006-08-14
I have spent so many hours trying to get my sound to work. I was hoping I could get some help. Anyways, my sound drivers are all installed, all the commands verify that they are installed.

The driver which is being used is an Alsa snd_hda_intel. I did a whole bunch of searches and tried a whole bunch of different things on this forum and other places and no luck. I have run into another idea of installing all new alsa drivers from their site but when I try to install them and use 
sudo ./configure --with-oss=yes --with-cards=hda-intel and everything is fine until the end.

checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

I checked the default location it is in fact not there. I have installed them using Synaptic Package Manager and reinstalled them and that didn't help. If anyone has any ideas, help, anything I would appreciate very much.

---

### Post by starorbs on 2006-08-14
This even confuses me more.. Acoording to this the sound should be playing but nothing comes out.

aplay /usr/share/sounds/login.wav
Playing WAVE '/usr/share/sounds/login.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

---

