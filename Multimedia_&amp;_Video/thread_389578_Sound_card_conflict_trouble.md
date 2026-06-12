---
title: "Sound card conflict trouble"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by Halfling Rogue on 2007-03-20
Not sure which forum this belonged in, so threw it in a couple.

I've been having sound conflict problems with my Dapper for a while. I can play mp3s on XMMS just fine, and audio CDs, but if I try to play any variation of Flash, including YouTube, I get no sound. If I have XMMS open while I try to play a YouTube, I get an error from XMMS saying another program is using my sound. I also tried to install the .deb package for the lastfm.com software, and the Package Installer keeps failing with the error message:

**[COLOR="Red"]Error: Dependency is not satisfiable: libasound2[/COLOR]**

I also tried to download libasound2-dev, libasound2-plugins, libjack0.100.0-0, and xmms-scrobbler via the synaptic package manager, but all of them failed to download. I have no idea how to fix this. :(

---

### Post by crispy_420 on 2007-03-21
Do you have two sound cards? (mobo and pci?)

I had the same issue until I disabled mobo sound in bios.

---

### Post by Halfling Rogue on 2007-03-21
I don't *think* I do. Although when I start up my computer I'm getting an error message:

ERROR
Resource Conflict - PCI Display Controller on Motherboard
Bus:00, Device:06, Function:00
<esc> resume, <F1> setup

So, uh, maybe it's my video card (or its drivers). Although I don't know how to fix that either. >_>

---

### Post by Halfling Rogue on 2007-04-06
Okay! Haven't tried last.fm again yet, but I installed Flash 8 as my Firefox plugin and all of the sudden I have sound for Flash again, including on YouTube. Maybe it's just a version-specific bug or something.

---

