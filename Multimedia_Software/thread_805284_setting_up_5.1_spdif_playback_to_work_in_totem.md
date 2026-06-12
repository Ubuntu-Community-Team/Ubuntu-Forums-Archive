---
title: "setting up 5.1 s/pdif playback to work in totem"
date: 2008-05-23
forum: Multimedia Software
---

### Post by pirotrav on 2008-05-23
Hi,

I recently purchased a sound adapter which converts usb to optical toslink.  (see further details >> at [http://www.mcmelectronics.com/product/83-10171](http://www.mcmelectronics.com/product/83-10171)).  When i plug the device in, ubuntu does the login sound, and i have checked my sound settings to ensure it is the default device etc.  I also ran the 'test' in preferences >> sound and the audio is pushed through my digital receiver and out the speakers correctly.  

My issue, however, is that in every media player i try (mplayer, totem movie player; no sound is pushed through.  I primarily want Totem to handle 5.1, and have tried all of the output options (2.1, 5.1, AC3 etc).  None produce sound.  Also the formats' of the test files range from dts to dolby digital to AC3.  Even wav's do not output any sound throught my reciever.  Any help on this matter is hugely appreciated (or redirect me if this is posted somewhere else but a few searches didnt return any solid results, and i think my situation is individual due to the nature of that sound-card adapter thing.  Finally, everything is hooked up correctly as all of the speakers work when a cd is played in vista (yuck!!)

After hours of tinkering i must turn to the experts.

Thanks in advance!!
Travis

p.s this is one of my first posts here so if i do anything incorrectly do let me know

---

### Post by proteo on 2008-05-27
You need to encode the sound to AC3 (Dolby Digital), spdif usually only handles stereo sound, there is an Alsa plugin called A52 that can mix 5.1 channel audio into a dolby Digital stream. here is the page from the alsa site: [http://www.alsa-project.org/main/index.php?title=A52_plugin&printable=yes]("http://www.alsa-project.org/main/index.php?title=A52_plugin&printable=yes")
and here is a link to my thread looking for help setting up the plugin: [http://ubuntuforums.org/showthread.php?t=802368]("http://ubuntuforums.org/showthread.php?t=802368")
still no responses for my thread. :(

---

### Post by proteo on 2008-05-28
i found a possible solution: [http://ubuntuforums.org/showthread.php?t=714712&highlight=alsa-plugins]("http://ubuntuforums.org/showthread.php?t=714712&highlight=alsa-plugins")

---

