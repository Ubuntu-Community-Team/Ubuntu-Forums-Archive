---
title: "Copying sound config info from live cd to disk install...."
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by Catalyst2Death on 2007-11-05
Hello,
My sound is configured, and works properly when running the live cd, however, when I install Gutsy, the sound configuration is lost, and fails to work.  Is there any way that I can copy the sound configuration settings that the live cd is using to my harddisk install?  

Specifically, my sound only works when I select multi-channel playback, and when I select that, it only plays mp3 files ( those are the only files I have available to test with)  it will not play any system sounds, and it will not play sound in video.  This is what is stopping my from swearing off windows for good, and I can't get it to work.  My card is a PCI Sound Blaster Live! 5.1 I can't figure out what I need to do to get Alsa to autodetect the settings.  Alsa has no problems in the live CD, but it doesn't translate after the install.  

Could it have to do with two different onboard soundcards that are being detected?  I disabled them in bios, but I can still select them in linux... I haven't tried in XP, but I'm pretty sure that the PCI card is the only one detected there...

The other cards (As detected by ubuntu) are a Realtek ALC658D (OSS Mixer) and the VIA 8237 (Alsa mixer)  The card that I want to work, which doesn't is the SB Live 5.1 [SB0220] (Alsa mixer)

Any help would be immensely appreciated, even if it I can be pointed in a different direction in terms of what I'm looking to fix...

---

### Post by Catalyst2Death on 2007-11-06
Bump.  I could really use some help, I just don't know where to look anymore.

---

### Post by killaken2000 on 2007-11-07
I'm having this exact problem maybe after i bump this someone might have an answer. That and i don't have to make a new thread.

When i use the gutsy live-cd everything works fine for me. All the videos play and its great. Then when i install to the harddrive. I get no audio and the ogg video test file is very choppy.Also the system isn't too stable. I'm now using dapper and got everything working fine.

---

