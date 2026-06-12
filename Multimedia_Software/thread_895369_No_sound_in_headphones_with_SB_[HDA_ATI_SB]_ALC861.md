---
title: "No sound in headphones with SB [HDA ATI SB] ALC861VD"
date: 2008-08-20
forum: Multimedia Software
---

### Post by mirena_mir on 2008-08-20
Hello!

I am one of the many "lucky" people having problems with the sound with Linux... I use Ubuntu 8.04 on Toshiba L30 134. I have sound from the speakers (if I don't suspend or hibernate), but no sound in headphones.
The output of aplay -l is:

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I tried all suggestions I found in forumes: re-installing alsa, adding lines in  /etc/modprobe.d/alsa-base, but without any result. I tried with the following models (one by one):

options snd-hda-intel model=dallas 
options snd-hda-intel model=hp 
options snd-hda-intel model=3stack-660-digout 
options snd-hda-intel model=auto 
options snd-hda-intel model=3stack-660 
options snd-hda-intel position-fix=1 model=3stack
options snd-hda-intel model=3stack

But with any of them I was completely losing sound (both on speakers and headphones). Typing alsaximer in the terminal caused an error message and there was no alsa.
So, now I don't use any of these options, I have speakers working, but not the headphones.
And one more thing - in my alsamixer there is no option for headphones.

Any suggestions?

Greetings,
Mirena

---

### Post by markbuntu on 2008-08-20
Did you look here, there are other options you can try for your ALC861VD card:


[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

