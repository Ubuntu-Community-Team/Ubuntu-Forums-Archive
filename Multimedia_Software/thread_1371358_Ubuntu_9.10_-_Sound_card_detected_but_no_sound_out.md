---
title: "Ubuntu 9.10 - Sound card detected but no sound output"
date: 2010-01-03
forum: Multimedia Software
---

### Post by Sylos on 2010-01-03
Hello all.
I have recently upgraded to Ubuntu 9.10 and Im havin some problems gettin the sound aspect sorted out. I've had a look through the forums and googled around some and found a lot of problems with pulseaudio but none of them seem to describe the issue I have.
I have an M audio Delta 66 PCI card installed whcih worked fine with my previous hardy heron installation. The card IS recognised and listed by the system but whenever I try to play any media (mp3, avi etc) the player seems to be runnning and any visual aspect works fine but there is no sound comming from the card.
I have tried to change the settings and used the alsagui tool but to no avail.
Does anyone have any ideas why this is happening.
All suggestions gratefully received.

---

### Post by Sylos on 2010-01-03
Solved this problem.
I had the motherboard BIOS set to "Auto" to determine whether to use the onboard sound or not. Curious that this would be the problem given that  it has worked fine until this upgrade to 9.10 and 9.10 was detecting the right card.
Anyhow, all is well now.

---

