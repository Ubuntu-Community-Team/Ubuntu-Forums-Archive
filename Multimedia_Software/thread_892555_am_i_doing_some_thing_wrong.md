---
title: "am i doing some thing wrong?"
date: 2008-08-17
forum: Multimedia Software
---

### Post by jammin2222 on 2008-08-17
Hello all, 
 Im another noob ubuntu user and am liking the experience a lot! 

It seemed to set everything up fine including my graphics card. The sound card on the other hand was a bit problematic. i have the sound blaster audigy 4.

I can hear music and video saved on my hard drive, but cant hear system sounds, record sound with the microphone, or hear sound from online video site youtube. 

In the sound preferences under: default mixer tracks: i have found my sound card listed in the drop down box: audigy4 [SB0610] (Alsa mixer)

the other drop down boxes above called: sound events, music and movies, and audio conferencing are a bit different, they don't say my sound card and i don't know what they should be set on. autodetect didn't do its thing im guessing?

I have tried a few combinations out but as of yet the only sounds i heard were from pidgin, and movie player. I have adjustment for each speaker in the volume settings that work with movie player so it must have recognized the audigy 4 sound card to some extent.  

I downloaded codecs when prompted and even installed flash 9 needed for youtube. 
 
I'm sure its something simple that im missing out.

I'm dieing to hear what the startup sound is and yes i have enabled software sound mixing (esd), and ticked the play system sounds box.

Any help muchly thanked in advance

Ben

---

### Post by Raffles10 on 2008-08-17
[PulseAudio]("https://wiki.ubuntu.com/PulseAudio") is the standard sound server in Hardy Heron 8.04.

The above link may help. If not try this:

[The (almost) Perfect PulseAudio Setup]("http://ubuntuforums.org/showthread.php?t=776739&highlight=ekiga+pulseaudio")

---

### Post by heracles on 2008-08-17
I have no asound or libaudio folders in etc ? I have checked that pulse audio is ticked in synaptics but no files are there for me to edit. Any ideas please?

---

