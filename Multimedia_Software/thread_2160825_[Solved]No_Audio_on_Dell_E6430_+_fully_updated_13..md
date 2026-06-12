---
title: "[Solved]No Audio on Dell E6430 + fully updated 13.04 install"
date: 2013-07-08
forum: Multimedia Software
---

### Post by chinamusic on 2013-07-08
In case anyone else is having trouble with this laptop and audio playback....looking at the sound widget in the control panel showed "dummy device" so there was no sound output.  What I did to fix it:

sudo su -
apt-get remove --purge alsa-base pulseaudio
apt-get install alsa-base pulseaudio
alsa force-reload
reboot

Then the sound widget shows "Built-in Audio" as an output device and things work as expected.

Best,

---

