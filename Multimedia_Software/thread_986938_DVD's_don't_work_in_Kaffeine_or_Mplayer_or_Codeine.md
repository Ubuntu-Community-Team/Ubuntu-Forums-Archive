---
title: "DVD's don't work in Kaffeine or Mplayer or Codeine."
date: 2008-11-19
forum: Multimedia Software
---

### Post by Pepse3 on 2008-11-19
I used the info from the Sticky and the only device a DVD plays on is VLC.  And since the sticky doesn't cover problems if it works in VLC but no others I decided to post.  I did notice that when I cut and paste to get all the necessary items to run I ended up with " libdvdcss2 " and win32 codecs in my home folder.  So, if needed I put them into their own folder.  Should I open these 2 files?  And if so which way?  Do I open them in a command line or just go to the folder and use gdebi?

  Funny though I am having more hassles with Kubuntu 8.04 on this hard drive than when I put it on another drive shortly after 8.04 was released.

Later.  Pepse.

---

### Post by mc4man on 2008-11-19
I not familiar with codeine but if vlc works then mplayer should.
Mplayer defaults to /dev/dvd, maybe your drive is /dev/dvd1.

Running this will tell you.
```
sudo lshw -C disk
``` 

then make change if needed in mplayers preference (open mplayer from menu and r. click on screen.

Kaffeine defaults to /dev/dvd also, in 8.04 you need to set it to /dev/scd0 or /dev/scd1, ect. 
It also needs libxine1-ffmpeg installed.

As far as libdvdcss2, w32codecs, and the home folder I'm not quite getting it, just ck. in adept if they are installed. If not add medibuntu to repo sources and install properly

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Pepse3 on 2008-11-19
Your suggestions worked:).  I thank you for your help.

  Strange that when installing KUB 8.04 on this hard drive that I am having so many little problems.  But, I recall similar situations when I ran Mandrake/Mandriva.

Later. Pepse.

---

