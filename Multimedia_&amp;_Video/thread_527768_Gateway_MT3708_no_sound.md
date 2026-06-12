---
title: "Gateway MT3708 no sound"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by g00ncuervo on 2007-08-17
I have a stac9200 audio card.. no sound... feisty... I've drudged through about a million posts and tried hundreds of things but I cant find a solution.. help?

---

### Post by mohnkern on 2007-08-17
if you go to the prompt and type


asoundconf list


What do you get?

---

### Post by dagowop on 2007-10-19
A while back I had this same problem with my mt3708.  I searched the internet for days untill I found a tutorial that involved installing alsa driver, libs, and utils from the 1.0.15rc3(2)(1).  I just completed the update to Gutsey and :( The sound dosn't work again and I have forgotten the url of the site. Please help!!! I will continue to look because I don't give up that easy but any help would be amazing.  If I discover a fix or make my own I will post it here.  Good luck I know the answer is out there.


SOLUTION:

1) sudo aptitude install build-essential
2) mkdir alsa
3) cd alsa
4) sudo wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
5) tar xvjf alsa-driver-1.0.15.tar.bz2
6) cd alsa-driver-1.0.15
7) sudo ./configure
8) sudo make
9) sudo make install
10) sudo reboot now
11) unmute all channels in mixer and sound should work. 

If that work then you can get the libs and utils for that alsa release as well.

Good luck

---

### Post by bricar2 on 2007-10-24
:guitar:THANK YOU THANK YOU THANK YOU AND THANK YOU!!!!! I can't tell you how good it feels to hear that Ubuntu login sound. Finally, it works. Thanks again.

Brian

---

