---
title: "Intermittent sound issues"
date: 2010-01-17
forum: Multimedia Software
---

### Post by Admiral Yi on 2010-01-17
Hello,
I have been having some weird sound problems. The sound works fine at the login screen, and when I play music off the pc its also fine. However, sometimes the Ubuntu startup tune doesn't play, and if I play a video on youtube there will be no sound. This problem doesn't happen everyday, just most days. I've had a look through my logs, and attached a screenshot of the messages I think explain the problem. I'm also getting two messages repeted in kern.log: 

PPdev0: unregisted paradevice
PPdev0: registed paradevice

These messages happen at exactly the same time. Dunno if they relate to this problem. 

If anyone can make some sense of the messages in the screenshot, help would be appreciated. If you need any more information, just ask. I really need this sorted out.

EDIT: just found some more messages, they're in another screenshot. Still can't amke much sense of them, other then they say that somethings broken.

---

### Post by sports.car.guy on 2010-01-17
It sounds like a pulseaudio issue to me. I believe I encountered that one with it years ago on Mandriva with the first version having it. It also sounds like it could be a matter of the system having a card swap happen on boot. That one I am going to deal with after a few hours of sleep myself.

I have my Creative X-Fi Fatality Titanium Pro and the HDMI on my AMD HD4670 swapping their positions making one priority then the other between boots and it is not a consistent thing either. There are a couple ways to solve this and it could be what is causing you some issue.

Your system could be loading sound modules improper to the order you need or even start up pulse before the one you need is loaded. That is if you are using pulseaudio in this instance.

I hope this help get you going in the right direction.

---

### Post by Admiral Yi on 2010-01-20
Right, sorry for not looking at this for a few days but I was busy. 

Those sound pretty reasonable, anyone shed any more light on what's wrong?

---

### Post by Admiral Yi on 2010-01-20
I am using the sound card built in to my motherboard, not a separate card. Could this be the issue? Also, not sure if I'm using pulse audio. Under System>Preferences>Sound it says im using 'HDA Intel ALC888 analogue (OSS)' for Movies and msuic. If I try and pick anything else music and movie playback stops altogether.

---

### Post by Yellow Pasque on 2010-01-20
You should be using pulseaudio output. It looks like you need to add your user to pulse-rt and pulse-access group to solve all the permission errors.

---

### Post by Admiral Yi on 2010-01-21
Didn't work. Added myself to those groups and changed sound output to pulseaudio. Also tried autodetect. Still no startup sound, still no sound on youtube, normal music wont play unlesss on the OSS one. Any other ideas?

---

### Post by Admiral Yi on 2010-01-21
Anything else I can do?

---

