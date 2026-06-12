---
title: "[SOLVED] amarok writes directly to sound card"
date: 2007-09-14
forum: Multimedia &amp; Video
---

### Post by pwaldo on 2007-09-14
Hi all,

I'm running Kubuntu Feisty AMD64.  My Amarok runs just fine, except for the fact that no other system sounds are heard while running Amarok.  I think this is because Amarok is writing directly to the sound card, rather than going through the arts daemon.

When I try to configure Amarok to use arts, the only engine available is xine.  There is no amarok-arts package available:

$ sudo apt-get install amarok-arts
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package amarok-arts

Any help would be greatly appreciated!

Paul

---

### Post by berZirker on 2007-10-15
Well this is a bit of an old post, but I'm going to jump on board and see if anyone can help.  Every so often, and I'm not sure exactly what triggers it yet, while running amarok in ubuntu 7.04, knotify will jump up with an error:

     During the previous startup, KNotify crashed while instantiating KNotify. Do you want to try
     again or disable aRts sound output?  If you choose to disable aRts output now, you can 
     re-enable it later or select an alternate sound player in the System Notifications control
     panel.

Sounds work fine with the rest of the system, and amarok doesn't crash or anything.  This warning just makes me nervous.  Anyone got any ideas?

---

### Post by pwaldo on 2007-12-14
Using pulse audio server and output plugin does the trick!

---

