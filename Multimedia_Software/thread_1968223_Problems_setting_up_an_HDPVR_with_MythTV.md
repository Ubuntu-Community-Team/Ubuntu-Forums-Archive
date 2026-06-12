---
title: "Problems setting up an HDPVR with MythTV"
date: 2012-04-28
forum: Multimedia Software
---

### Post by LeHerp on 2012-04-28
Hi there. I'm new to using Ubuntu and I've been trying to set up my HDPVR with MythTV as I heard it was the best option available. I've tried several guides online, all with no success so I'm getting the impression that they might be out of date. I was wondering if anyone could either provide me with an up to date, step by step guide (jargon free preferably) or explain it themselves. Any help would be much appreciated.

---

### Post by BicyclerBoy on 2012-04-29
Your best hope could be website mythtv.org &/or the mythtv mailing lists & search of hd-pvr (if you mean the haupig).
[http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR)
[http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/)

There is a mythbuntu sub-forum "here" hidden under 3rd party projects.

---

### Post by LeHerp on 2012-04-29
Okay, thanks for your help. I tried using the first of your links and generally, I didn't seem to encounter any problems when compiling. There was one example though; here is the command tree for installing the driver

git clone git://linuxtv.org/media_build.git
cd media_build
./check_needs.pl
make -C linux/ download
make -C linux/ untar
make stagingconfig
make
sudo make install

When I tried "./check.needs.pl" I got "no such file or directory". I do not know how crucial a step this was so I'm unsure as to whether or not this affected the overall outcome.

---

