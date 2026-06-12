---
title: "Sound card issues"
date: 2008-08-29
forum: Multimedia Software
---

### Post by Strangewayz on 2008-08-29
Hi
 
I'm having issues with my soundcard and was wondering if anyone could suggest a fix for me. I have followed the [[COLOR=blue]Comprehensive Sound Problems Solutions Guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449&highlight=1010LT") but I still cannot record on my soundcard which is going to be the deciding factor on whether I stay with Ubuntu or not as I need to be able to record sound. I don't want to go back to shitty Microsoft so if anyone can suggest any 
 
I have two soundcards in my system (Ubuntu Studio 8.04 - although I have also experienced the same problem on Ubuntu 8.04) which are a Creative soundblaster audigy SE (ca0106 chipset linked to 5.1 surround sound) for sound playback and also a M-Audio 1010LT (ice1712 chipset) which is linked to my mixing desk. I have sound playback through my soundblaster and 5.1 speaker setup which is fine and have no problems. The problem lies with recording and playback through the M-Audio card and the problem being that it just doesn't happen. I have managed to get the Envy24 mixer to register the sound going in through the card but no sound is audible, I cannot record the sound and cannot playback any sound at all through the M-audio card.
 
When I typed 
 
```
 
aplay -l

```
 
both soundcards were displayed and the modules for both cards are loaded.
 
I followed the above mentioned instructions and purged the alsa drivers before reinstalling as described but again the problem was the same and it was also the same after recompiling the Kernel. I have a feeling it may have something to do with PulseAudio as when I go into the manager for PA it only displays details for the audigy SE but as I'm pretty new to linux and can't seem to find any user friendly documentation for PA I'm not able to look into PA further without help. 
 
As I'm a musician I'm basically useless without recording capability so any help anyone can give me will be greatly appreciated as as soon as this issue is fixed I will be free of MS forever.

---

### Post by markbuntu on 2008-08-29
If you are serious about recording, you should use UbuntuStudio. That way you can use jack to directly access the 1010 card for recording while leaving the SB card for other stuff.

You can peruse my extensive and longwinded guide about getting sound to work in Ubuntu. This may be helpful to you for getting a studio setup off the ground as there is a lot of important information you should be aware of and a zillion links:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Strangewayz on 2008-09-01
Thanks for this.
 
Just so you know I am currently using UbuntuStudio so will have a look at the links and have a go at tackling this issue tonight.
 
Cheers

---

