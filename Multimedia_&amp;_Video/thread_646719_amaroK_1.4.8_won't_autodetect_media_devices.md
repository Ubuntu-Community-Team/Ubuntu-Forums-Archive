---
title: "amaroK 1.4.8 won't autodetect media devices"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by LTBookman on 2007-12-21
Hello,

I upgraded to amaroK 1.4.8 yesterday and found that it would not autodetect my iPod nor any other media device.

Its response was:
»No new media devices were found. If you feel this is an error, ensure that the DBUS and HAL daemons are running and KDE was built with support for them. You can test this by running "dcop kded mediamanager fullList" in a Konsole window

And, "dcop kded mediamanager fullList" gave nothing but "call failed".

I have downloaded again version 1.4.7 from packages.ubuntu.com and it still works like a charm, so the problem must come from versión 1.4.8 itself.

Any ideas?

---

### Post by ldalcaraz on 2007-12-23
Same problem here and HAL and DBUS up and running. It is amarok v 1.4.8 the one with the bug, any way you can manually mount your devices...  Don't know how to solve the auto detect feature with this version too:confused:

---

### Post by niethslim on 2007-12-23
You can try first opening your ipod from the desktop and then see if amarok detects it.  
It works for me for some reason (I guess that opening the ipod somehow mounts it "officially"), although I'm not sure what version do I use.

---

### Post by jbernardo on 2008-01-06
I'm having the almost same problem in hardy, even though "dcop kded mediamanager fullList" finds my media player:
```
/org/freedesktop/Hal/devices/volume_uuid_68DE_5DE7
sdb
8.2G Removable Media
Meizu 8GB
true
/dev/sdb

vfat
false

media/removable_unmounted
ipod_unmount
false

---

```

I had no problems until upgrading amarok, my media player was detected and worked out of the box.

---

### Post by maestrobwh1 on 2008-01-20
I am using kde4 on kubuntu 7.10 (used the live CD). I am haing the same issue although:

$ dcop kded mediamanager fullList
call failed

So I don't even get this far.

GTKPOD does recognize it however?  How weird.

Resolved: I am leaving this here in case anyone else does a search.  The KDE4 live cd is missing some packages for the ipod.  It might be overkill, but...
install

python-dcop
libipod0
libipoddevice0
ipod
ipodslave
libgpod-common
libgpod2
libipod-cil
libipodui-cil

---

### Post by MadMonkey234 on 2008-01-24
I have the same problem. I posted a bug report there:

[http://bugs.kde.org/show_bug.cgi?id=156622]("http://bugs.kde.org/show_bug.cgi?id=156622")

---

### Post by jbernardo on 2008-01-25
I've voted and commented on it, but maybe we should also open a bug in ubuntu's launchpad?

---

### Post by mzw! on 2008-01-27
I have the same problem after adding the KDE4 repository for kubuntu from ppa

I opened a thread here, because I am not sure we have the exact problem.

[http://ubuntuforums.org/showthread.php?t=672912](http://ubuntuforums.org/showthread.php?t=672912)

---

### Post by mzw! on 2008-02-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/186384](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/186384) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I filled a bug in launchpad:
[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/186384](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/186384)

---

### Post by jbernardo on 2008-02-20
Thanks, I subscribed the bug.

---

