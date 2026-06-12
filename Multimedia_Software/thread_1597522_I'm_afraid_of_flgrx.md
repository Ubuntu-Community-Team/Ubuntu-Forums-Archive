---
title: "I'm afraid of flgrx"
date: 2010-10-15
forum: Multimedia Software
---

### Post by xaegis on 2010-10-15
:)I'm affraid to load the repo ati drivers on my new system with the ati 5730. I tried the ati drivers on a different system and I got screen artifacts and boot/splash screen issues. Is there a write up on how to fix this problem or should I wait till the open source drivers catch up?  I would really like the 3d acceleration but I dont want to sacrifice stability or uniformity. What is the general consensus of the drivers?

---

### Post by SpEcIeS on 2010-10-15
Here is a PPA for you to try out:

> sudo add-apt-repository ppa:xorg-edgers/radeon

Remember, it is a testing PPA. Good luck. ;)

[the upper :x is a : x together]

---

### Post by xaegis on 2010-10-15
> **SpEcIeS said:**
> Here is a PPA for you to try out:



Remember, it is a testing PPA. Good luck. ;)

[the upper :x is a : x together]

What does this very unhappy ppa do? I cant apply it till I get off from work.

-e

---

### Post by xaegis on 2010-10-16
Warning to anyone reading this; this PPA "BORKED" my system(system hang on startup), if you're using an ATI 5730 card. I tried the hotfix listed on the ATI website but No Bueno! I guess I will have to wait till next kernel update for better drivers.

---

### Post by SpEcIeS on 2010-10-16
Ouch! Sorry to hear that. Did you have any problems removing the PPA?
```

Uninstalling:

Use ppa-purge or remove any references (in sources.list) to this PPA and run:
sudo apt-get install libgl1-mesa-dri/lucid libgl1-mesa-dri-dbg/lucid libgl1-mesa-glx/lucid libgl1-mesa-glx-dbg/lucid libglu1-mesa/lucid mesa-utils/lucid
```

**[https://launchpad.net/~xorg-edgers/+archive/radeon]("https://launchpad.net/~xorg-edgers/+archive/radeon")**

So far so good on my system, however GoogleEarth will kill xorg and reload the login manager. When the Maverick fglrx drivers were applied to my system GoogleEarth would only begin to start and then crash.

Now I am waiting for the axe to fall. :rolleyes:

---

### Post by xaegis on 2010-10-16
I tried to install the hot-fix from ati but it said I had the wrong kernel for it. I had everything on a separate home partition so no biggie I just reinstalled. I think I will wait a month to update my video drivers, see if it gets sorted out. Thanks for the update with how to remove the ppa tho.

---

