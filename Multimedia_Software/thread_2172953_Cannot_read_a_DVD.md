---
title: "Cannot read a DVD"
date: 2013-09-07
forum: Multimedia Software
---

### Post by Lloydb39 on 2013-09-07
I have a homebuilt AMD 64 bit machine running 12.04. I tried to play a movie DVD. Movieplayer created multiple blank windows and then froze. Had to reboot to get rid of them. VLC created a window but never showed the movie. The disk was mounted and I could access the TS files but none would play. I can play video files that are in the computer and I could play the DVD movie disk on my Windows computer, so it is not the disk but something to do with my setup. I ran all the fixes in the sticky above and still nothing. Would appreciate any tips to diagnose and fix.

---

### Post by rai_shu2 on 2013-09-07
Most commercial DVDs contain encryption that requires some form of [descrambling]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") to work correctly.

---

### Post by Lloydb39 on 2013-09-07
Thank you for the link. I already had dvdread4 but the second command did something. VLC will show only the menu screen, upside down. Mplayer tries to play it and actually launched one movie from the menu, but then froze and I had to reboot from the terminal. I then got Gnome player and it worked -- except for one oddity: It leaves a white square on the screen where the menu block was... I would show a screenshot if I could figure out how ... In short, I'm almost there.

---

### Post by rai_shu2 on 2013-09-07
Maybe try out Xine (maybe just be called xine-ui).

---

