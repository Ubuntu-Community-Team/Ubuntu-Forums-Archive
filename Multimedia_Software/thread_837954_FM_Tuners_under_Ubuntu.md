---
title: "FM Tuners under Ubuntu"
date: 2008-06-23
forum: Multimedia Software
---

### Post by Mikster on 2008-06-23
For a long time now, I've had an old Aztech fm tuner card running in one or another of my linux boxes. Most recently, it was working just fine under a disk install of Knoppix.

I recently upgraded that same box to Ubuntu 8.04, and have been extremely happy with the experience... except for one problem:

When I try using an application like kradio, the fm tuner card seems to find stations, scan the spectrum, and otherwise work exactly as it should... except that I get no sound. If I try running "fm" (a command-line tool for controlling fm radio cards, part of the fmtools package), same deal: the card appears to be working, but no audio. Note that all of this is the same hardware that was working just fine before the upgrade. The appropriate module (radio_aztech) loads just fine, alsa seems to be working just fine, all of the audio channels are unmuted and set to high volumes.

So, I have two questions for the Ubuntu community:

1. If the radio card appears to be working, and the sound system appears to be working, how should I go about further troubleshooting this situation? 

and...

2. If you listen to broadcast FM under Ubuntu, how do you do it? Do you use an FM tuner on your TV tuner card, a special-purpose piece of hardware like RadioShark, or something else? When I build my next box, I won't be able to use my same old card, and will have to move to something else... and I'd like to pick a piece of hardware that I already know works under Ubuntu.

Thanks for your help...

---

