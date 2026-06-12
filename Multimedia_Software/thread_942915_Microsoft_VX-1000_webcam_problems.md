---
title: "Microsoft VX-1000 webcam problems"
date: 2008-10-09
forum: Multimedia Software
---

### Post by agamble on 2008-10-09
Hello,
I have recently started using Linux, and have found that most plug-ins are highly compatible. However, I have a Microsoft VX-1000 webcam that will not work on Ubuntu. Any suggestions on how I can solve this problem?

---

### Post by jesterthejedi on 2008-12-24
Working after 6 months of waiting and searching forums. My cam is the dreaded Microsoft VX-1000.

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file
extract and change directory
in terminal type "make" no quotes take about 5 mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue Hardy mess.
not working in Camorama, Camstream, errors in gqcam

installed xawtv, luvcview, and removed camserv.

I am so happy that I should pinch myself. I bought this webcam in June for my birthday and it was always a pain in the butt to solve. Success at last!

---

### Post by pri.julien on 2009-04-04
is there a command to do all of this at once on konsole or is there another way to do it. Sorry I just have the same problem and kind of confused of the instruction you left. Anyway thanx in advance, Julien :)

---

### Post by oiu on 2009-06-26
Just install kernell 2.6.30 and Vx-1000 will work but with no mic

---

