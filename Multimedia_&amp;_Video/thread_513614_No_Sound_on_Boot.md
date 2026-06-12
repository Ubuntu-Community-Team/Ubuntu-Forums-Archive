---
title: "No Sound on Boot"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by JumpingHooligans on 2007-07-30
Alright I'm going to be as thorough as possible, but I'm sure there will be many questions as I am a newbie to linux and Ubuntu.

First off my system is a Dell Dimension 8400 with a Dell Sound Blaster Live! sound card.

On my first few boots everything worked fine except I had to install my WPN111 USB Wireless Dongle.  It took many tries but I finally got it working only if it is unplugged as the computer boots up.  After I am logged in I can plug it back in and my internet works fine.  However after getting the wireless to finally work, my sound began to stop working.  I did some experimenting and I found that if the wireless dongle is plugged in when I boot up, the sound works but no internet, and of course if I boot it up so the internet is working, the sound does not.

I followed some troubleshooting how-to's and used the volume control to turn everything up and unmute everything, but I found that you can change sound devices.  I found that the default device is set to Intel ICH6 which I would guess to be the on-board sound card, when I switched it to the Sound Blaster I still had no sound, but when I turned the microphone on, I could hear myself when I talked into it.  Which to me shows that the soundcard is working but its just not where the system is sending its sound.

Please ask any questions you need, I would like to be able to get sound and internet at the same time, and maybe even not have to unplug my wireless dongle every boot.

Thanks!

---

### Post by kyphi on 2007-07-30
If you are using a soundcard then I would recommend that you deactivate your onboard sound.  You can do that in the BIOS and instructions will be in your motherboard manual.

After you have done that you could check to see that your SoundBlaster Live is the device used by your system.  Go to System (top panel) then Preferences then Sound and check that sound is enabled (checkbox at the top).  At the bottom it should say Sound Blaster Live or something like it.

---

### Post by JumpingHooligans on 2007-08-08
Did what you said, still getting sparatic sound on boot.

---

