---
title: "Mythbuntu 12.04 turns off computer - often"
date: 2012-06-04
forum: Multimedia Software
---

### Post by rmhurt on 2012-06-04
i had a harddrive die in my Mythbuntu 8.10 setup (one of three hdd's) and when i got a replacement hdd i took the opportunity to do a clean install of 11.10 and upgrade mythconverg to the 0.24 schema, and from there upgrade to Mythbuntu 12.04 and MythTV 0.25.  this seemed to work fine and there were no unexpected shut-downs of the computer while i was getting it to work, about 24 hours of work say.  at this point the only hdd attached was the new one, a SATA hdd attached to an IDE motherboard using a Rosewill SATA-to-IDE adapter.

on Saturday i brought the other two hdd's into the mix by adding them to fstab and added them to MythTV, and voila i had all of my recordings available to watch on MythTV 0.25; i thought i was golden.  But then, the computer just shut itself off suddenly.  I was attached with putty and got a warning, just before it turned off.  since then, it has turned off on a regular basis, especially while watching a recording.  twice while i watched one episode of Hawaii 5-0, and apparently 8-10 times while my wife was watching several hours of shows last night.

Mythbuntu 8.10 never did this, and my hardware is the exact same except for the new hdd - which worked fine for the one week it was the sole hdd.  one exception is that i figured out how to attach an older hdd via SATA cable instead of using the Rosewill adapter, by adding a jumper to the hdd which apparently throttles the transfer speed from 3Gb to 1.5.  one thing i am going to do tonight is remove the SATA cable and go back to using the Rosewill adapter.  i have an old nvidia 5200 card using the nvidia-173 driver, which only works by pinning xorg to a non-current version.

i poked around some of the /var/log logs but couldn't find anything, but i'm not sure which ones are my best bet.  thoughts on how i might find out what's causing this?  one thought of mine is that maybe the cpu temp is too high, but putty got a warning of the shutdown and it doesn't seem like it would have if the temp was the problem.

---

