---
title: "Please help me with the speakers"
date: 2011-04-28
forum: Multimedia Software
---

### Post by indenser on 2011-04-28
I have two different speakers connected to my PC through two differnt audio ports.

I am using ubuntu (11.04)for the first time...Yeah I am a noob

In windows I used to select both ports as front speakers through realtek speaker set up page...

Here I'm at wits end...:(

PLz tell me how pass audio to both speakers equally with same audio level being served...

And how to normalize audio and master equalizer...

---

### Post by kostkon on 2011-04-28
What type of ports? Did you try all the available devices and profiles in your sound preferences?

---

### Post by indenser on 2011-04-28
Line in jack (blue)
Line out jack (green)

Only the green one is working

Yes I tried sound profiles and checked if any driver is working...no help or I am doing something wrong...

---

### Post by kostkon on 2011-04-28
> **indenser said:**
> Line in jack (blue)
Line out jack (green)

Only the green one is working

Yes I tried sound profiles and checked if any driver is working...no help or I am doing something wrong...
It seems that you need to activate a hardware switch that will make your line in output sound.

Open the software centre, search for the application
```
gnome-alsamixer
```
and install it.

Run it and then check all the available options, volume levels and switches that will be presented to you.

---

