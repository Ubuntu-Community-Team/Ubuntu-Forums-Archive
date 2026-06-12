---
title: "Another no sound thread =/.."
date: 2009-07-18
forum: Multimedia Software
---

### Post by Noctis BR on 2009-07-18
Hey im new to Ubuntu and am having problems with having no sound. The pulseaudio playback meter shows that sound is being played but I am not hearing anything. (Nothing is muted) I've tried running sudo killall pulseaudio and switching everything to alsa but still no good.

My sound card is a Realtek ALC889A

This problem happened when I switched to using headphones but now neither worked, I thought I had messed it up really bad so I tried reinstalling Ubuntu, but still no good. I really enjoy Ubuntu and want to work with it so please give me a solution :D.

---

### Post by igorzwx on 2009-07-18
you cannot just kill pulse.
It does not help, I tried.
You start Audacity and pulse is back.
kill it once more.
start playback in Audacity,
and you see that pulse is back.

Evil should be removed,
but this produces other problems.
Eventually, I decided to change to OSS4

---

### Post by markbuntu on 2009-07-18
Your problem is mosty likely very hardware specific and you need to tell the driver to use the headphone switch sensor. Since you did not specify the machine you are using I can only offer some generic help: 

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

btw, this has nothing to do with pulseaudio, it is a problem with the alsa snd-hda-intel kernel driver.

---

### Post by Noctis BR on 2009-07-19
My system is an Alienware m15x, its showing me sound is coming from the realtek Analog pulseaudio but thats the only one its saying sound is coming from. Thanks for the replies.

---

### Post by ecmatter on 2009-07-19
Try this:

[http://ubuntuforums.org/showpost.php?p=5037399&postcount=1](http://ubuntuforums.org/showpost.php?p=5037399&postcount=1)

---

