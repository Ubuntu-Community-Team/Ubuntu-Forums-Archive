---
title: "KWorld card won't work... Please help!"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by novice_geek on 2007-01-18
Hello,
 
I just installed Ubuntu Edgy and now I need to get the TV Tuner Card working.  It's a KWorld (Should be a saa7133 or saa7134 based card).  It's not the Xpert series, just one of the cheaper ones.  It has Radio and TV, plus a remote (Which I won't be using, as I have an external satellite receiver which I will use for that.  Once I got it up, I installed KDETV, and it's not working.  The card shows up as UNKNOWN/GENERIC.  In MythTV, it is labeled as "Analog V4L capture card" and "UNKNOWN/GENERIC [saa7134]"  Please tell me how I can install it and get it working.
 
I have no idea as to what I'm doing, so instructions would be great.
 
Thank-you to everyone.
 
Novice_Geek

---

### Post by cfcubed on 2007-01-19
I have the KWorld ATSC-110 and did a search for it & MythTV prior to installing...  Turns out that myth setup had no problem recognizing it so after dealing with backend auth issues (see also my posts on "MythTV Backend Authentication Rejected.." thread) its working pretty well for me.

So recommend searching for your KWorld card model & MythTV & see what you get.  MythTV setup is fairly involved but there are alot of comments, docs & suggestions out there.  Besides the obvious places, you could try searching del.icio.us mythtv tagged links.  Giving much more detail in your post is helpful too (eg "not working", no model #s, etc.).

Good luck.

---

### Post by munkiepus on 2007-04-17
It sounds like you have the same card that i have, the kworld dvb-t 220 analog/dvb dual tuner card. it could be called tevion/kworld. It took me quite a while to figure out if this even worked with ubuntu. But once all the searching was over then it was pretty easy. I'm doing this from memory so forgive me if i get a step wrong;

You can Check your sys log just to check if the card is the same.

```
cat /var/log/messages | grep world
``` 
there should be a couple of lines there showing the analogue part of the card registered.

There is a bug logged for the dvb part of this card not loading automatically in ubuntu:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/56801](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/56801)

You might get lucky and this could load the missing modules and detect the dvb-t part of the card.
```
sudo modprobe saa7134-dvb
```


If not you will have to install the v4l-dvb kernel modules i cant remember exactly how i did this but i used the guide here [http://www.linuxtv.org/repo/](http://www.linuxtv.org/repo/)

One thing worth noting is that if you reset your machine then the card will stop working. Don't worry it's easily fixed. You will have to to the 'make reload' part of the guide again and this will put the modules back for you. I'm not sure how to get the modules to load on startup, but at least this will let you see if the card works. 

Hope this helps :)

---

