---
title: "&quot;Watch TV&quot; Doesn't Work"
date: 2009-02-14
forum: Multimedia Software
---

### Post by tufcamman on 2009-02-14
Hi everyone, so I'm trying out mythbuntu for the first time.  Easiest setup, same machine for primary backend and frontend.  I know my capture card is working because I can run vlc and see the cable channels, changing it with ivtv controls on the command line.

I have set up an account with schedules direct and that all the channels have been downloaded into mythbuntu backend setup.  Also, when I scan channels, it finds them all.  So I know the signal is getting into the computer.

I can log into the backend fine, the database is there and everything seems to be happy.  I have my captue card set to MPEG-2 encoder (I have a PVR-150).  Device is /dev/video0.  Input is Tuner 1.

My Video source is set to us-cable (I figure that's correct since scanning the channels discovers them all).  I have my schedulesdirect.org account setup and it is downloading listings.

I have run mythfilldatabase and it downloaded everything from schedules direct and it seemed to work fine.

I just can't seem to find anything that I've done wrong.  But still when I run myth frontend and hit watch tv, the screen goes black for about 2 seconds and then just goes back to the mythtv homepage.

Thanks in advance for reading my giant post and any help is greatly appreciated.

---

### Post by saedelaere on 2009-02-17
> **tufcamman said:**
> Hi everyone, so I'm trying out mythbuntu for the first time.  Easiest setup, same machine for primary backend and frontend.  I know my capture card is working because I can run vlc and see the cable channels, changing it with ivtv controls on the command line.

I have set up an account with schedules direct and that all the channels have been downloaded into mythbuntu backend setup.  Also, when I scan channels, it finds them all.  So I know the signal is getting into the computer.

I can log into the backend fine, the database is there and everything seems to be happy.  I have my captue card set to MPEG-2 encoder (I have a PVR-150).  Device is /dev/video0.  Input is Tuner 1.

My Video source is set to us-cable (I figure that's correct since scanning the channels discovers them all).  I have my schedulesdirect.org account setup and it is downloading listings.

I have run mythfilldatabase and it downloaded everything from schedules direct and it seemed to work fine.

I just can't seem to find anything that I've done wrong.  But still when I run myth frontend and hit watch tv, the screen goes black for about 2 seconds and then just goes back to the mythtv homepage.

Thanks in advance for reading my giant post and any help is greatly appreciated.

I have to admit I can't help you with your problem, but [here]("http://home.arcor.de/saedelaere/index_eng.html") is an alternative you could try to use.

Regards
Saedelaere

---

### Post by tufcamman on 2009-02-17
Hi, thanks for the suggestion.  I seem to have gotten it working though.  I reinstalled and the only thing that I did differently was use a basic password without special characters for everything.  Login, MySQL Database, MythBackend, everything.  And now it seems to be working fine.  Not sure how this would effect anything but it seems to have.  Thanks again.

---

