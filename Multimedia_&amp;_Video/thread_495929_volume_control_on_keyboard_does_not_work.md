---
title: "volume control on keyboard does not work"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by nicolasdiogo on 2007-07-08
hi folks,

i am having difficulties trying to change the configuration for my keyboard to increasedecrease the volume of my desktop.

when i use the keyboard key (LOGITECH CORDLESS DESKTOP EX110) it changes the volume of SORROUND slider on the sound mixer, but the slider which actually changes the global volume is the PCM.

how can i make the keyboard change the PCM slider?

many thanks,


Nicolas

---

### Post by Daveth on 2007-07-08
as a guess I would have thought that you have to re-map the key - have you played around with System-Prefs-keyboard shortcuts, as this allows such mapping to take place?

---

### Post by WiseOdd on 2007-07-08
Ihve got the exact same problem, and using keyboard shortcuts doesnt help :(
Problem is that keyboard shortcuts doesnt help you changing the way the volume shortcut affects the slider. In volume control you cant decide which slider gets affected by the control buttons. 

In my case the "line in" slider is affected by the volume buttons.. Strange bcause it worked fine in 6.10...

---

### Post by nicolasdiogo on 2007-07-11
that has been my problem as well.

there is no remedy in re-mapping the keys, it has to do with the slider that is undertood to control the general sound.


thus i need to understand which configuration files make this work

---

### Post by nicolasdiogo on 2007-07-11
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/97530](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/97530)

there is a bug confirmed..

and the solution for me is from the above page on this posting:

 Santiago Canez said on 2007-04-18: (permalink)

Maybe you (the submitter) already knows this, but you can control what volume (PCM, Master, etc) the keyboard buttons change by selecting the required one under "Default Mixer Tracks" in Sound Preferences (System -> Preferences -> Sound). If your bug goes beyond this, then excuse this message :)

---

### Post by Theimon on 2007-07-11
I recently bought a Logitech Media Keyboard, with some extra buttons on it. Some worked out of the box, some didn't. I found an easy program in Synaptic that is easy to configure and works very good so far. Look in Synaptic for Keytouch.

---

