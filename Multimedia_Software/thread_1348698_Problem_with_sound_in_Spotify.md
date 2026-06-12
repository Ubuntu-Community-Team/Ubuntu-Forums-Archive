---
title: "Problem with sound in Spotify"
date: 2009-12-07
forum: Multimedia Software
---

### Post by Mr. Kaschei on 2009-12-07
Hey, I'm new to the forums (new to Ubuntu and Linux too), so hi all!

I'm running Spotify through Wine 1.0.1. My problem is that when I've listened to 2 or 3 songs, the sound becomes a somewhat scratchy noise, and keeps like that until I restart Ubuntu.

Hope you can help me, I'm getting quite mad without some music on the background!


By the way, I don't usually write in english, so sorry if there are any faults ;).

---

### Post by jaezcurra on 2009-12-07
Try their advice:
 
"Start winecfg and make sure your audio works.

$ winecfg
Go to the Audio tab in the program and click on Test Sound. If you hear something, then you are all set, if an error message appears you have to configure it. Make sure the ALSA checkbox is checked and press OK and restart winecfg (it needs to re-initialize sound drivers) and click on Test Sound again. When you hear something you can continue. If you can’t get sound to work, it is unlikely you will hear anything in Spotify.

In the DirectSound frame at the bottom enter the following for best sound.

Hardware Acceleration: Emulation
Default Sample Rate: 44100
Default Bits Per Sample: 16
Driver Emulation: unchecked"

BTW, I unchecked ALSA and checked OSS in the Audio tab of Wine, as well.

Spotify goes flawless under 9.10 for me.

---

### Post by Mr. Kaschei on 2009-12-07
I followed their advices, but it didn't work. It works unchecking ALSA and checking OSS though. Thank you :p.

---

