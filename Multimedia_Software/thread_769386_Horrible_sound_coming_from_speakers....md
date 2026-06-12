---
title: "Horrible sound coming from speakers..."
date: 2008-04-26
forum: Multimedia Software
---

### Post by Toshibawarrior on 2008-04-26
Hi guys!, I'm kinda new to all this Linux thing and I tried the new version (Ubuntu Hardy 8.04) on my Toshiba Satellite A135 S4527...and well I got everything working: wi-fi, display, trackpad/mouse and so on...even the sound is working even though many people had problems with it. BUT when I try to use Rhythmbox the sound is low and horribly un-equalized...let me explain...

The sound I get from Windows Vista is like 3 times the one I get from UBUNTU and this is very frustrating since I'm always working with music.

I made a few sudo things and the sound got  a little higher but more distorted than before...

It sounds like Windows Media Player with the EQ setting at -0 ...nasty...

So is there any way to fix this?...This is driving me nuts, It's like using a Moto RAZR with MP3's inside a tin can, sound very bad. You know, getting better/higher sound and using an EQ for everything and not only Rhythymbox...it be nice to have a General EQ like the ones found on the driver apps of sound cards on windows...In UBUNTU everything I listen to sounds horrible...so any help will be highly appreciated!

I really need to fix this...

---

### Post by rafaelsaraiva on 2008-04-26
i'm having the same problem ... very unpleasant. i was using ubuntu 7.10, and it was running clean. after i installed the 8.10, the sound was without equalization, dirty and metallized. i have dual boot, and with win vista, the sound still perfect.

someone knows what's happening?

ps.
what is _really_ new in ubuntu 8.10? i confess that i'm disappointed.

---

### Post by Islington on 2008-04-26
Alright start with the basics, could you list what you have done with sudo I mean...


did you go to system>preferences.sound?

---

### Post by Toshibawarrior on 2008-04-26
Well I did a commando which i really can't remember but it was something "option...." and it finished with "intel-model-3stack" or something like that, which helped with the low volume issue, but the horrible distorted un-equalized sound kept being there...

I'm sorry but I really can't remember the exact "sudo code" but I DO remember i only used that one...and I did go to system>prefences>sound, and nothing in there helped at all......Im very new to this Linux thing...but I'll highly appreciate ANY help, even if i tried it before...

Or if you guys have any app/synaptic manager package/program suggestion to help me with this, please do post them.:popcorn:

---

### Post by rafaelsaraiva on 2008-04-27
well, i tried system > preferences > sound, and had test others possibilities [alsa, esd, oss, etc] for each topic in 'sounds preferences' [sounds events, music and films, audio conference, etc] and the sound problem stills.

then i tried to rebuild the alsa modules manually, with this command: 

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

i rebooted, but didn't work...

i have a hp pavilliondv6000, and how i said, in gutsy sound was running perfect. anybody?

thanks in advance.

---

### Post by markusX on 2008-04-27
i have the same problem after upgrading to hardy. sound was ok when i was still using gutsy. btw, i did a clean install of hardy and dual boots xp. sound on XP is ok. havent done anything yet to try and solve the problem.

---

