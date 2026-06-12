---
title: "Optimizing Ubuntu 10.04 for hi fi purpose"
date: 2010-08-24
forum: Multimedia Software
---

### Post by borisfr on 2010-08-24
Hello, I have just bought a digital-to-analog converter, [this one]("http://www.son-video.com/Rayons/Hifi/LectChangCD/DacMagic.html") to be exact, along with an amplificator and two speakers. I'd like to get the most of my Ubuntu, a good sound (what player can I use ?) and to know wether I need to do some extra changes in the kernel (OSS / PulseAudio / ALSA ?) or not.
I wonder if my converter will be detected when i plug it in, and if any sound from my computer will be leaded to it automatically ? (I'll have the converter tomorrow). I believe its purpose is to replace the sound card, to provide a greater, pure sound. The converter is linked by USB by the way.
Thanks for your help :) 

PS : I'm French so please excuse my language

---

### Post by cchhrriiss121212 on 2010-08-24
This is probably a little late for you but there is no guarantee that this will work in Ubuntu as an external USB soundcard. If it does not work via USB, you could still use it as a DAC if your PC has digital output. If it does work , you should just need to select it in the preferences>sound menu as default output. 

Regarding software, any player will do fine as they all make use of the same audio backend, any difference between players is personal preference, I recommend Quod Libet.
Tweaking the kernel is not necessary, but you could use ALSA instead of pulse+ALSA (which is the default in Ubuntu) if you wanted to simplify your sound chain.

---

### Post by cascade9 on 2010-08-25
I found this- 

> [SIZE=4][SIZE=2]I contacted Cambridge Audio They said that their DACMagic should work OK with Linux. So I gave a DACMagic a try.  

I connected the DACMagic to the Shuttle computer via USB and experimented. For whatever reason I was unable to get any sound using Xubuntu. But Cambridge audio said they had it working with Ubuntu, so I then tried that. Success!![/SIZE] [/SIZE]

[http://www.audiomisc.co.uk/Linux/Sound1/SoundComputing.html](http://www.audiomisc.co.uk/Linux/Sound1/SoundComputing.html)

Good luck ;)

---

### Post by borisfr on 2010-08-26
Thank you for you reply :) I was a little disappointed at first sight but then I got my DAC today and I found [this page]("http://www.314r.fr/index.php?post/2009/07/30/DAC-USB-sous-Ubuntu-9.04"). (by searching "Cambridge DAC linux" in google - What I should have done before posting here...)
It's in French and seems really helping :D ! I'm gonna see if it works !

cascade9 > I just wrote this without seeing your reply ^^ Thank you ! I can't fail now :D

---

### Post by borisfr on 2010-08-26
I'm not sure it's the right expression, but I just wanna say this : It works like hell ! :D
I'm so happy ^^ In fact, I just had to
1. Link my DAC
2. ??????
3. PROFIT !§§§§§11

Now I can just :popcorn: and enjoy my music :D Thanks for all of you who replied!

PS : If anyone has an idea about a media player I'd take it ;)

Ah, and according to this[ topic]("http://www.hydrogenaudio.org/forums/lofiversion/index.php/t56404.html") (but it's kinda ancient...) we should not use gstreamer or any player using it... Is that right ?
And I have heard that Phonon was bad too cause automatically converts 44.1 khz data in 48 khz, thus decreasing drastically the quality of the audio...

---

