---
title: "Virtualbox - Its playing, but i hear no sound!"
date: 2009-03-03
forum: Multimedia Software
---

### Post by captain_conrad on 2009-03-03
Hi

I Have windows XP running in Virtualbox 2.1.4.

If I play any music or video inside windows, I cannot hear anything!:sad:

My Host OS (ubuntu) can play sound, i have rhythmbox playing loud and clear.

But the Guest OS is somehow not getting the sound to play through the Host OS´s sound output places (speakers/headphones)

My guest OS can use my Host´s CD/DVD drive, and all 4 my USB ports work perfectely. My internet even works inside the guest OS.

I just want the sound to work plz!

Any advice?

thank you

---

### Post by captain_conrad on 2009-03-05
hey, i think i solved this?

I went to System->Preferences->Sound

All of them were on Auto Detect on my machine. So when i hit Test it would give the tone. I then scrolled through the list, selecting them, one at a time, and checking whether it gave the tone or not. And in doing this i found out which driver my PC is using for the sound and video playback.

I then shut down my Windows´ Virtualbox, so that i could get into its settings.

In settings, I went to the Audio Tab, and Where it says Host Audio Driver, I changed that to match the one I had established was the working one back in My system preferences´ sound Window.

As much as i have kinda solved the problem, I still don´t understand exactely what those things are...

There in virtualbox audio settings, what is that audio controller thing? I have two options, ICH AC97 and Soundblaster 16. Which is which and what is it? And more importntly, hich should I use?

And in my system preferences´ sound window, i found the two drivers that do work were PulseAudio Sound Server and ALSA Advanced Linux Sound Architecture. Now what on earth are these, and more importantly, which one should i use?
I do trust my ubuntu to Autodetect the right one for itself, but which should i use in virtualbox?

thanks, *cc

---

### Post by kelvin spratt on 2009-03-05
ICH AC97 is for linux on the 1st one the other depends on what you are using in linux
PulseAudio Sound Server or ALSA Advanced Linux Sound Architecture or oss. usually alsa please note you can't play cds in virtual box at the moment,  have you got guest additions installed?

---

### Post by captain_conrad on 2009-03-09
yup, got all guest editions installed

---

