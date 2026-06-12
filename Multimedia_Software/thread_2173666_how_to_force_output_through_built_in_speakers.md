---
title: "how to force output through built in speakers"
date: 2013-09-10
forum: Multimedia Software
---

### Post by jonah3 on 2013-09-10
hi, i have broken my headphone jack in the headphone port of my laptop and now it is permanently stuck in headphone mode and no sound will come out of the inbuilt speakers. i have tried selecting speakers in pulseaudio and disabled automute in alsamixer but nothing has worked. anyone got any other ideas. i'm running 12.04 on a lenovo r500. any help would be much appreciated. best wishes, jonah

---

### Post by Yellow Pasque on 2013-09-11
Try playing with hda-jack-retask. Hopefully, it will allow you to completely disable that jack:
```
sudo apt-add-repostiory ppa:diwic/hda
sudo apt-get update
sudo apt-get install hda-jack-retask
hda-jack-retask
```

---

### Post by zombienerd1 on 2013-09-11
It is possible that your hardware physically disconnects the speakers from the card when there are headphones inserted.  I know there's no way to get my Netbook to play sound through it's primary speaker if there is a set of headphones plugged in, even in Windows it was impossible.

I would recommend getting the broken headphone plug removed.  You can do it yourself with about 10-15 minutes and some patience. (Up to an hour if it fails the first or second time)

You'll need a drinking straw, a toothpick, and some super glue.

Cut 2" off the straw, then use a knife/razor to slice the straw up the center.  Roll it together until it's about the size of the plug.  Slide it into the jack around the broken plug.  Take your toothpick and DOUSE the end of it with super glue.  You should soak the end of the toothpick well.  Stick the toothpick into the straw until it touches the broken end of the plug, and let it sit about 10 minutes.  Then, pinch the straw to the toothpick so you're holding them both, and pull out slowly.  You should have the headphone plug removed.  

The last time this happened to me, it took 2-3 tries and about 45 minutes total to get it pulled out, but it works.

I know that's not the answer you were looking for, but I hope it helps.

---

