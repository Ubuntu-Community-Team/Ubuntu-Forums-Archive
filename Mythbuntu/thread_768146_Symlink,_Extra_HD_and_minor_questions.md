---
title: "Symlink, Extra HD and minor questions"
date: 2008-04-26
forum: Mythbuntu
---

### Post by gephdk on 2008-04-26
Hey guys

Have some probs on my Mythbuntu I can´t get fixed nomatter what I do, minor stuff I know, but still it´s irritating. Am very new to Linux so pls talk to me like I´m an 3 year old on this :D

But onwards to the technical stuff :)

I´ve installed Mythbuntu on a smaller boot drive and put all media on a second drive altering the symlinks for the different media etc, and it has worked like a charm, besides minor stuff.


Mythweb:
Everything seems to be working BUT the covers in the movies section for some odd reason..

The covers are working fine in the Mythtv bit where I have set a dir link in generel settings to /media/mythstore2/video_covers. To get Mythweb to work with covers I´ve made a Symblink in /usr/share/mythtv/mythweb/data/ called video (and a similar called videos just to be sure) that points to /media/mythstore2/video_covers

Then in Mythweb settings I´ve set "VideoArtworkDir" to /media/mythstore2/video_covers

But no dice for some odd reason.. It worked like 5 mins when I was playing around with symlinks (new to the topic) but it haven´t worked since... Any ideas?


Problem2, harddrives:
I know about Storagegroups but as I can understand, Storagegroups only works for recordings, and since I want to add a second drive for converted ISO movies I can´t use this option.

So how do I add a second storage harddrive for media that´s not only for recordings so mythTV can scan through it and add it on the fex. movie section of MythTV?


Third problem:
I´ve installed a digtital TV card and also have digital channel provider, and when scanning for channels I get them listed. But when I go to "watch TV" I get nothing but black screen, it says the channel signal is locked and all that, but no signal.

It´s a autoinstalled technotrend/hauppauge card (Probed info: dvb [saa7146 v4|2] )I´ve installed as TV card and then have a geforce 6600 as "normal card". Any ideas on that?

Fourth one:
Assumably MythWeb should be able to stream both movies and music over network via flash, is that feature enabled or, because that doesn´t seem to function on mine. Well music is streaming or atleast letting me play the music on mythweb, but no working for movies, neither .ISO or any other format :(


I´m running the RC version of Mythbuntu because it fixed some other stuff I had problems with and I generelly like to work with that version a lot better than the old one (VERY nice work guys, thanks :) )

---

### Post by tgm4883 on 2008-04-26
Problem 1.   You probably don't have the video covers anymore (you do, but not in the right directory).  Rescan the videos

Problem 2.   Mount the drive in whatever location you want to use for recordings (ie, mine are /mythtv/recordings/disk1, /mythtv/recordings/disk2).  Add that directory to your storage groups, then, symlink that directory to your mythvideos directory.  Then you can use it for both.

Problem 3.  Don't know.  Does it work for recordings?  Can you post your /var/log/mythtv/mythbackend.log file?

Problem 4.  AFAIK, videos don't get streamed over mythweb.  Only recordings and music

---

### Post by gephdk on 2008-04-27
Hey tgm4883 and thanks for answering :)

Problem1:
Scan where? The covers are working fine inside mythtv when I got to the movies section, it´s only on Mythweb they´re not working, but don´t think there´s a scanoption there?

Problem 2:
Gonna try that out and see if it works :)

Problem3:
Posted :)

Problem4:
Ahh okay, bummer :(

---

### Post by gephdk on 2008-05-01
Stupid question (I think)

I´ve now created 2 storagegroups in the "default section", so far so good.

Then, to get MythTV to "scan" those groups I have to symlink them, but symlink them to where?

---

### Post by sgunther on 2008-05-01
Problem One Fix

Ok so the covers issue is fairly easy.  MythWeb requires a symlink for the videos and the covers.

So...

```
cd /var/www/mythweb/data/
sudo rm ./video
sudo ln -s **<Path to Videos>** ./video
sudo rm ./video_covers
sudo ln -s **<Path to Video Covers>** ./video_covers
```

Note: You must put in your local paths where the <> symbols are.
      You should only have to do this for non default video storage locations.

---

### Post by newlinux on 2008-05-01
For number two, you can have multiple directories in your mythvideo scan settings. Just separate them with a colon. You don't have to symlink them if you don't want to...

---

