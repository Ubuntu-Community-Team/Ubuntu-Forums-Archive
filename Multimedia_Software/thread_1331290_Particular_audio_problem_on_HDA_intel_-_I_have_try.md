---
title: "Particular audio problem on HDA intel - I have try all your guide!"
date: 2009-11-19
forum: Multimedia Software
---

### Post by N!coz on 2009-11-19
Hi! I'm a disperate italian ubuntu user :p

I have read all the proposed guide on this fantastic community...but my problems still remains the same!
The problem that i have, is began on the 9.04 and persist on the 9.10 ! 

I have a ASUS P5Q DELUXE, the results of aplay -l is :

```
alessandro@ubunico:~$ aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: AD198x Analog [AD198x Analog]
  Sottoperiferiche: 0/1
  Sottoperiferica #0: subdevice #0
scheda 0: Intel [HDA Intel], dispositivo 1: AD198x Digital [AD198x Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
```

and the answer of lspci -v is :

```
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Device 8311
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```


Now i explain my  problem ; 
I can hear the audio correctly but my problem is on the microphone... it seems doesn't work!
This problem that i have on 9.04 will persist on the 9.10... can we take me a hand to solve this problem? 


I wish tell another specification : in the audio settings, in HARDWARE panel is configured as Analog Stereo DUplex, and after the following of this guide [http://www.unixmen.com/linux-tutoria...0-karmic-koala](http://www.unixmen.com/linux-tutoria...0-karmic-koala)

the microphone bar ( in the record software) seems to move when i move the microphone or if i punch on the desk.. but if i try to test for example on skype, i hear only rustle... sorry for the trouble.. I hope that my horrible english is understanded by you!

---

### Post by grayrainbow on 2009-11-19
As far as I remember skype work with pulse audio, so you have to go in skype audio settings and try to set it on it.

---

### Post by kostkon on 2009-11-19
What version of Skype are you using?

---

### Post by N!coz on 2009-11-19
> **kostkon said:**
> What version of Skype are you using?


Oh i'm sorry.. probably my description of the problem maybe not clear!

The mic don't work anyway with any application!
If i try to register with the ubuntu default sound recorder i see the microphone bar mooving only when i punch on the desk or if i move the mic... but i don't ear anything in the registration!
If i try with audacity or similar.. the result is the same!
Skype is one of the various application with i can try to use the microphone but without any good results!

Anyway my skype version is: 2.1.0.47

:p

---

### Post by N!coz on 2009-11-22
there is another new problem...

when k3b (for example) finish his work and try to send the "finish sound working" , appear that message:  Phonon: KDE's Multimedia Library .. The audio playback device HDA intel (ad198x analog) does not work. Falling back to HDA Intel ( ad ecc)..
What is the problem? i can feel the audio and the sound from sofwtare as skype & company.. someone can answer? thanks

---

### Post by N!coz on 2009-11-27
someone can help me? i can't find the driver on the intel website ( for my hda intel audio cards).. someone know the links?

---

