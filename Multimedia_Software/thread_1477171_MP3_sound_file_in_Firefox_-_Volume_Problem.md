---
title: "MP3 sound file in Firefox - Volume Problem"
date: 2010-05-08
forum: Multimedia Software
---

### Post by Bobhuber on 2010-05-08
Hey All
Got a problem and no clue.While trying to play an embedded MP3 sound file in Firefox the volume is automatically decreased.This happens when the page loads or is refreshed. I can open the system sound preferences, go to applications and slide the volume control up while the sound is playing and its fine.Alsa mixer controls are fine and Flash etc. work fine in Firefox.The minute you reload the page it shoves the volume control back down to 0.
The same page loads and plays fine in Google Chrome and IE6 using VBOX and loads fine with Karmic that I still have on another partition on my drive with the same version of Firefox (3.6.3).
After days of research there is a known bug in Lucid.Here is the fix. From a terminal prompt type the following (DO NOT USE SUDO OR GKSU)

gconftool --type int --set /apps/totem/volume 100

---

