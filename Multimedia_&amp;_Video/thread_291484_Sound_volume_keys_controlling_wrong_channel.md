---
title: "Sound volume keys controlling wrong channel"
date: 2006-11-02
forum: Multimedia &amp; Video
---

### Post by keltren on 2006-11-02
Just bought a shiny new mobo yesterday (P5LD2 SE (Rev.2.03)) and everythings working perfectly. 
The only problem I have is that the Volume control keys on my keyboard control the wrong channel, i.e. "Headphone" which doesn't do anything. The correct channel would be "Front". Is there any way to get gnome to use the "Front" channel for the keyboard controls? There must be some hidden setting somewhere to change this...

It may seem like a small thing but I've gotten so used to the keys that it's really annonying now that they aren't working anymore...

Changing the default channel in the mixer doesn't affect the keys unfortunately only the slider...maybe this should be reported as a bug...

---

### Post by ltmon on 2006-11-03
On Kubuntu you can do it, by telling KMix what the "master channel" is.  Right click on the kmix icon in the system tray and it should be obvious.

If it's Gnome, i really don't know what to do.  I used to fix it with a "softvol"... that is I would create a fake master channel with it's volume controlled by software.  Then it would be picked up.  You could try this... Google for "ALSA softvol".

L.

---

