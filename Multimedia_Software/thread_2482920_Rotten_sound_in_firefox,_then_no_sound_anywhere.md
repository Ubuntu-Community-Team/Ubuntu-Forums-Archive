---
title: "Rotten sound in firefox, then no sound anywhere"
date: 2023-01-14
forum: Multimedia Software
---

### Post by alreve on 2023-01-14
The problem started today. I wanted to watch a video with firefox and the sound was vibrating. As if it was saturating, even though it wasn't very loud. 
I started fiddling. I tested with VLC and the sound was OK. I removed-purged firefox. Still vibrating. I removed-purged pulseaudio and rebooted. 
Vibrating sound in firefox and NO sound at all with VLC. I tried a few other command line instructions found online and rebooted. Now I have no 
sound at all, even in firefox.

Now I'm afraid to do anything except sudo inxi -SMA, because when I fiddle I make things worse. I should have left things alone (I could always 
download my video to watch it). sudo inxi -SMA says:
 
System:
  Host: lub Kernel: 5.15.0-56-generic x86_64 bits: 64 
  Desktop: LXQt 0.14.1 Distro: Ubuntu 20.04.5 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: Acer product: Aspire 7739ZG v: V1.04 
  serial: LXRUM02001148018E07200 
  Mobo: Acer model: HMA71_CP v: Type2 - Board Version 
  serial: Type2 - Board Serial Number BIOS: Insyde v: 1.04 
  date: 10/11/2011 
Audio:
  Device-1: Intel 5 Series/3400 Series High Definition Audio 
  driver: snd_hda_intel 
  Device-2: NVIDIA GF108 High Definition Audio 
  driver: snd_hda_intel 
  Sound Server: ALSA v: k5.15.0-56-generic

---

