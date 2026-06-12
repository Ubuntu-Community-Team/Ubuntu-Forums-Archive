---
title: "Creative Xmod Volume knob"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by ceverett on 2007-05-13
Hi,

I have a nice Creative Xmod usb audio device that has this big fat volume knob on it.  Hotplug sees it as an input device, I think, and at certain points in the boot process, twiddling it will throw up garbage characters on the screen.

How do I set things up so the volume knob on the card does something useful like control the master volume for ALSA?

Christopher

---

### Post by Leviand on 2007-05-15
I've fixed this problem with 
System --> Preferences --> Audio --> Default Mixer Tracks: "Creative Xmod"

Then select PCM right above that option: that means that with that fat knob you will control volume... or at least, on me that has been worked.

Sry for bad english :)

bb!\\:D/

---

### Post by galloper on 2007-10-18
See here:
[http://galloper.kmip.net/2007/10/18/enable-volume-knob-on-xmod-usb-sound-card-under-linux-console-environment/]("http://galloper.kmip.net/2007/10/18/enable-volume-knob-on-xmod-usb-sound-card-under-linux-console-environment/")
Inspired by [this]("http://ejohansson.se/archives/2006/05/23/enable-dells-volume-knob-under-linux/"), I created a little program to enable XMod's volume knob. Tested on feisty.

---

### Post by c00ly on 2008-01-28
galloper, that website is down, is there any other way i can get that software?

---

