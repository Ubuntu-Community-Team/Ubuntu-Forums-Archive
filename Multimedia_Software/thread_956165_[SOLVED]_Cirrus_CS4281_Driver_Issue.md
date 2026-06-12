---
title: "[SOLVED] Cirrus CS4281 Driver Issue"
date: 2008-10-22
forum: Multimedia Software
---

### Post by dnlcorrea on 2008-10-22
Hello,

I am trying to make a CS4281 soundcard work on my IBM Thinkpad X20. Ubuntu recognises the card, but it doesn't play any sounds. I tried to install all alsa-related packages, load and reload modules, recompile kernel and nothing seems to work. Can anyone give me a help?

Thanks in advance,

DNL

---

### Post by dnlcorrea on 2008-10-23
Solved!

[http://ubuntuforums.org/showthread.php?t=205449&highlight=cs4281](http://ubuntuforums.org/showthread.php?t=205449&highlight=cs4281)

 sudo modprobe snd-cs4281
 sudo nano/etc/modules #add sndcs4281 to it
 alsamixer #volumes UP
--> > System > Preferences > Sound 

Ta-da! It just worked...go figure.

Hope it helps...

DNL

---

