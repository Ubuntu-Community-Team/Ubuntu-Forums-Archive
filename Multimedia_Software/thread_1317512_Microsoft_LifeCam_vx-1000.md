---
title: "Microsoft LifeCam vx-1000"
date: 2009-11-06
forum: Multimedia Software
---

### Post by exploitations on 2009-11-06
This is the only problem that I'm having with Ubuntu. If I can get this webcam working, Goodbye windows. Even though I don't exactly have windows on my computer anymore.

I'm so excited to get this webcam working, I love ubuntu, and to have the webcam working, it'll feel like a real computer, with everything I've paid for working.

So, if any of you have any help, it would be really helpful.

I have Ubuntu 9.1,
500 GB hd. 3 gb ram, ATI hd graphics card..

And of course, the vx-1000. 

Other Information:
My computer will read the webcam, and tries to use it, but the screen is green, except for the top part, where something shows, but I don't exactly know how to explain it.

I've tried everything. Everyone elses problems don't seem to help mine, lol.

---

### Post by dannyfel on 2009-11-20
Download [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)
Unpack it wherever
Enter the new created folder, and run:
# make
then:
# gedit v4l/.config
Change:
CONFIG_DVB_FIREDTV=m
to
CONFIG_DVB_FIREDTV=n
save the file and run again:
#make
#sudo make install
reboot

original solution from [http://swiss.ubuntuforums.org/showthread.php?p=8238570](http://swiss.ubuntuforums.org/showthread.php?p=8238570)

---

