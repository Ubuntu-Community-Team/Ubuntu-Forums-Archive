---
title: "HDMI video: intermittent signal drop"
date: 2008-10-12
forum: Mythbuntu
---

### Post by dsbw on 2008-10-12
I'm working out the kinks on my MythTV system and am currently running an HDMI video out (with analog audio for now; I'm going to try HDMI audio later).

My TV does a thing where it shows what input is being used on changing the input or if the signal to that input is dropped. Currently, if I play back a ripped DVD at intervals ranging from a few seconds to a few minutes, the screen will go blank and the HDMI1 indicator on the TV will appear.

Curiously, I can't play the ISO using mplayer, VLC or xine outside of MythTV so I can't test there.

:confused:

---

### Post by dsbw on 2008-10-26
bump

---

### Post by jpentlow on 2008-12-31
I also have the same issue as yours. The signal seems to "drop" and then comes straight back again. Although It can happen at any time, not just in mythtv or when watching a ripped DVD. I have tried the other hdmi sockets but all show the same symptoms. 

My setup:
Sony KDL40v4000 (40 inch LCD)
GeForce 7300 LE running at 1920 x 1080
DVI -> hdmi cable
Mythbuntu 8.04

I don't think its the TV as the DVD player works for hours without any signs of the problem.

I'm also fairly sure its an issue with the current configuration as the TV is new and this issue was not apparent on my old CRT TV, but I was using the s-vhs output?

Any suggestions would be appreciated :D

---

### Post by jpentlow on 2009-01-09
Problem solved :P

After much swapping and changing of settings, cables etc. The problem was with my graphics card. I changed it for a GeForce 8300GS from XFX and hey presto the picture is now steady as a rock.

---

