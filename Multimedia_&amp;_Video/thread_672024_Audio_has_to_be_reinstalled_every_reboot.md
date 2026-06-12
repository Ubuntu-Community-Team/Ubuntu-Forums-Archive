---
title: "Audio has to be reinstalled every reboot"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by savethewabbit on 2008-01-19
hi everyone,
i'm having a really frustrating problem with my audio on ubuntu. at first it didn't work, so i checked the comprehensive thread for audio problems here on the forums, and they suggested to do this:

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

then

```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

and then

```
sudo apt-get install gdm ubuntu-desktop
```

and then it worked. problem is, most of the times, after i reboot, audio won't work again. i have to open up the terminal, do the whole abovementioned process, and reboot to have my audio working again. 
now, at first it wasn't that bad because it worked at the first attempt, so i only needed to reboot once. 
then it started to need *two* or *three* reboots (both of which included opening the terminal and doing that stuff) to have it work. 
today i'm at my 6th reboot and it still doesn't work. it's getting really frustrating :-\

do you know why is this happening? i mean, when it works it works fine, but when it doesn't it takes ages and a million reboots for me to fix it, and i would rather not going on like this. 

anyone has suggestions about how to fix this problem? 

thank you very much!

---

### Post by savethewabbit on 2008-01-19
up...

---

### Post by ubuntu-freak on 2008-01-19
Is it onboard sound or a sound card? Have you booted in text mode and checked if it's not detecting your sound while loading everything?
 
Install startupmanager, easy way to boot in text mode.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-19
Might be worth installing the Hardy kernel. Set your sources list back to Gutsy straight after though.
 
Try this thread also
 
[http://ubuntuforums.org/showthread.php?t=647499](http://ubuntuforums.org/showthread.php?t=647499)
 
Nathan

---

### Post by savethewabbit on 2008-01-26
> **reassuringlyoffensive said:**
> Might be worth installing the Hardy kernel. Set your sources list back to Gutsy straight after though.
 
Try this thread also
 
[http://ubuntuforums.org/showthread.php?t=647499](http://ubuntuforums.org/showthread.php?t=647499)
 
Nathan

thanks for your help. how do i install the hardy kernel, and what is it exactly? i'm new to ubuntu, so sorry for the noob-like questions.

i have both a sound card and an onboard card, both recognized by ubuntu, but use the sound card. 
i've fiddled around these last few days and i've managed to get some sound.
in system - audio, i've set everything on "C-Media PCI DAC/ADC" (only option that shows sings of life), and while i can't hear sounds from any program other than totem (nothing from vlc, things online - i use firefox - ,  xmms... nothing but totem), now sound "works" every time even when i reboot. problems now are that a) the volume is so low it's nearly impossible to hear anything and b) as i said, it only works with totem. 
any ideas? 
please let me know if i have to give you more infos. 

also, there is another option on system - audio that "should work", i mean, at least it tries to give me the example sound (all the other options give me error messages), but i don't actually hear anything. i guess that's the sound card, the one that gives me problems and needs reinstalling of gdm and the other stuff + reboot in order to work.

edited to add: before anyone tells me to: yes, i've made sure that all of the necessary parameters in alsamixer were on and at max. :)

---

