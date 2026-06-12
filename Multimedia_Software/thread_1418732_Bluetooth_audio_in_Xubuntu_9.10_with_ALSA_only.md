---
title: "Bluetooth audio in Xubuntu 9.10 with ALSA only"
date: 2010-02-28
forum: Multimedia Software
---

### Post by Agnaramasi on 2010-02-28
Xubuntu 9.10 ships with only ALSA installed and I would like to keep it that way. Unfortunately, I am having trouble getting my bluetooth speakers to work. I can connect to the bluetooth device with A2DP service with the blueman manager, but the bluetooth audio device does not show up in my ALSA mixer.  I've tried editing/creating ~/.asoundrc and /etc/asound.conf files as instructed [here](http://wiki.bluez.org/wiki/HOWTO/AudioDevices). That doesn't seem to work. I would much rather have a simple ALSA setup than use pulseaudio.  I'm also not sure if the bluez-alsa package is required, as the bluez site indicates it is deprecated, although I've found no success with it installed or not.

Thanks for your help!

---

### Post by JamesSmith on 2010-05-02
I too would love to see a solution to this.

I did get bluetooth audio to work in Ubuntu 9.04, basically by manunally editing the .asoundrc file when I wanted to use bt audio and replacing the default device for my bluetooth device.  Not even a remotely elegant way of doing it though.

---

### Post by mangamaster99 on 2010-05-24
yeah i would like to see this solved too 

switched from ubuntu to xubuntu becase i didnt like the ram cache feature but other wise

it was working in ubuntu with bluez 

so far it connects with blueman but does not show in sound prefences 

it thoguht they would have ths fixed somewhat already in all versions of ubuntu

---

