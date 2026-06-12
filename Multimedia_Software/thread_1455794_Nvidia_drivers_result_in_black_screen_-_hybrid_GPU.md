---
title: "Nvidia drivers result in black screen - hybrid GPU"
date: 2010-04-16
forum: Multimedia Software
---

### Post by skipperkl2k on 2010-04-16
Hello everyone,

I feel absolutely dreadful doing a first-post like this, practically begging for advice, but I have been trying to figure this problem out (with the aid of google, various help files, real life buddies etc) for the better part of a week now, and I have gotten nowhere.


On both Karmic Koala as well as Lucid Lynx, I am having massive problems getting my nvidia card to register properly. I am on an Acer Aspire 5953 laptop pc with a Gt130m discrete GPU in a hybrid installation with an onboard GPU.

Freshly installed, both 9.10 and 10.04 runs smoothly, I can enable desktop effects, I can even see the screensavers that run openGL - although they run laggily in fullscreen, since they're obviously using the onboard, and very weak, GPU.

The problem however, appears whenever I install the suggested NVIDIA drivers that Ubuntu finds for me - after doing this, I am asked to reboot the system and on both systems, I am treated to a black screen, instead of a login-screen. The only way to get the system up and running again, I have found, is boot in fail safe mode and edit /etc/X11/xorg.conf, erasing everything. This lets me boot back up in a regular mode.

When I check the logs, both the onboard GPU and the gt130m GPU is located, the onboard as PCI:0:0:2:0 and the nvidia gt130m discrete gpu as PCI:0:1:0:0 - I have tried adding

BusID: ("PCI:0:1:0:0") to the xorg.conf, too, to no avail. I am continously treated to the black screen (a flicker at most) and the logs always tells me that no xserver could find no screens.

I have tried every single solution out there - it's really frustrating.

So far, I have only been installing Ubuntu inside windows - I am hesitating to install on a fresh drive, since I am afraid of the nvidia black screen putting me in a position where I can't access the system. 
Is it possible that the fact that I install ubuntu inside windows might somehow affect Linux's capability of accessing my discrete GPU?

---

### Post by skipperkl2k on 2010-09-12
Bump - still having this problem several months later.

---

### Post by aldenmalden on 2010-09-12
I am in a similar situation and unfortunately i cant help out much. I am a new user *wife is regular ubuntu user* i cant seem to find a supported driver for my ati xfx radeon hd 4650. Searching everywhere.... any suggestions?

---

