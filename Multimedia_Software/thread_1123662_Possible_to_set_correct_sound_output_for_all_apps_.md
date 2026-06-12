---
title: "Possible to set correct sound output for all apps to use?"
date: 2009-04-12
forum: Multimedia Software
---

### Post by themusicalduck on 2009-04-12
I'm trying to persuade ubuntu to use my onboard chipset for sound but I can't get it to use the correct output for all of my apps.

I currently have a soundcard installed as well which works fine, but I don't have the right connector for it at the moment and need to use my onboard chipset. I have set it as default using asoundconf and turned up pretty much any slider I can find in alsamixer. The weird thing is that I can set the sound preferences to use ALSA and using test, it will play out of my front output. I think it is playing out of ALSA PCM on front:0 however if I try to use any sound app it won't play at all. Using the volume meter on padevchooser shows it as playing out of ALSA PCM on front: 1, yet I can plug my headphones into all of the outputs on my card and get no signal (excluding trying the spdif output as I cannot)

I'm guessing I might need to change my asoundconf file, but I'm not sure what it is I need to do.

The onboard sound is an Nvidia CK804 and it is Ubuntu 8.10.

---

### Post by themusicalduck on 2009-04-12
I swear.. the number of times Ubuntu does this to me. I type out a thread for help on the forums and 30 seconds later it starts working magically by itself. I don't even know what it is I did that fixed it if anything, but oh well, it's all good.

---

### Post by markbuntu on 2009-04-12
Well, I saw your OP and I was going to tell you to go here. You should check it out anyway as it will help you better understand and control what is going on with your sound, especially with two hardware devices.


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by themusicalduck on 2009-04-13
Was about to bump this thread as my sound had stopped working again after rebooting. Your link fixed it for me and at least now I know what it is I need to do if it happens again :)

Thanks a lot.

---

### Post by markbuntu on 2009-04-13
I have also written this for multiple sound hardware devices


[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

