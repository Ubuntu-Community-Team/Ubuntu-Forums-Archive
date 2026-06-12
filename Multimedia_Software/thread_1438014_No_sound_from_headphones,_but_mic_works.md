---
title: "No sound from headphones, but mic works"
date: 2010-03-24
forum: Multimedia Software
---

### Post by eminembdg on 2010-03-24
Ok, Redsingularity told me i should start a new thread with my problem.

I have Ubuntu 9.10. Clean install. I have a cheap headset but can't get sound to come thru the headset. The mic works, but sound only comes from main speakers.

I do not have a HP, SONY or anything like that. I bought my pc barebones and built myself. So there doesn't seem to be any easy fix for my pc. Here are the specs:

Gigabyte MB model# GA-M61SME-S2

This is my aplay -l :

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

anything else you need just tell me what to do.. any help will be greatly appreciated.

---

### Post by RedSingularity on 2010-03-24
Do you have any other headphones laying around?  Maybe an Ipod set or something.  I would suggest you plug in another set of headphones and see if you have the same problem.

---

### Post by eminembdg on 2010-03-24
hmmm... tried pair of ipod headphones and still no sound.....

---

### Post by RedSingularity on 2010-03-24
Odd......do you happen to have winblows installed on that machine?  If you do you can test it in that.  It may be a bad Jack.  There is no software necessary to put the sound through the headset.  Once you plug it in it closes a circuit inside the computer and allows the sound to come through the headset.  Since yours is not working the problem may be the Jack.

Edit: Oh  I see your next post.

---

### Post by eminembdg on 2010-03-24
also, right before i installed Ubuntu I was using Windows and everything was fine

---

### Post by eminembdg on 2010-03-24
> **RedSingularity said:**
> Odd......do you happen to have winblows installed on that machine?  If you do you can test it in that.  It may be a bad Jack.  There is no software necessary to put the sound through the headset.  Once you plug it in it closes a circuit inside the computer and allows the sound to come through the headset.  Since yours is not working the problem may be the Jack.

Edit:  I see your next post.

I may have to retry to hook up the front sound ports. maybe you are right and my rear jack is broke... I didn't hook them up because it didnt' work becaue obviously the MB wasn't made specifically for the case and I couldn't figure out the correct connections to make front jacks work

---

### Post by RedSingularity on 2010-03-24
Edit: .......

---

### Post by RedSingularity on 2010-03-24
> **eminembdg said:**
> I may have to retry to hook up the front sound ports. maybe you are right and my rear jack is broke... I didn't hook them up because it didnt' work becaue obviously the MB wasn't made specifically for the case and I couldn't figure out the correct connections to make front jacks work


That may be the problem then.

---

### Post by eminembdg on 2010-03-24
I don't believe so. If PA wasn't included with 9.10 then it's not installed

---

### Post by RedSingularity on 2010-03-24
> **eminembdg said:**
> I don't believe so. If PA wasn't included with 9.10 then it's not installed


Disregard that.  Try re-hooking the ports again.  It may be your problem.

---

### Post by RedSingularity on 2010-03-24
It does in fact sound like a hardware problem rather than a software one.

---

### Post by Hikayu on 2010-03-24
> **eminembdg said:**
> I may have to retry to hook up the front sound ports. maybe you are right and my rear jack is broke... I didn't hook them up because it didnt' work becaue obviously the MB wasn't made specifically for the case and I couldn't figure out the correct connections to make front jacks work

Have you tried putting your headphones in and seeing if the speakers are still on?

Also, try removing the speakers from your computer prior to putting the headphones in.

---

### Post by eminembdg on 2010-03-24
> **RedSingularity said:**
> Disregard that.  Try re-hooking the ports again.  It may be your problem.

i will try the unhooking of speakers before headset

---

### Post by RedSingularity on 2010-03-24
> **eminembdg said:**
> i will try that later and repost 

thanks for your help. really appreciate it


No problem.  Let us know what happens.

---

### Post by eminembdg on 2010-03-24
ok, if i disconnect the green jack for my main speakers and plug my headset into that, then I do get sound. 

If i try to just use the blue, headset jack, i get no sound even with main speakers unplugged

maybe i need a splitter so that i can plug main speakers and headset into the green output jack and then maybe i'll get sound from both

---

### Post by RedSingularity on 2010-03-24
> **eminembdg said:**
> ok, if i disconnect the green jack for my main speakers and plug my headset into that, then I do get sound. 

If i try to just use the blue, headset jack, i get no sound even with main speakers unplugged

maybe i need a splitter so that i can plug main speakers and headset into the green output jack and then maybe i'll get sound from both


Thats exactly what i have done on my PC.

---

### Post by Hikayu on 2010-03-24
> **eminembdg said:**
> ok, if i disconnect the green jack for my main speakers and plug my headset into that, then I do get sound. 

If i try to just use the blue, headset jack, i get no sound even with main speakers unplugged

maybe i need a splitter so that i can plug main speakers and headset into the green output jack and then maybe i'll get sound from both

Ahem : The green jack is for speakers. The blue jack isn't. 

I think...

---

### Post by eminembdg on 2010-03-24
> **Hikayu said:**
> Ahem : The green jack is for speakers. The blue jack isn't.

then why did it always work in windows?

---

### Post by Hikayu on 2010-03-24
> **eminembdg said:**
> then why did it always work in windows?

Ok. I have the *exact* same problem as you than. I always thought that the blue jack was for something else.

---

### Post by RedSingularity on 2010-03-24
Use the splitter.  It works great on my PC and i dont have to continuously switch from headset to speakers.

---

### Post by eminembdg on 2010-03-24
> **Hikayu said:**
> Ok. I have the *exact* same problem as you than. I always thought that the blue jack was for something else.

yea, it even has the same little speaker logo above it as does the green jack port. and it always worked in windows.

i will just get a splitter then and do it that way. just need headphone sound for TeamSpeak

Thank you so much for your help guys. Need to go do some pc work at my aunts house. bye

---

### Post by RedSingularity on 2010-03-24
> **eminembdg said:**
> yea, it even has the same little speaker logo above it as does the green jack port. and it always worked in windows.

i will just get a splitter then and do it that way. just need headphone sound for TeamSpeak

Thank you so much for your help guys. Need to go do some pc work at my aunts house. bye


Glad you got it worked out :)

---

