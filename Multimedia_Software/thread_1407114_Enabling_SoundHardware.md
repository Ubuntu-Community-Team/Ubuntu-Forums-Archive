---
title: "Enabling Sound/Hardware"
date: 2010-02-14
forum: Multimedia Software
---

### Post by Joe772 on 2010-02-14
So I did a command line install recently, and installed xorg, and a few window managers. (Gnome, KDE, XFCE, Fluxbox) I'm using startx to run them. Can someone give me the instructions on how to enable mp3 playback, as well as my soundcard hardware? 

This is my soundcard: [http://www.alsa-project.org/main/index.php/Matrix:Module-ens1371](http://www.alsa-project.org/main/index.php/Matrix:Module-ens1371)

The real issue is, is that I did a command line install a few days ago (Had to reformat and do this one) and I had mp3 playback working as well as my hardware working. It would just be really helpful if someone could give me a step by step on what exact packages to install. 

Regards,
Joe

---

### Post by Joe772 on 2010-02-15
bump

if I have ubuntu-desktop installed, everything works fine btw

---

### Post by Yellow Pasque on 2010-02-15
For the sound hardware, you should only need alsa-utils (and it dependencies).
For mp3 playback, it depends on what program you;re using.

---

### Post by Joe772 on 2010-02-16
So asla-utils installs all the drivers as well? It seemed that when I was frumping around with everything, I could get it to play in tty7 but no sound, and when I switched to tty1-6 (logged in) it would have the sound from tty7 coming out.

---

