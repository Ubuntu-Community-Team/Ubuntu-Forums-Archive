---
title: "Sound profile resetting every time (AMD64)"
date: 2009-11-01
forum: Multimedia Software
---

### Post by Ken-san on 2009-11-01
Hi all, I wanted to file a bug on this (somewhat annoying) issue I have with sound profiles on Ubuntu 9.10 x64, but since I wouldn't know where to start, I thought I'd ask here first.

The issue is as follows: 
I have an EVGA 680i motherboard, and a Genius 5.1 surround system. Sound was working just fine in 9.04, but after the fresh install of 9.10, and choosing the appropiate (5.1) sound profile in System -> Preferences -> Sound -> Hardware, sound pops and makes weird noises. After testing for a bit, I found that the most appropiate one was the Analog Surround 7.1 Output one.

It would seem that there wouldn't be any more problems after this, but after playing songs for a while in Rhythmbox, the profile seems to reset and I lose all sound on my subwoofer. If I go to the Profile page again, change it to another one, and revert back to 7.1, sound returns to normal. I'm sure that this only happens when I manually advance to another song (by clicking Next/Back) or choosing another one from the playlist. It's really annoying because I have to go and change the profile every time I change a song (and I get weird noises after every profile change).

Edit: Also confirmed it with Totem. It's even worse, because, while Rhythmbox did it only after manual song changes, Totem does it for every song change, automatic or not.

Anyone have the same problem, or have any ideas to solve it/file a bug?

---

### Post by Ken-san on 2009-11-01
Just thought I'd bump the thread up. I realize now the problem lies with PulseAudio or ALSA, don't know which.

---

