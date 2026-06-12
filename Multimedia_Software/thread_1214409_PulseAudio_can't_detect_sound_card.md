---
title: "PulseAudio can't detect sound card"
date: 2009-07-15
forum: Multimedia Software
---

### Post by thechief19 on 2009-07-15
I'm trying to get PulseAudio working with Ubuntu 8.10. The sound card is a sound blaster 16 using an ISA slot. Initially I had to configure the BIOS to manully select the sound card. I also had to configure Ubuntu to choose the sound card at startup. This part seems to work fine now.
 
If I go to System->Preferences->Sound and change the sound playback to OSS I will get sound. When I click the Test button I get a tone. I can also play music using Rhythmbox.
 
If I go to System->Preferences->Sound and change the sound playback to PulseAudio Sound Server I can't get any sound. When I click the Test button the graphic will be displayed but no sound is heard.
 
If I go to the PulseAudio Volume Control, Output Device tab I don't see any Hardware Output Devices. I think this may be one of the problems.
 
Any help would be appreciated. Thanks.

---

### Post by HeadHunter00 on 2010-01-26
sudo alsa force-reload

---

