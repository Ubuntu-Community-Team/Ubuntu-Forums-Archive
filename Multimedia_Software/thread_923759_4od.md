---
title: "4od"
date: 2008-09-18
forum: Multimedia Software
---

### Post by mikeym on 2008-09-18
Can anyone tell me if it's possible to get channel 4 on demand in the UK using ubuntu? 

I tried and it wouldn't let me use it because it detected that I wasn't using internet explorer 5.5+ or XP+.

Thanks for your help.

---

### Post by squaregoldfish on 2008-09-19
Unfortunately this isn't possible. Even if you manage to circumvent the browser/OS checks, all the media files are DRM'd for Windows Media Player, so you won't be able to play them.

When I was looking into this, I happened to have a Windows XP install running in VirtualBox. Accessing 4OD through that worked fine, but it's not something I'd recommend as a setup purely for 4OD.

Steve.

---

### Post by aeiah on 2008-09-19
when i looked into it the only choice was a virtual machine. to be honest you're best using the torrents. more convenient than setting up and running a virtual machine but if you think you're gonna use it a lot then go with virtualbox. with the seamless mode it should be nice and usable, although there will be large overhead due to running windows.

---

### Post by mikeym on 2008-09-19
Just from a brief look this looks like it should be possible using wine. 

Both .NET and WMP10 work under wine ([.NET 2.0]("http://appdb.winehq.org/appview.php?iVersionId=3754") is gold and [WMP10]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3212") is bronze in the AppDB).

I wonder if anyone has any other thoughts on this?

---

### Post by mikeym on 2008-09-19
There's a page on a related topic of getting iPlayer to work under wine.

[http://bbciplayerlinux.sourceforge.net/index.php/Main_Page](http://bbciplayerlinux.sourceforge.net/index.php/Main_Page)

---

### Post by lesshaste on 2009-03-12
There is a wine bug report which you could contribute to.  Who knows, it might encourage the developers to try to get it working if lots of people confirm the problem.

[http://bugs.winehq.org/show_bug.cgi?id=16505](http://bugs.winehq.org/show_bug.cgi?id=16505)

Raphael

---

### Post by gdbutcher on 2009-04-09
I can confirm what aeiah said I've got 4 OD (along with ITV, and Channel 5, I run BBC Iplayer Natively) working on my laptop using Win XP, VirtualBox + Guest Addidtions. I've allocated 1GB of RAM and 100 Mb of video memory to the virtual machine but I suspect it could run off a lot less. 

The screenshot attached shows the virtual machine running on the excellent new Ubuntu 9.04 beta. It did also work in 8.10 

I know this isn't a native linux suggestion but it seems like the companies are in no hurry to support Linux...morons!

---

