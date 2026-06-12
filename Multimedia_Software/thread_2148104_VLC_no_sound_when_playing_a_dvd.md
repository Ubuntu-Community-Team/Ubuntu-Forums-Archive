---
title: "VLC no sound when playing a dvd"
date: 2013-05-23
forum: Multimedia Software
---

### Post by jdwaugh on 2013-05-23
So I installed VLC because the default player was giving me fits, VLC plays the DVD fine, but I have no sound.  However, if I play the DVD in Videos, which is Totem???, then I have sound so it is not the disc.  I used google to find that a lot of people had success by changing the Audio preferences to ALSA, but that did not work for me.  Can someone give me some help.  

I am trying to learn and switch over to using Ubuntu exclusively for my home use, No DVDs would bea kind of a drag.

---

### Post by ohnonot on 2013-05-24
what sound architecture are you using? my guess is pulseaudio on top of alsa as is pretty much standard on ubuntu these days.
last time i looked, vlc needed an extra package for pulseaudio support.
but before you install that, undo all changes you made with alsa and all that.
after installing pulseaudio support for vlc, you might need to change audio prefs again.

i hope this helps.

vlc is a cross-platform application and not native to linux.

---

### Post by jdwaugh on 2013-05-24
I reset the audior preferences, but I already had the pulseauudio plug in.  I don't know what my sound architecture is unfortunately

---

### Post by ohnonot on 2013-05-24
but you have to find that out.

edit: sorry that was a bit curt.
if you're using vanilla ubuntu and made no big changes, you most probably have pulseaudio.
open volume preferences, open autostart, see if pulseaudio is up and running and if it gets started on boot.
if other apps use sound and are working, make sure they also use pulseaudio. now make sure that vlc is in fact using pulseaudio.

---

### Post by jdwaugh on 2013-05-24
I got it to work, by changing it to pulseadio, closing VLC and restarting and this time it works.  LAthough I had done it before so maybe a setting didn't dtick.  THanks for the help

---

### Post by ohnonot on 2013-05-25
you're welcome, glad to be of help.

---

