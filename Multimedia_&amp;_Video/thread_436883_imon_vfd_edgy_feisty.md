---
title: "imon vfd edgy feisty"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by peterthewolf on 2007-05-08
This howto post works fine in 6.10 Edgy

[http://ubuntuforums.org/showthread.php?t=306437](http://ubuntuforums.org/showthread.php?t=306437)

But with 7.04 Feisty the make fails

Any ideas

---

### Post by rob.gilbert on 2007-08-27
Similar problem here.

Following instructions from [http://www.checkthisshitout.com/post/33/](http://www.checkthisshitout.com/post/33/) changing 'linux' to point to correct directory.

x64 amd machine with feisty 7.04

Error message notes config.h and devfs_fs.h missing in subdirectory.

Any idea's on what needs to be installed to get these files in place?

---

### Post by peterthewolf on 2007-09-02
All I have found so far is this post [http://ubuntuforums.org/showthread.php?t=306437](http://ubuntuforums.org/showthread.php?t=306437)

---

### Post by javipas on 2007-09-03
I've been dealing with this lately. I bought a Silverstone LC16BM with iMon VFD and iMon PAD Remote Control, and I've been trying to make them work.

For the moment, the VFD works perfect, but the RC fails to work with MythTV...

MythTV wiki is a great resource to make it work under MythTV:

[http://www.mythtv.org/wiki/index.php/Imon](http://www.mythtv.org/wiki/index.php/Imon)

But there is other resource included on the wiki:


[http://www.mythtv.org/wiki/index.php/LCDproc](http://www.mythtv.org/wiki/index.php/LCDproc)

I've followed this one and I have the VFD working, and MythTV messages appear on the LCD without problem.

Now I'm trying to use the iMon Pad, but although I've compiled lirc-0.8.1 with the iMon patch and irw works (it receives key presses on the RC) MythTV doesn't see anything :-( I've created a /home/javipas/.mythtv/lircrc config file copying and pasting from some guide, but it doesn't work...

---

