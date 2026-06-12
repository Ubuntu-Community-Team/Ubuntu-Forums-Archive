---
title: "Amarok 2 volume independant from system volume"
date: 2009-03-10
forum: Multimedia Software
---

### Post by geoffm on 2009-03-10
I just installed amarok 2.0.1 (somehow I can't figure out why I can't get the 2.0.1.1 version since I followed the instructions there [http://www.kubuntu.org/news/amarok-2.0.1.1](http://www.kubuntu.org/news/amarok-2.0.1.1))

It's volume is independant from the system volume. I can even mute the whole system and amarok2 will keep playing on its own. (I can control its volume using the graphical slider though). It's annoying because I use the multimedia keyboard most of the time, I don't want to have to pickup the mouse, find the program window and move a slider just to ajust the volume everytime.

I would guess amarok uses another sound server? There is no setting related to this.
How can I install 2.0.1.1?
Can I make amarok2 respond to kmix?

---

### Post by markbuntu on 2009-03-11
Amarok 2 uses the new Phonon api and the xine backend. You can configure Phonon in System Settings Sound. If you set music to default instead of the hardware device you should be able to control it with kmix. You can also read this post

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

---

