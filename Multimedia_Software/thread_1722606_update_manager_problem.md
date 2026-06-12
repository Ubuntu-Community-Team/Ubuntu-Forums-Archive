---
title: "update manager problem"
date: 2011-04-06
forum: Multimedia Software
---

### Post by Mia1990 on 2011-04-06
When i start the update manager it checks for updates then gives me this message.

> Not all updates can be installed
run a partial upgrade to install as many updates as possible
this can be caused by
A previous upgrade which didn't complete
 Problems with some of the installed software
 Unofficial software packages not provided by Ubuntu
 Normal changes of a pre-release version of UbuntuI have not installed any thing or add any software source's and i did not do a upgrade.The files that will not update are > libavdevice52 libavfilter libavformat52 libpostproc51 libswscale0 and winetricksall of the files go with ffmpeg and winetricks goes with wine.Those are the only updates that shows any problem.I have already run fix broken packages and that doesn't help.Deos anyone know what's wrong?

---

### Post by wolfen69 on 2011-04-06
Did you just upgrade to 10.04 by any chance?

---

### Post by Mia1990 on 2011-04-06
no i didn't upgrade i did a clean install of ubuntu 10.04

---

### Post by blackdalek on 2011-04-06
I am having the same problem.

Mine is having a problem with ffmpeg, libavdevice32, linavfilter0 and winetricks.

I am having this same problem on two different systems - Ubuntu 10.10 and 10.04

The problem only started within the last 5 days.

---

### Post by jmuggins on 2011-04-06
I'm sorry to have to add a "me, too" to this.

Mine (10.04) has been showing the identical ffmpeg upgrade problem for about three days, and this is the only thread I've found so far... :confused:

---

### Post by Qboy61 on 2011-04-06
I am having a similar problem with only 3 files that will not install in the update manager.

libavformat52
libpostproc51
libswscale0

These three updates are showing up in update manager and their check boxes are not selected, and can not be selected for install.

---

### Post by jmuggins on 2011-04-06
This bug: [https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/751114](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/751114)

Nach0 provided the workaround:

Do a *# sudo aptitude update*, then repeat *# sudo aptitude dist-upgrade* untill all dependencies are met.

---

### Post by Mia1990 on 2011-04-07
Thank you jmuggins Nach0 workaround worked great for me.

---

