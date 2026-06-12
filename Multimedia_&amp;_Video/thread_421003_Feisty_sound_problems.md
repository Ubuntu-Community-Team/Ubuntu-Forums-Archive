---
title: "Feisty sound problems"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by easyfragger on 2007-04-24
Hi, I have two questions related to sound issues in Kubuntu Feisty 64bit.

First: Are there any drivers for the soundblaster x-fi series from creative yet? Up to now, I did not manage to get my x-fi working, and therefore used my onboard sound chip (board is an asus p5b). Sound is mostly working fine, but sometimes (quite often, actually), I have no sound when after booting. In these situations, I can for example play songs with amaroks without any complaints from the software, but I just don't hear anything. Restarting the system then usually resolves the problem temporarily. So my second question is: What could be wrong here? :confused: Restarting the sound server via the admin panel does not help, by the way. Don't know if it helps, but "audio hardware" is set to "automatic config" there.

Any help appreciated, of course, :(

---

### Post by ghannakc07 on 2007-04-26
I'm needing an answer to this question also... I just installed Feisty via Wubi, and got booted into the GUI (after figuring out that Feisty didn't install Nvidia GFX drivers), and Feisty told me that I didn't have a sound card installed.  My on-board audio is disabled in BIOS and I have a Soundblaster X-Fi card that works fine in Windows XP.  Are there drivers for this card or a way to get Feisty to recognize it?

---

### Post by robertsaron on 2007-05-18
Some thing I have wondered for a long time. What kind of onboard audio will work with Feisty right out of the box? Preferrably a motherboard with a pcie amd  with no file manipulation or installation?

I have a friend who refuses to have windows (YAY), and wants linux, preferrably Kubuntu. but the Audio MUST WORK out of the box. they know very little about computers (and I know very little about linux), and if they have to reinstall for one reason or another, they need the audio to work from the get go. I was told anything with nforce 1,2,3 should work, possibly 4. 

Can anyone confirm this or make recomendations?

---

### Post by Lord Illidan on 2007-05-18
HDA Intel seems to work well, with a little tweaking of modprobe.conf

Regarding X-FI, it seems that Creative is being held up by Vista, so Linux drivers will be a long time coming :(

---

