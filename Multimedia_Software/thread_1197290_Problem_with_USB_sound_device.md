---
title: "Problem with USB sound device"
date: 2009-06-25
forum: Multimedia Software
---

### Post by valles on 2009-06-25
Heres an interesting problem:
So i have two soundcards. An NVidia vt1708b (onboard), and an MAudio Fast Track Pro. I installed both WINE and VLC today, and at first niether of them had sound. Fast Track Pro is the systems default sound card, because it is connected to a reciever. After some tinkering (disabled pulse audio, installed ALSA drivers) i managed to get some sound to come from VLC and WINE. The problem is, both apps output to the the vt1708b, even though (as far to my knowlage) there are no config settings telling them to output to anything other than the default card. Im pretty much a beginner, and this is all verry confusing. any help would be greatly appreciated.

---

### Post by valles on 2009-06-26
Ok, problem solved. i just downloaded and installed alsa-usb and compleatly disabled the onboard card.

---

