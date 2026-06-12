---
title: "No sound when playing dvd"
date: 2010-01-15
forum: Multimedia Software
---

### Post by krisro on 2010-01-15
Hello everyone,

I bought an LG external cd/dvd unit (model: GP08 ).
The problem is that I have no sound when playing DVDs. Everything else works fine. I installed libdvdcss (followed this link: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)) but still no sound on DVDs (the DVD works fine on a windows machine).
I have an Acer Aspire One with Karmic Koala.

Any help would be greatly appreciated.
Many thanks.

---

### Post by wojox on 2010-01-15
Did you install:

```
sudo apt-get install ubuntu-restricted-extras
```

Then:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by ramblinche81 on 2010-01-18
WOJOX....I have similar problem to others...no DVD sound and other sound sources play. Restricted Extras with libdvd4 installed per your suggestion with no change.

Device is combo CD/DVD player, and I have attempted the commonly suggested fixes, mods etc with no success.  aplay -l indicates

[INDENT]**** List of PLAYBACK Hardware Devices ****
[/INDENT][INDENT]card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[/INDENT]module is hda-intel

I am GUESSING the problem is in the straightwired CD on device 0 and DVD is device 1 on card 0. When I tried to activate device 1, I received a card/device not present/found type message.

I added my user name to /etc/group file as suggested on another thread but didn't like removing the "pulse" reference as suggested in the Comprehensive instructions.
[INDENT]audio:x:29:pulse
replaced "pulse" with my user name per instructions on LordRaiden's comprehensive sound problem user guide
[/INDENT][INDENT]audio:x:29:root:xxxxx
[/INDENT][INDENT]Do I need to have both pulse and my user name installed ? How would that line of code look for both pulse and xxxxx users on the audio line ?

[/INDENT]Since the CDROM is straight wired to motherboard on board sound, and sound for DVD comes through the SATA bus, I am thinking that is the most likely path to a solution.

Any help or ideas are appreciated.

---

