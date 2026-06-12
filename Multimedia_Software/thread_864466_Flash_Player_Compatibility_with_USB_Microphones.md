---
title: "Flash Player Compatibility with USB Microphones"
date: 2008-07-19
forum: Multimedia Software
---

### Post by ndelp on 2008-07-19
I'm running ubuntu 8.04, have a logitech communicate stx webcam which has a built in microphone and is connected via usb. 

My microphone works fine in any application where i can select the driver (skype, etc), but for some reason Flash 9 won't recognize it when i go to select it. (im using it for stickam.com) which uses flash. 

the only device which it will locate is the default linux microphone. is this just a flash issue or is there some kind of driver which i would need for flash, or could i just make my usb mic fall under the linux microphone by editing some file. 

thanks for reading that mangled mess and any insight would be more than helpful. thanks again!

---

### Post by SubGenius13013 on 2008-11-10
I use a set of Bose Companion 5 USB speakers and I also have a Logitech USB headset (in addition to the crappy on-board sound my motherboard came with). Everything works perfectly as is under PulseAudio except Flash Player, which will only work with ALSA. The only way I could get it to recognize the USB headset was to create a killall pulseaudio startup command, blacklist the onboard sound, unplug my Bose speakers and restart. It's a pain... I thought PulseAudio was supposed to make everyone's life easier!

---

