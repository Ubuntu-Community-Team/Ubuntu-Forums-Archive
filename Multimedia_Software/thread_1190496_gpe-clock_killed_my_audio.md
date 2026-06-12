---
title: "gpe-clock killed my audio"
date: 2009-06-17
forum: Multimedia Software
---

### Post by amp_man on 2009-06-17
Last night my alarm clock died, so I decided to try out gpe-clock, to see if it'd wake me up. I installed it, set the alarm to go off about 3 minutes from then, and went back to watching a movie with totem. When the clock went off, it made its little ding just fine, but the movie's audio went to all static. A few more tests showed that all audio is now varying levels of static, including the startup sounds, and I've tried vlc, banshee, and rhythmbox as well. I removed gpe-clock and all the packages that were installed with it, and rebooted the computer, still the same symptoms.

I'm running Ubuntu 9.04 on a Dell XPS M1530.

EDIT: the answer is always so obvious once you've posted the question online. I guess I overlooked that the PCM in the mixer was turned all the way down, not sure why that'd result in static though.

---

