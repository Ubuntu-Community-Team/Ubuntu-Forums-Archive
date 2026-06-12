---
title: "Sound not working with text login and startx"
date: 2009-10-02
forum: Multimedia Software
---

### Post by kev000 on 2009-10-02
I'm logging in from tty1 and running starx with matchbox-window-manager.  At first, it appeared that console-kit wasn't giving me correct permissions (aplay -l listed nothing, but sudo aplay -l did).  /etc/Xsession.d/90console-kit apparently wasn't doing anything, so I changed my script to launch matchbox with ck-launch-session.  Now pulseaudio thinks that it's playing, but I get no sound.  I've tested this setup in vbox and on an eepc.

Any hints?

---

### Post by nuovodna on 2009-10-16
perhaps you have to add your user to audio group

see here

[http://forums.remote-exploit.org/newbie-area/16377-startx-problems.html]("http://forums.remote-exploit.org/newbie-area/16377-startx-problems.html")

---

