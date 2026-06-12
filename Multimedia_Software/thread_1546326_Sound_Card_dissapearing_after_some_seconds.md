---
title: "Sound Card dissapearing after some seconds"
date: 2010-08-05
forum: Multimedia Software
---

### Post by sapoleon on 2010-08-05
Hi, 
I have a problem that I don't even understand. I have not used linux much, and I am trying to move my small bussines from ms to linux. 

I started with my first machine, and Ubuntu 10.4. I must say that everything started smoothly. zero problem. 
I have installed wine and make the tests for our bussiness program, and even printing was almost flawless (must make a small change somewhere because it start printing a little lower than windows and I have preformated receips)

So.. it all started when I wanted to use skype. skype installed also without problem, and it seemed to start ok, I make the first call, and after a couple of seconds, no more mic or sound. I thought it was skype, but it seems not.

what I have, is a VT1708 VIA, Onboard sound card.

I followed one of the guides in the forum, to see if all is installed and seems to work... and it is. it seems all fine. 

Even more, I installed the ALSA mixer, and when I enable the mic from there, it works.

But, when I open the sound prefferences, the sound card appears in Hardware and Input, when I open it, but some seconds after, it dissapears. Still working from the ALSA thou.... 

In conclusion, I can not use skype or similar. and the sound dissapears from the system, even if I can use it form the ALSA mixer.... 

Any ideas?
Any more info I should post for someone to help?.... 

I can't change the other computers to linux unless I prove to the people here that everything is working 100%.... and belive me... today skype phone is a must... in the bussiness.

Thanks to all from now

---

### Post by sapoleon on 2010-08-05
Hi, 

I have a strange problem. I have a sound card on board, and it stops working after a couple of seconds... let me explain.

First of all, I don't have much experience with linux, and I am moving my bussiness computers to ubuntu 10.4 x64 (in this case). I just made my first computer, and it all seems to be working fine. Wine with a small custom program, printing and all, Open Office is great. The people is liking the system, and everything started smoothly. 

So, the problem started when I wanted to use Skype. I installed, and seems everything OK. I make the first call, and after a couple of seconds, the audio in skype was death. no mic, no sound.
I thought it was a skype problem at the begining, but now I don't think so.

I checked now with the guide posted in teh forum, and everything seems fine. the card is recogniced, the drivers seems to be ok. BUT, when I open the  Sound Preferences, after a new start, I see in Hardware and Inputs the sound card, but after a few seconds, it dissapears, and it's all dissable.

I installed the ALSA mixer, and even when in the sound prefferences all is grey, I can enable and use the mic with the mixer. Not so with skype. or other applications that are aparently not the ALSA itself.

Because of the work, skype is a must, and sound is always desirable. So, does anyone have a tip? ideas?
Do you need more info that i must post?

Thanks in advance.


---------------------------------
aplay -l (response)
tarjeta 0: VT82xx [HDA VIA VT82xx], dispositivo 0: AD198x Analog [AD198x Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: VT82xx [HDA VIA VT82xx], dispositivo 1: AD198x Digital [AD198x Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

---

### Post by sapoleon on 2010-08-06
Solved when installed the ALSA 1.0.23

---

### Post by sapoleon on 2010-08-06
Solved with ALSA 1.0.23

---

