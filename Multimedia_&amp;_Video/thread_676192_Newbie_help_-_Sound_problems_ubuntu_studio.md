---
title: "Newbie help - Sound problems ubuntu studio"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by Prinssimikko on 2008-01-23
Hi

I just stepped into the world of Linux. It's been interesting as well as frustrating so far...
after a couple of nights i finally managed to make a working dual boot system with XP and Ubuntu Studio.

My main concern at the moment is sound. 
I cant get any sound of any audio player! 
I managed to get a test sound by going to Sound Preferences. there is the Test button, and i kept pressing it with various settings. i found out that when i have selected "VIA 8237" for sound events or music and movies, i hear the test sound.
but if i then start an audio application "Amarok", i cant hear nothing! the file is playing, and i can see the level meter move.

at first i thought it was because of my sound card (SoundBlaster X-Fi) which apparently doesnt work with Linux, but i plugged my headphones to the integrated sound card on motherboard, and still i can only hear the test beeb.

i'm running an quite old AMD Athlon PC. On the motherboard's manual it says: 
"Audio - ADI AD1888 SoundMAX 6-channel audio codec supports s/pdif-out interface."

Any help would be appreciated!

_Mikko

---

### Post by Prinssimikko on 2008-01-24
:( bumb

sorry to harrash you guys, but i am totally lost here... 

btw, when booting does it make any difference if i choose rt or generic -version? i tried both and they look and feel the same... and both have the same problem with sound...

thanks!

---

### Post by caseyg on 2008-01-27
You may have to enable or disable onboard audio in bios. Also, when opening the audio application, look for an options tab or some where in the app that may let you specify which audio device to use. I also have sound issues with Ubuntu Studio with my sound card but onboard works well. I have a 4 year old AMD system with Epox main board. 

This may be a silly question, but when your in the sound preference section, are you selecting 'test' on the audio playback area? Can you here sound when selecting OSS? I do know you shouldn't be  using ALSA unless you use a compatible sound card.

Good Luck

---

