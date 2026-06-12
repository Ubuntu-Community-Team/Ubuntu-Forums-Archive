---
title: "i dont get sound when i watch videos on the net"
date: 2008-10-21
forum: Multimedia Software
---

### Post by cowboyup8606 on 2008-10-21
everytime i  try to watch a video on you tube or metacafe  im not getting sound yet when im watching a movie on ubuntu's movie player or rythem box it get sound can anyone hlp me plz

---

### Post by darthshak on 2008-10-21
Do you have Rhythmbox open while watching videos on Youtube?

I have a problem where youtube does not play any sound when rhthymbox is open. I'm not sure if this is a bug or not. Closing rhythmbox and restarting firefox should do the trick.

---

### Post by cowboyup8606 on 2008-10-21
yea i do ill close it and try it

---

### Post by BigKO114 on 2008-10-21
I have a similar problem.  I'm using Banshee as my music player, and it plays through my sound card (m-audio mobile pre) but I cannot get playback through a web browser from my mobile pre.  Any ideas why only the browser isn't playing back?

---

### Post by wolfen69 on 2008-10-21
this is a common problem. ```
sudo apt-get install libflashsupport
``` restart firefox if open.

---

### Post by patrickballeux on 2008-10-21
Are you using Flash 9?  If so, you have to install libflashsupport that will make it compatible with Pulseaudio.

But better, simply install Flash 10 which is already compatible and working better.  

The problem you have is that Flash is trying to talk to your ALSA sound card, already locked by the Pulseaudio Server (While playing your banshee/totem/whatever).

And also, it means that your sound card does not have a hardware mixer, so you need (like the majority of us) a software mixer (Pulseaudio, already installed in Hardy).

I would suggest installing "pavucontrol".  You will then be able to see what is connecting or not to the pulseaudio server (Open Volume Control.. 1st tab...).

Ah, yes, also, open the "System - Preferences - Sound", and switch everything to "Pulseaudio". 

That should do the trick.

Good luck!

---

### Post by BigKO114 on 2008-10-22
patrickballeux, your suggestion does work.  I am running flash 10, but my card is an external mobile preamp.  Your suggestion doesn't work with this external card.  I am new to this kind of thing, so I don't pretend to know everything.  I understand that the problem is with having a sound mixer to combine both player output and browser output.  I am just unsure how to link them together, and through which sound mixer.  Thanks in advance for all the help.

---

### Post by chocka on 2008-10-22
Since I have the 8.10 Beta version libflashsuport does not work - however the following does 'sudo apt-get install flashplugin-nonfree-extrasound'.

---

