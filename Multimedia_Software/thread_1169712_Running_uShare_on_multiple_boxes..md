---
title: "Running uShare on multiple boxes."
date: 2009-05-25
forum: Multimedia Software
---

### Post by toyota_f1 on 2009-05-25
I had a fileserving machine running uShare that was already maxed out with hard drives.  I started to build a new faster fileserver and moved a good chunk of media over to this.  Ushare is working fine on my new fileserver, unfortunately now I can't get my old machine to connect to my xBox 360 now.

New machine: P4 3.2 running Ubuntu 9.04 x64
Old machine: Athlon 64 3700+ running Ubuntu 8.04 x64

On the old machine I run it with
:~$ ushare -x
and now get

Interface eth- is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight uPnP A/V and DLNA Media Server.
Benjamin Zores (c) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates
bind: Address already in use

This happens whether I'm actively running uShare on the new box or not.  It has only started happening since the first time I ran uShare on the new box.

Is it not possible to run multiple instances of ushare on multiple machines?  Do I need to drastically change some settings?  I'm using different telnet and web interface ports on each one.

On a side note, if I launch with 
:~$ ushare -x -t

then it will actually launch, and the xBox can see it, I just can't connect to it.  I get the "may be behind a firewall" message on the xBox.  Any help would be appreciated.

---

