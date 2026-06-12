---
title: "sound problem"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by d11 on 2007-10-16
hi. i installed ubuntu 7.10 rc gutsy and my sound is working almost whit all aplications and login. the only problem is that i dont have logout sound and others system sounds like battery alert, errors, windows effects(compiz) or when you empty the trash etc.
help please.

---

### Post by ok1dtm on 2007-10-20
The same problem:( Play ok only startup*.wav. Logout sound and others no work in final Gusty:(

---

### Post by dahlheim on 2007-10-20
> **ok1dtm said:**
> The same problem:( Play ok only startup*.wav. Logout sound and others no work in final Gusty:(

same here, been that way since i first install gutsy (tribe 5) :(

---

### Post by d11 on 2007-10-22
I got the solution. first install gstreamer0.10-esd, libesd0-dev, libesd0-alsa, mpg123-sd.
then go to system, preferences, sounds. and select sound events,then select  use esd enlightened sound daemon.
lucky.

---

### Post by dahlheim on 2007-10-22
> **d11 said:**
> I got the solution. first install gstreamer0.10-esd, libesd0-dev, libesd0-alsa, mpg123-sd.
then go to system, preferences, sounds. and select sound events,then select  use esd enlightened sound daemon.
lucky.

are you running the final 7.10?  i am still running beta from 2 weeks ago and these maneuvers didn't help me.  i cannot run the enlightened sound daemon (gives me errors trying to enable it).  also, for me,
gstreamer0.10-esd is ok
libesd0-dev is ok
libesd0-alsa is actually libesd-alsa0
mpg123-sd is actually mpg123-esd

---

### Post by ceaseoleo on 2007-10-22
I had the same issue of not having sound with gutsy. 

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/131577](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/131577)

-- link to bug 

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

--  link on how to install new alsa driver  just replace 1.0.14 with 1.0.15

thanks

 this is the error msg i was receiving --
No volume control GStreamer plugins and/or devices found. 

my card that was effect.. if you type sudo lspci and see this, then you will definitely be effected.  
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

---

### Post by d11 on 2007-10-23
you are right. i also installed esound, esound-clients, esound-common. try now. then go to sounds and select a sound for the events. i am using ubuntu Gutsy RC.

---

