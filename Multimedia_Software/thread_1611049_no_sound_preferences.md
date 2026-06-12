---
title: "no sound preferences"
date: 2010-11-01
forum: Multimedia Software
---

### Post by tommah04 on 2010-11-01
hey all,

unusual problem, I can't get to my sound preferences.  I tried right-clicking on the volume button > Sound Preferences but nothing happens.  I tried going to System>Preferences>Sound, but it isn't an option.  Now this isn't a HUGE deal because my sound does actually work, just fine in fact.  But it would just be nice cause I used to use it every once and a while.  Its probably a really simple and stupid but I can't figure it out

Ubuntu 10.04
amd64


Thanks!

---

### Post by triumphguy on 2010-11-03
I have a similar issue.  I have sound but can't access sound preferences or adjust the sound.

Hopefully an update will be coming soon.

10.10  64bit

Ronnie

---

### Post by tommcd on 2010-11-03
Did either of you remove **pusleaudio**? Removing pulseaudio will disable the: system > preferences > sound applet.

You can adjust the sound with **alsamixer** in the terminal. You can also try installing **alsamixergui** or **gnome-alsamixer** if you want a GUI app to control the sound.

Triumphguy,
Welcome to the Ubuntu forums!

---

### Post by tommah04 on 2010-11-06
hey all,

I figured it out... somehow gnome-media was uninstalled

after typing "gnome-volume-control-applet" command it told me to install gnome-media

so....

sudo apt-get install gnome-media

then add it back to startup applications and it'll show up in the Notification Area in the taskbar

thanks for your time!

---

