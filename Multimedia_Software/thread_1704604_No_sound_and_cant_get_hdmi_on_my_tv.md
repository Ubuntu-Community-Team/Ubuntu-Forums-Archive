---
title: "No sound and cant get hdmi on my tv?"
date: 2011-03-10
forum: Multimedia Software
---

### Post by ankers on 2011-03-10
Okay so i installed ubuntu netbook ages ago, i have no sound.. im on a sony vaio f-series so the soundcard is realtek

I installed alsa, checked in alsamixer and all the sounds are turned up. I no longer have the sound control in my taskbar though ether..

And i have a nvidia geforce card, i plug my hdmi cord in turn my tv on and i get no single/display, this all works fine on windows but i would much rather not use windows..

please help me so i dont have to go back to windows again!

Ubuntu: Netbook editiion
Laptop: Sony vaio F series VPCF115FG

Linux ZELAPTOP 2.6.32-2ankers@ZELAPTOP:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: digital audio playback
  5: [ 0- 0]: digital audio capture
  6: [ 0- 0]: hardware dependent
  7: [ 0]   : control
  8: [ 1- 3]: hardware dependent
  9: [ 1- 2]: hardware dependent
 10: [ 1- 1]: hardware dependent
 11: [ 1- 0]: hardware dependent
 12: [ 1]   : control

ankers@ZELAPTOP:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 275

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID b


ankers@ZELAPTOP:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

Most importantly i use my laptop threw my tv threw hdmi

but i cant get sound on my laptop, and i have no idea how to get hdmi to work ether

---

