---
title: "Asus Xonar DG"
date: 2012-04-26
forum: Multimedia Software
---

### Post by Zyxer22 on 2012-04-26
So, I decided to give Ubuntu 11.10 a shot on my desktop. My desktop has an Asus Xonar DG installed, which I'm pretty sure is what's causing my issues. I've tried searching this card and it seems that it has issues with Linux.

When I attempt to use my headphones, my computer doesn't recognize they're plugged in. I'm pretty sure it's because of the sound card since I have it set up through the front panel. When I put the Front Panel plug into the motherboard rather than the sound card, the sound played out of my headphones just fine. It's also of note, that my sound only works when it's set to run through Nvidia HDMI 2.

Like I'd said, I have Ubuntu 11.10 and  I've installed all the updates. And, my version of alsa is 1.0.24

I'm not sure what (if any) more information might be necessary, so whatever you need to know, just ask me and I'll be glad to post it. And, thanks fro any help.

---

### Post by Zyxer22 on 2012-04-27
Bump? I'd just really like to get this working. Does anyone know if 12.04 has a fix for this?

---

### Post by Zyxer22 on 2012-04-28
Bump again?

---

### Post by meluxx on 2012-05-03
I'am using 12.04 and its working here, havent testeid it alot, it has 3 outputs

speakers
headphones 1
headphones 2
not sure witch is right one for headphones, but i think headphone amplifier is working (soundcard is making fysically click sound when changing output channels)

too bad i cant configure it fully as i could in windows (change channels and stuff)

---

### Post by Zyxer22 on 2012-05-06
Well, I can play the headphones through the back using Oxygen HD Audio headphone 2, but I can't play through the front panel, nor do any of the Oxygen options play through my monitor's built in speakers, which is annoying.

edit: Yeah, mine makes the click sound whenever I switch my output slot as well.

---

### Post by Yellow Pasque on 2012-05-07
Known bug: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/919809](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/919809)

---

### Post by akvenugopal on 2012-09-20
> **Zyxer22 said:**
> Bump? I'd just really like to get this working. Does anyone know if 12.04 has a fix for this?
I am using ASUS Xonar DG under Ubuntu 12.04. Yesterday it stopped working. I am searching for a solution.

---

### Post by BodaciousBrian on 2012-10-05
I have a Xonar DG in 12.04 also.  The output works great, but no matter what I try, with alsamixer, or different ports on the card, I can not get any input.

---

