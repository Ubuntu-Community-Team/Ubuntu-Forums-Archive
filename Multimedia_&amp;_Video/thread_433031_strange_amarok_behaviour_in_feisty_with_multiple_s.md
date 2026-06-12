---
title: "strange amarok behaviour in feisty with multiple sound cards"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by groggyboy on 2007-05-04
i'm running feisty gnome ubuntu, and i have onboard speakers (ICH6) and logitech USB speakers (Speaker).  I have set the usb to default ("asoundconf set-default-card Speaker").

this works fine for programs like rhythmbox - when the speakers are plugged in, the sound comes out of them, and when the speakers are disconnected, the sound comes out of my laptop.  this is exactly how i want things to behave (aside from being unable to hear the startup sound if the USB speakers aren't attached).

however, when i try to run amarok, things start getting weird.  the first song will play out of the external speakers, but when the track changes, the new song will play from the onboard speakers.  if i double click the track to restart it, it will play from the external speakers (until the next song change, when it goes back to onboard sound).  i would love to use amarok, but this is unacceptable.  ](*,) 

does anyone know what's going on and how i could fix this?

thanks in advance,
groggyboy

---

### Post by groggyboy on 2007-05-05
[BUMP]

still no fix yet - can't *anyone* help?

[/BUMP]

---

### Post by groggyboy on 2007-05-08
well, this isn't a solution, but at least i know i'm not alone:

[Launchpad Bug #79128]("https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/79128")

---

